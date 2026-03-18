🌐 [English](README.md) | [Español](README.es.md) | [Português](README.pt.md)

# Module 01 — My First Commit

## Objective
Complete the full Git cycle for the first time: edit a file, stage it, commit it, and push it to the shared repository.

## Key concepts

- **Working directory**: where you edit your files.
- **Staging area**: a preparation zone — you choose what goes into the next commit.
- **Commit**: a saved snapshot of the project at a specific moment.
- **Remote**: the shared repository on GitHub/GitLab that everyone pushes to and pulls from.

```
[Working Directory] → git add → [Staging Area] → git commit → [Local Repo] → git push → [Remote]
```

---

## Step by step

### Step 1 — Check the current state
Run this and observe what it tells you:
```bash
git status
```
You should see that everything is up to date — no changes yet.

### Step 2 — Edit a file
Open `notas.txt` in this folder and add a line with your name and one thing you want to learn.

### Step 3 — See what changed
```bash
git status
git diff
```
Notice the difference: `git status` tells you *which* files changed, `git diff` shows you *what* changed inside them.

### Step 4 — Stage your change
```bash
git add 01-primer-commit/notas.txt
```
Run `git status` again. Notice how the file moved from "not staged" (red) to "staged" (green).

### Step 5 — Commit
```bash
git commit -m "feat: add [your name] to notes"
```
The message should describe what you changed. Use present tense and be specific.

### Step 6 — Push to the shared repository
```bash
git push origin main
```
This uploads your commit to the remote so your teammates can see it.

### Step 7 — Verify
```bash
git log --oneline
```
You should see your commit at the top of the list.

---

## Extra challenge
Create a new file called `my-first-file.txt` inside this folder, write something in it, and make a commit.

## Hints
<details>
<summary>Show hints</summary>

- `git status` shows modified files (red = not staged, green = staged).
- `git add .` stages ALL modified files at once. Use it carefully.
- A good commit message describes WHAT you changed and WHY.
- The first time you push, Git might ask you to confirm your identity — that's normal.

</details>

---

Next: [02-trabajo-en-equipo](../02-trabajo-en-equipo/README.md)
