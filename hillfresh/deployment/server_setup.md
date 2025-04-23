# DEPLOYING TO DIGITAL OCEAN

## SETUP

- After installing `frappe-bench` using the command, `sudo -H pip3 install frappe-bench`.

  1.Create a New Site
  Create a new site for your ERPNext installation.

```bash
bench new-site yourdomain.com
```

2.Install ERPNext

- Install ERPNext on the site you just created.

  ```bash
  bench get-app erpnext https://github.com/frappe/erpnext
  bench --site yourdomain.com install-app erpnext
  ```

### Configure Supervisor

- Supervisor will be used to manage multiple sites and processes.

- Install Supervisor using the command.
  ```bash
  sudo apt install supervisor -y
  ```

#### Configure Supervisor for ERPNext

- Create a new Supervisor configuration file for ERPNext.

  ```bash
  
  sudo nano /etc/supervisor/conf.d/erpnext.conf
  ```

- `The name of the file in conf.d will also specify the name of the tenant/site`. For example.
  `hillfresh.co.ke` will use the supervisor file located at `/etc/supervisor/conf.d/hillfresh.co.ke.conf`

- Add the following content:

  ```ini
  [program:frappe-bench]
  command = /usr/bin/bench serve --port 8000
  directory = /home/youruser/frappe-bench
  user = youruser
  autostart = true
  autorestart = true
  redirect_stderr = true
  stdout_logfile = /home/youruser/frappe-bench/logs/supervisor.log
  ```

- Replace youruser with your actual username and the client's port with the custom port they are assigned to.

#### Reload Supervisor

- Reload Supervisor to apply the new configuration.
  `bash
sudo supervisorctl reread
sudo supervisorctl update
sudo supervisorctl start frappe-bench
`

### Configure Nginx

- Nginx will be used to serve your ERPNext site.

- Create a New Nginx Configuration file for your site.

  ```bash
  sudo nano /etc/nginx/sites-available/yourdomain.com
  ```

- Add the following content:

      ```nginx
      server {
      listen 80;
      server_name yourdomain.com;

          location / {
              proxy_pass http://127.0.0.1:8000;
              proxy_set_header Host $host;
              proxy_set_header X-Real-IP $remote_addr;
              proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
              proxy_set_header X-Forwarded-Proto $scheme;
          }

          location /assets {
              alias /home/youruser/frappe-bench/sites/yourdomain.com/public/assets;
          }

          location /files {
              alias /home/youruser/frappe-bench/sites/yourdomain.com/public/files;
          }
      }
      ```

- Replace yourdomain.com and youruser with your actual domain and username.

#### Enable the Nginx Configuration

- Enable the Nginx configuration by creating a symbolic link.

  ```bash
  sudo ln -s /etc/nginx/sites-available/yourdomain.com /etc/nginx/sites-enabled/
  ```

### Test and Reload Nginx

- Test the Nginx configuration and reload it.

  ```bash
      sudo nginx -t
      sudo systemctl reload nginx
  ```

### Serve Assets Properly

- ERPNext assets are served from the public directory of your site. Ensure that the Nginx configuration correctly points to the `public/assets` and `public/files` directories.

## SOLVING CORS PROBLEMS

- To setup a server DNS for multitenancy, add the following to the `common_site_config.json` and save the changes.

```json
 "allow_cors":"*",
```

## SETTING UP EACH SITE'S CUSTOM SUPERVISOR

```bash
[program:test.hillfresh.co.ke]
command=/home/hillfresh/frappe-bench/env/bin/gunicorn --chdir /home/hillfresh/frappe-bench/sites --bind 127.0.0.1:8001 --workers 4 --threads 2 frappe.app:application
directory=/home/hillfresh/frappe-bench/sites
user=hillfresh
autostart=true
autorestart=true
redirect_stderr=true
stdout_logfile=/var/log/supervisor/test.hillfresh.co.ke.log
```

- After adding the above config into the `site's` configuration found at `/etc/supervisor/conf.d/sitename.conf`, restart supervisor using the commands below provided.

```bash
sudo supervisorctl reread
sudo supervisorctl update
sudo supervisorctl start test.hillfresh.co.ke
```

## FAQ?

### What happens when my static files do not load properly and I get an error 13:Permission Denied

1. Check if Static Files Exist
   Ensure that the static files are generated and located in the correct directory. Run the following command to collect static files:

```bash
cd /home/hillfresh/frappe-bench
bench build
bench --site <your-site-name> clear-cache
```

- This will generate static files in the sites/assets directory.

2. Identify the Nginx User
   On most Linux systems, the Nginx user is www-data (Ubuntu/Debian) or nginx (CentOS/RHEL). You can confirm this by checking the Nginx configuration file:

```bash
grep -i user /etc/nginx/nginx.conf
```

The output will typically look like this:

```bash
user www-data;
```

If the user directive is not present, Nginx defaults to `www-data` (Ubuntu/Debian) or nginx (CentOS/RHEL).

3. Add the Nginx User to the hillfresh Group
   To allow the Nginx user to access the files, add the Nginx user to the hillfresh group (the user under which Frappe Bench is running).

Run the following command:

```bash
sudo usermod -a -G hillfresh www-data
```

Replace `www-data` with nginx if you’re on CentOS/RHEL.

4. Set Proper File Permissions
   Ensure that the sites/assets directory and its contents are readable by the Nginx user. Run the following commands:

```bash
sudo chown -R hillfresh:hillfresh /home/hillfresh/frappe-bench/sites/assets
sudo chmod -R 775 /home/hillfresh/frappe-bench/sites/assets
```

    chown -R hillfresh:hillfresh: Ensures that the hillfresh user and group own the files.

    chmod -R 775: Ensures that the hillfresh group has read and execute permissions.

5. Verify Group Membership
   Ensure that the Nginx user is correctly added to the hillfresh group. Run:

```bash
groups www-data
```

The output should include hillfresh:

```bash
www-data : www-data hillfresh
```

6. Restart Nginx
   After making these changes, restart Nginx to apply the new permissions:

```bash
sudo systemctl restart nginx
```

### SETTING UP A SERVER DNS FOR MULTITENANCY.

- To setup a server DNS for multitenancy, add the following to your `common_site_config.json` and save the changes.

```json
"dns_multitenant": true,
"wildcard": {
      "domain": "hillfresh.co.ke",
      "ssl_certificate": "/etc/letsencrypt/live/hillfresh.co.ke/fullchain.pem",
      "ssl_certificate_key": "/etc/letsencrypt/live/hillfresh.co.ke/privkey.pem"
  }
```

### Does bench provide a mechanism for Keep track of each site's config?

- NO, they are assigned by `bench` when bench starts up and as such, they are not stored in a fixed location.

### How do I drop a site on ERPNext?

- To drop a site, run the command below.

```bash
bench drop-site test.hillfresh.co.ke --no-backup
```

### How do I create a new site? and What happens when I create a new server site?

- After I create a new site using the command `bench new-site site_name`. you may get one of the errors below.

```bash
test.hillfresh.co.ke: SystemSettings.enable_scheduler is UNSET
*** Scheduler is disabled ***
$ bench --site test.hillfresh.co.ke install-app erpnext
```

- Install erpnext using the command `bench --site test.hillfresh.co.ke install-app erpnext`
