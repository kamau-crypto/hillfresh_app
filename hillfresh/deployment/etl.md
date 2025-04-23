# Deployment workflow

## Generate your ssh key.

Generate SSH keys on your server (if you haven't already)

```bash

ssh-keygen -t ed25519 -C "your_email@example.com"
```

1. Add the SSH key to your GitHub account

```bash

cat ~/.ssh/id_ed25519.pub
```

Copy the output and add it to your GitHub account under:
Settings → SSH and GPG keys → New SSH key

## Add your ssh key to your ssh-agent

```bash
ssh-add ~/peter

```

## Test Basic ssh connectivity to GitHub

```bash
ssh -T git@github.com
```

## Pull the repo from GitHub

- Install the bench app from GitHub using

```bash

bench get-app icrm git@github.com/yourreponame.git

```
