**Q1**

- What command unstages a file without deleting changes?

**A1**

- git restore --staged `<file>`

---

**Q2**

- What is the difference between git merge and git rebase?

**A2**

- **git merge** combines branches and creates a new merge commit, preserving the original commit history.
- **git rebase** rewrites commit history by replaying commits on top of another branch, resulting in a linear history.

---

**Q3:**

- After rebasing and updating history, what command should you use to push safely?

**A3:**

- git push --force-with-lease
- Because rebase rewrites commit history, a normal push will be rejected.
- `--force-with-lease` safely updates the remote branch without overwriting others’ work.

---

**Q4:**

- What Actually Happens?

```bash
git add .
git commit -m "Update feature"
git reset --soft HEAD~1
```

**A4:**

- The commit is removed, but the changes remain in the staging area (index).
- No code is lost.
- git status would show the files as Changes to be committed.

---

**Q5:**

```bash
main:     A --- B --- C
feature:            D --- E

# Someone pushes a new commit F to main.
main:     A --- B --- C --- F
feature:            D --- E

# You run:
git checkout feature
git rebase main
```

- What happens to commits D and E?

**A5:**

- D and E are replayed.
- They become new commits (D', E'). It means the commit hashes change.

```bash
main:     A --- B --- C --- F
feature:                    D' --- E'
```

<hr />

**Q6:**

- Why would this be preferred before opening a PR?

**A6:**

- Rebasing keeps the history clean and linear, making the PR easier to review. It avoids unnecessary merge commits and reduces noise in the commit history.

<hr />

**Q7:**

- After this rebase, what must you be careful about when pushing?

**A7:**

- `git push --force-with-lease`
- Because commit hashes changed.

---

**Q8:**

What is difference between git stash apply vs git stash pop?

**A8:**

- git stash apply → restores changes but keeps the stash.
- git stash pop → restores changes and **deletes** the stash.

---

**Q9:**

- You are on branch feature/login. Your commit history looks like this. You made commits D and E on feature/login.

```bash
A -- B -- C  (main)
       \
        D -- E  (feature/login)

>git rebase main
```

**Q9-1:**

- What happens to commits D and E after the rebase?

**A9-1:**

- Commits D and E are recreated on top of the latest commit on main, creating a linear history.

<hr />

**Q9-2:**

- Does Git modify the original commits or create new ones?

**A9-2:**

- Git creates new commits (D' and E') with new commit hashes.

<hr />

**Q9-3:**

- What will the commit history look like after the rebase? (Draw it.)

**A9-3:**

```bash
A -- B -- C -- D' -- E'   (feature/login)
             ^
            main
```

<hr />

**Q9-4:**

- What is one advantage of using git rebase instead of git merge in this case?

**A9-4:**

- Rebasing creates a clean, linear commit history, which makes the project history easier to read and manage.

---

**Q9-5:**

- When should you avoid using git rebase?

**A9-5:**

- shared branches that other team members are using, because it rewrites commit history.

---
