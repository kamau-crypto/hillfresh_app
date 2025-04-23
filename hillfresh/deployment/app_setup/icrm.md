Here's how to install a custom Frappe/ERPNext app from GitHub to your bench environment:

Prerequisites
You have a working Frappe Bench setup

Git is installed on your system

You have the GitHub repository URL for the app. Since Git Disabled `https access from an url`. Use ssh instead. Refer to `../etl.md` for more information.

1. Navigate to your bench directory
   bash
   Copy
   cd ~/frappe-bench

2. Add the app to your bench

```bash
bench get-app [app-name] [github-repo-url]
```

```bash
bench get-app erpnext_healthcare https://github.com/frappe/healthcare
```

3. Install the app to your site

- Before running the command below, make sure developer mode is enabled to perform this addition of the custom app.

```bash
bench --site [your-site-name] install-app [app-name]

```

- You can also temporarily enable developer mode during installation:

```bash
bench --site [your-site-name] set-config developer_mode 1 && bench --site [your-site-name] install-app icrm
```

- After installation, you can disable developer mode if desired:

```bash

bench --site [your-site-name] set-config developer_mode 0

```

4. Run Bench Migrate to ensure you have all the migrations ready.

```bash
bench migrate
```
