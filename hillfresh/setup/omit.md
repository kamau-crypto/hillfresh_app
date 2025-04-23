# Omitting packages from Auto Update

##

1. Edit the unattended-upgrades configuration:

```bash

sudo nano /etc/apt/apt.conf.d/50unattended-upgrades

```

2. Add packages to the blacklist code block:

```ini

Unattended-Upgrade::Package-Blacklist {
    //
    //THE REST OF THE CONFIG
    "mariadb-server";
    "mariadb-client";
    "python*";
    "redis-server";
    "nodejs";
    "yarn";
};
```

3. Test that the packages were successfully black listed by running

```bash

sudo grep -A 30 "Package-Blacklist" /etc/apt/apt.conf.d/50unattended-upgrades

```
