# How to add your sshkey to the ssh agent

1. Verify your SSH agent is running

```bash
eval "$(ssh-agent -s)"
ssh-add  ~/.ssh/id_ed25519
```

2. First, test basic SSH connectivity to GitHub

```bash
ssh -T git@github.com
```

- You should see:

```bash
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```
