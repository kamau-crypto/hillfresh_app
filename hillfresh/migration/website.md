# Migration

## Website

1. TO move code/ a folder from a local machine to a server, run the following command...

```bash
 scp -r ./hillfresh-website-main/ root@46.101.233.96:/var/www/
```

2. After that, you can rename or move the folders using the `mv command` as follows.

```bash
mv ./hillfresh-website-main/* /var/www/tutorial/
```

3. You can pipe commands using the `|` pipe operator allowing you to combine more than one command at once.
