🌐 [English](README.md) | [Español](README.es.md) | [Português](README.pt.md)

# Module 03 — Branches

## Objective
Learn to work in parallel on separate branches so that each person's work stays isolated until it's ready to be integrated into main.

## Key concepts

- **Branch**: an independent line of work. Changes you make here don't affect `main` until you merge.
- **main**: the principal branch — it should always be in a working state.
- **Merge**: integrating the changes from one branch into another.

```
main:      A --------- B ----------- E (merge)
                        \           /
feature/ana:             C --- D ---
```

---

## Step by step

### Step 1 — See existing branches
```bash
git branch
```
The asterisk (*) marks the branch you are currently on. You should be on `main`.

### Step 2 — Make sure your main is up to date
```bash
git pull origin main
```

### Step 3 — Create your own branch
Replace `your-name` with your actual name (no spaces, use hyphens):
```bash
git checkout -b feature/your-name
```

Verify which branch you are on:
```bash
git branch
```

### Step 4 — Make your change
Open `ideas.txt` and add your idea on a new line.

### Step 5 — Commit on your branch
```bash
git add 03-ramas/ideas.txt
git commit -m "feat: add idea from [your name]"
```

### Step 6 — Push your branch to the remote
```bash
git push origin feature/your-name
```

### Step 7 — Switch back to main and update it
```bash
git checkout main
git pull origin main
```

### Step 8 — Merge your branch into main
```bash
git merge feature/your-name
```

If no one else edited the same lines, Git will merge automatically.

### Step 9 — Push the updated main
```bash
git push origin main
```

### Step 10 — See the full history with branches
```bash
git log --oneline --graph --all
```

---

## Extra challenge
After everyone has merged their branches, have two people edit the **same line** of `ideas.txt` in their respective branches. Merge the first one normally. Then try to merge the second — you will get a conflict. Resolve it as you learned in Module 02.

---

## 🙋 Doing this alone?

Create two branches in sequence: `feature/version-a` and `feature/version-b`. Make a different change in each. Merge the first, then the second. Observe the history with `git log --oneline --graph --all` to see how the branches look.

For the extra challenge: make both branches edit the same line of `ideas.txt`, then try to merge both. You will produce a conflict to resolve on your own.

---

## Hints
<details>
<summary>Show hints</summary>

- Name your branches descriptively: `feature/login`, `fix/broken-link`, `draft/spec-v2`.
- Always make sure you are on the destination branch (e.g. `main`) before running `git merge`.
- If the merge has no conflicts, Git does it automatically (fast-forward or automatic merge).
- After merging, you can delete the branch if you no longer need it: `git branch -d feature/your-name`

</details>

---

Next: [04-historial](../04-historial/README.md)
