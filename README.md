# Git commands

## Four locations

1. Working Directory: File you edit, can be unstaged or staged.
2. Staging Area: Changes marked for the next commit, git add
3. Local Repository (.git): the hidden .git database that stores all commits, branches, and history on your machine.
4. Remote Repository (GitHub)

```bash
Working Directory
   ↓ git add
   ↑ git restore
Staging Area
   ↓ git commit
   ↑ git reset HEAD
Local Repository
```

- Unstage == Keep file changes
- **The local repository** is the **hidden .git database** that stores all commits, branches, and history on your machine.

```
Q: How to “see” the local repository. See commits.
A: git log --oneline
```

```
Q: How to “see” the local repository. See branches (local repository)
A: git branch
```

## Prepare to Commit

### git add

- Save changes to the staging area for the next commit.
- Working Directory ==> State Area

### git restore --staged

- Unstage a file
  ```bash
  git add xxx→ stage a file
  git restore --staged xxx → unstage a file
  ```

### git add <=> git restore

- stage changes <=> unstage changes

### git status

- show current repository state, staged vs unstaged changes.
- Red → unstaged
- Green → staged

---

## Make Commits

### git commit

- Save staged changes to the local repository.

### git reset HEAD~1

- Undo commit and unstaged

```bash
git add → stage changes
git restore --staged → unstage changes
git commit → save staged changes
git reset --soft → undo commit, keep staged
git reset → undo commit, keep unstaged
```

### git commit --amend

- Edit the latest commit message

---

## Merge vs Regase

### git fetch | git merge | git pull

- `git fetch` → download remote updates TO `remote-tracking branches` (==NO visible changes)
- `git merge` → change your branch
- `git pull` → fetch + merge (automatic)
- Fetch is like checking the menu.
- Merge is like ordering the food 🍔
- `origin/main` ==> local, read-only references of the remote main branch. (== remote-tracking branches)
- `origin/feature-test` ==> local, read-only references of the remote feature-test branch. (==remote-tracking branches)

```bash
// I am main branch.
git fetch origin 					# update remote-tracking branches
git diff main origin/feature-test	# preview changes before merge
git merge origin/feature-test		# apply changes to main
```

### git pull

- fetch + merge (automatic)
- fetch and merge remote changes into the current branch

### git push

- upload local commits to the remote repository

### git diff

- show changes in working directory vs staging area

---

## Branch

### git branch

- List all local branches

### git branch xxx

- Create a new branch (does not switch to it)

## git checkout -b new-branch

- Create a new branch and switch to it immediately

---

## git stash

- temporarily save uncommitted changes to reapply later

```bash
git stash
git pull origin master
git stash apply
```

## git clone

- Copy a remote repository to a local directory

---

## rebase

### git rebase -i HEAD~x

- squash multiple commits into one
- squash these 3 commits into 1. `git rebase -i HEAD~3`

```bash
pick 0a2a79e test 2/11 ## Keep a first commit
squash 36d7e81 commit test 2 # squash
squash fb0cf39 commit test -3 # squash
OR
pick 0a2a79e test 2/11 ## Keep a first commit
s 36d7e81 commit test 2 # squash
s fb0cf39 commit test -3 # squash
// Escape wq!
// Add one clean commit
```

### git rebase | git rebase -i

**Normal rebase is for syncing code; interactive rebase is for cleaning history.**

- `git rebase develop`: syncing code
- `git rebase -i develop`:interactive rebase is for cleaning history before pushing / opening PR

  ```js
  pick a1b2c3 commit 1
  s d4e5f6 commit 2
  s g7h8i9 commit 3
  ```

```bash
# Sync with develop (may happen many times)
git rebase develop

# Finish feature work
# ...

# Clean history ONCE
git rebase -i develop

# Push
git push origin my-branch --force-with-lease
```

---

## History

## git log --oneline --graph

- Show commit history with graph

```bash
git log --oneline → compact commit history
git log --oneline --graph → commit history with graph
```

## Misc

### Merge conflict

- Merge Conflict occurs when changes made to the same part of the same file on two different branch.
- Resolve by checking the conflict markers (HEAD for current branch, incoming branch markers) and fixing manually.

### What is HEAD in Git?

- pointer to the current commit on the checked-out branch.

## A linear history

```bash
A — B — C — D
```

```bash
A — B — C — M
        \   /
         D — E
```

To get a linear history, teams usually require:

- rebase (not merge)
- squash feature commits
- fast-forward merges only

```bash
# Update develop
git checkout develop
git pull origin develop
# Switch to your feature branch
git checkout my-branch
git rebase develop ## git merge vs git rebase
### !!! If conflicts happen → fix them, then:
git add .
git rebase --continue
### Then, I keep working on my-branch to complete my tasks.

git rebase -i develop ## interactive rebase to edit your own commits (squash, reorder, rename) on top of develop.
git push origin my-branch --force-with-lease
```

```bash
## Before rebase
A — B — C  (develop)
       \
        D  (feature1)
## After rebase
A — B — C — D'  (feature1)
```

## When does main get a linear history?

```bash
git checkout develop
git merge feature1

# A — B — C — D'  (develop)
```

## screenshot

![](./screen/git-4-locations.png)

## Reference

- https://git-scm.com/docs/git
- https://git-scm.com/cheat-sheet#make-commits
