# Use SSH Keys

## Step 1: Generate SSH key on your server

```bash
ssh-keygen -t ed25519 -C "it@thinksurfmedia.info"
```

Press **Enter** to accept defaults (it will create `~/.ssh/id_ed25519`).  
Optionally set a passphrase (or just press Enter for none).

---

## Step 2: Copy public key

```bash
cat ~/.ssh/id_ed25519.pub
```

Copy the whole output.

Example:
```
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIFc+X9ocmBp3attkGYAThuUjaJFAzXbnBPx/Xl8kiOMt it@thinksurfmedia.info
```

---

## Step 3: Add key to your Git hosting

- Go to **GitHub → Settings → SSH and GPG keys → New SSH Key**  
- Paste the key and save.  

If it’s an **organization repo**, you may need admin rights or to add it under the **organization settings → SSH keys**.

---

## Step 4: Test connection

```bash
ssh -T git@github.com
```

If it says `"You’ve successfully authenticated"`, you’re good.

---

## Step 5: Change your repo remote to SSH

Inside your repo folder: Change Git Remote to SSH

1. Check your remote URL:
```bash
git remote -v
```
You’ll see something like:
origin  https://github.com/ORG_NAME/REPO_NAME.git (fetch)
origin  https://github.com/ORG_NAME/REPO_NAME.git (push)

2.Change it to SSH:
```bash
git remote set-url origin git@github.com:Thinksurfmedia-LLP/shopfrombharat.git
```

Now `git pull` or `git push` will work **without asking username/password**.
