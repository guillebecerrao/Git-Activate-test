🌐 [English](README.md) | [Español](README.es.md) | [Português](README.pt.md)

# Module 00 — Setup

> Complete this checklist **before the workshop session**. Every participant must do this individually on their own machine.
>
> If you get stuck on any step, contact the workshop facilitator before the session starts.

---

## Checklist

### ✅ Step 1 — Create an account

If you don't have one yet, create an account on the platform where this repository lives:

- **GitHub:** https://github.com/signup
- **GitLab:** https://gitlab.com/users/sign_up

### ✅ Step 2 — Accept the collaborator invitation

The facilitator will send you an invitation to collaborate on the repository. Check your email or go to the platform's notifications and **accept the invitation**.

> Without this step, you will be able to clone and work locally, but you won't be able to push your changes to the shared repository.

### ✅ Step 3 — Install Git

Check if Git is already installed:
```bash
git --version
```

If you see a version number (e.g. `git version 2.43.0`), you're good. If not:

- **macOS:** `brew install git` or download from https://git-scm.com
- **Windows:** Download Git for Windows from https://git-scm.com — it includes **Git Bash**, which you should use for all commands in this workshop.
- **Linux:** `sudo apt install git` (Ubuntu/Debian) or `sudo dnf install git` (Fedora)

### ✅ Step 4 — Configure your identity

Git needs to know who you are to sign your commits:
```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

Verify it worked:
```bash
git config --list
```
You should see your name and email in the output.

### ✅ Step 5 — Create an SSH key

SSH is a secure way to authenticate with GitHub/GitLab without typing your password on every push.

> **Windows users:** run the following commands in **Git Bash**, not in Command Prompt or PowerShell.

```bash
ssh-keygen -t ed25519 -C "your@email.com"
```

- Press **Enter** to accept the default file location (`~/.ssh/id_ed25519`)
- You can set a passphrase for extra security, or press **Enter** twice to skip it

### ✅ Step 6 — Add your SSH key to GitHub or GitLab

First, display your public key and copy the entire output:
```bash
cat ~/.ssh/id_ed25519.pub
```
The output starts with `ssh-ed25519`. Select and copy the whole line.

Then add it to your account:

**GitHub:**
1. Go to your profile → **Settings** → **SSH and GPG keys** → **New SSH key**
2. Give it a title (e.g. "My laptop")
3. Paste the key and click **Add SSH key**

**GitLab:**
1. Click your avatar (top right) → **Preferences** → **SSH Keys**
2. Paste the key, give it a title, and click **Add key**

### ✅ Step 7 — Test your SSH connection

```bash
# GitHub
ssh -T git@github.com

# GitLab
ssh -T git@gitlab.com
```

Expected responses:
- **GitHub:** `Hi username! You've successfully authenticated, but GitHub does not provide shell access.`
- **GitLab:** `Welcome to GitLab, @username!`

> If you see a warning like `The authenticity of host ... can't be established`, type `yes` and press Enter. This is normal on the first connection.

### ✅ Step 8 — Clone the repository

Get the **SSH URL** from the repository page (look for the **Clone** button and select the **SSH** option). Then run:

```bash
git clone git@github.com:OWNER/Git-Activate-test.git
# or
git clone git@gitlab.com:OWNER/Git-Activate-test.git
```

Replace `OWNER` with the username or group name of whoever owns the repository. The facilitator will give you the exact URL.

### ✅ Step 9 — Final verification

Enter the cloned folder and check the history:
```bash
cd Git-Activate-test
git log --oneline
```

You should see a list of past commits. If you do — you're all set! 🎉

---

## Common issues

| Problem | Likely cause | Solution |
|---|---|---|
| `Permission denied (publickey)` | SSH key not added to account or wrong key | Redo Steps 5–7 |
| `Repository not found` | Wrong URL or invitation not accepted | Check Step 2 and the clone URL |
| `git: command not found` | Git not installed | Redo Step 3 |
| SSH warning on first connect | Normal behavior | Type `yes` and press Enter |
| `git push` fails with "rejected" | You haven't accepted the invitation | Check Step 2 |

---

Ready? Go to [01-primer-commit](../01-primer-commit/README.md) — see you in the session!
