✅ Question 1 – Git Fundamentals

Q: What command unstages a file without deleting changes?

A: git restore --staged `<file>`

---

✅ Question 2 – Rebase vs Merge

Q: What is the difference between git merge and git rebase?

A:

- (org) git merge creates a new commit to preserve the original commit history, while git rebase rewrites the commits history resulting the history becomes a linear history.
- **git merge** combines branches and creates a new merge commit, preserving the original commit history.
- **git rebase** rewrites commit history by replaying commits on top of another branch, resulting in a linear history.

---

Q: After rebasing and updating history, what command should you use to push safely?

A: git push --force-with-lease

```
Because rebase rewrites commit history, a normal push will be rejected.
--force-with-lease safely updates the remote branch without overwriting others’ work.
```

---

✅ Question 1 – What Actually Happens?

```bash
git add .
git commit -m "Update feature"
git reset --soft HEAD~1
```

- The commit is removed, but the changes remain in the staging area (index).
- No code is lost.
- git status would show the files as Changes to be committed.
- (org) Canceled the latest commit, but the file is still staged.No code lost. git status shows staged file.

✅ Question 2 – Rebase Scenario
1️⃣ What happens to commits D and E?

```bash
main:     A --- B --- C
feature:            D --- E
```

**Someone pushes a new commit F to main.**

```bash
main:     A --- B --- C --- F
feature:            D --- E
```

You run:

```bash
git checkout feature
git rebase main
```

Questions:

Q1. What happens to commits D and E?

```bash
main:     A --- B --- C --- F
feature:                    D' --- E'
```

A1:

- D and E are replayed
- They become new commits (D', E')
- Commit hashes change

<hr />

Q3. Why would this be preferred before opening a PR?

A3: Rebasing keeps the history clean and linear, making the PR easier to review. It avoids unnecessary merge commits and reduces noise in the commit history.

<hr />

4. After this rebase, what must you be careful about when pushing?

- git push --force-with-lease
- Because commit hashes changed.

5.

- git stash apply → restores changes but keeps the stash
- git stash pop → restores changes and deletes the stash
