🌐 [English](README.md) | [Español](README.es.md) | [Português](README.pt.md)

# Module 04 — History

> This module is **optional but recommended**. It covers the tools you will reach for when something goes wrong in real collaborative work.

## Objective
Learn to navigate the change history, see exactly what changed and when, undo commits safely, and temporarily set work aside.

## Key concepts

- **git log**: see all commits in the project.
- **git diff**: see exactly which lines changed.
- **git revert**: create a new commit that undoes a previous one — the history stays intact.
- **git reset**: move the history pointer back. Use with caution.
- **git stash**: temporarily set aside uncommitted changes so you can work on something else.

---

## Step by step

### Step 1 — Explore the history

```bash
# Compact view
git log --oneline

# View with branches and merges
git log --oneline --graph --all

# Detailed view of a specific commit
git show <commit-hash>
```

### Step 2 — See differences

```bash
# Difference between your working directory and the last commit
git diff

# Difference between two commits
git diff <hash-1> <hash-2>

# Difference between a branch and main
git diff main..feature/my-branch
```

### Step 3 — Make a change to practice revert

Edit `experimento.txt` in this folder, add something, and commit:
```bash
git add 04-historial/experimento.txt
git commit -m "test: practice change for revert exercise"
```

### Step 4 — Undo the commit with revert

First, get the hash of the commit you want to undo:
```bash
git log --oneline
```
Then revert it:
```bash
git revert <commit-hash>
```
Git will open a text editor asking you to confirm the commit message — save and close it. Git creates a new commit that undoes the previous one. The history stays intact.

### Step 5 — Observe the result

```bash
git log --oneline
```
You will see both commits: the original and the one that reverts it.

---

## revert vs reset

| Command | What it does | When to use it |
|---|---|---|
| `git revert` | Creates a new commit that undoes changes | When you've already pushed (shared work) |
| `git reset --soft` | Undoes the commit, keeps changes staged | Only locally, before pushing |
| `git reset --hard` | Undoes the commit AND discards the changes | With caution — changes are lost |

> **Rule of thumb:** if the commit is already in the remote, always use `git revert`. Never use `git reset --hard` on shared history.

---

## Bonus: git stash

Imagine you're in the middle of editing a file and need to quickly switch to another branch (for example, to help a teammate). You don't want to commit an unfinished change.

```bash
# Save your uncommitted changes temporarily
git stash

# Switch branch, do what you need, come back
git checkout main
# ... do something ...
git checkout feature/your-branch

# Recover your saved changes
git stash pop
```

`git stash` is your "save for later" button.

---

## Extra challenge
Use `git blame experimento.txt` to see who modified each line of the file and in which commit.

## Hints
<details>
<summary>Show hints</summary>

- Never use `git reset --hard` on commits that are already in the remote — it will affect your teammates.
- `git revert` is the safe option for undoing in a shared project.
- The first 7 characters of the hash are enough to identify a commit.
- `git stash pop` recovers your most recently stashed changes. If you stash multiple times, use `git stash list` to see them all.

</details>
