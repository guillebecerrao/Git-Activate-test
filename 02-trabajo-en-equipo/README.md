🌐 [English](README.md) | [Español](README.es.md) | [Português](README.pt.md)

# Module 02 — Working as a Team

## Objective
Learn the day-to-day flow for collaborating on a shared repository: how to sync your work with your teammates', and what to do when two people change the same thing.

## Key concepts

- **origin**: the default name for the remote repository (on GitHub/GitLab).
- **push**: upload your commits to the remote.
- **pull**: download your teammates' commits to your machine.
- **Conflict**: when two people change the same line of the same file. Git can't decide which version to keep — it needs you to resolve it.

---

## Part A — The daily flow

### The scenario
You've made changes locally and committed them. Meanwhile, a teammate also made changes and pushed before you. When you try to push, Git rejects it — your local copy is behind the remote.

```
Remote:  A --- B --- C   ← your teammate pushed C
Local:   A --- B --- D   ← your commit D
                    ↑
              rejected! you need to pull first
```

### Step 1 — Everyone edits equipo.txt
Open `equipo.txt` and add a line with your name, role, and today's date.

### Step 2 — Stage and commit your change
```bash
git add 02-trabajo-en-equipo/equipo.txt
git commit -m "feat: add [your name] to team file"
```

### Step 3 — Try to push
```bash
git push origin main
```

**If you were the first person to push:** it will succeed. Wait for your teammates to try.

**If someone else pushed first:** you will see an error like this:
```
! [rejected] main -> main (fetch first)
error: failed to push some refs
```
This is not a mistake — it's Git protecting everyone's work. Continue to Step 4.

### Step 4 — Pull your teammate's changes
```bash
git pull origin main
```

If your changes and your teammate's are in **different lines**, Git will merge them automatically. You will see a message like `Merge made by the 'ort' strategy` — that's a success.

If they are in the **same line**, you will get a conflict. See Part B.

### Step 5 — Push again
```bash
git push origin main
```

### Step 6 — Verify
```bash
git log --oneline
```
You should see both your commit and your teammate's in the history.

---

### The golden rule

> **Pull → Work → Add → Commit → Pull → Push**

Always pull before you start working, and pull again before you push. This minimizes conflicts.

---

## Part B — Resolving a conflict

### The scenario
Two people edited the same line. Git shows you both versions and asks you to decide.

### What a conflict looks like

When you run `git pull` and there is a conflict, Git will tell you which file has the problem. Open it and you will see:

```
<<<<<<< HEAD
Your version of the line
=======
Your teammate's version of the line
>>>>>>> origin/main
```

### How to resolve it

1. Open the file with the conflict (`conciliar.txt`).
2. Decide what the final version should be — yours, your teammate's, or a combination of both.
3. Delete the conflict markers: `<<<<<<<`, `=======`, `>>>>>>>`.
4. Save the file.
5. Stage and commit:
```bash
git add 02-trabajo-en-equipo/conciliar.txt
git commit -m "fix: resolve conflict in conciliar.txt"
```
6. Push:
```bash
git push origin main
```

### To practice this with your team

- **Person A:** edit line 8 of `conciliar.txt`, commit and push.
- **Person B:** edit the same line 8 of `conciliar.txt` (without pulling first), commit and try to push.
- **Person B:** will see the rejection. Pull, resolve the conflict, and push again.

> Tip: before resolving, talk to Person A. A conflict is a conversation starter, not just a technical problem.

---

## 🙋 Doing this alone?

**For Part A:** make your change locally, commit and push. Then open the repository in your browser (GitHub or GitLab), navigate to `equipo.txt`, click the **edit** (pencil) icon, add a second line, and commit directly from the web interface. Now your local copy is behind the remote — run `git pull` to see the sync in action.

**For Part B:** repeat the same but edit **the same line** from the web interface. When you pull locally, you will get a conflict to resolve.

> This works because you accepted the collaborator invitation in `00-setup`. You have write access to the repository, including through the web interface.

---

## Hints
<details>
<summary>Show hints</summary>

- Always do `git pull` before starting to work each day.
- If `git push` fails with "rejected", it means you need to pull first — not that you did anything wrong.
- In a conflict, the `HEAD` section is what you have locally, and the section below `=======` is what came from the remote.
- After resolving a conflict, `git status` should show the file as staged (green) before you commit.

</details>

---

Next: [03-ramas](../03-ramas/README.md)
