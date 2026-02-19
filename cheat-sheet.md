# Git Summary

```bash
# Four locations
Working Dir → Staging → Local Repo → Remote Repo

# Prepare & commit
git add        # stage changes
git restore --staged  # unstage
git commit     # save snapshot to local repo
git commit --amend  # edit last commit
git reset --soft HEAD~1   # undo the latest commit (keep staged changes)

# Sync branches
git fetch      # update remote-tracking branches
git merge      # merge branches (creates merge commit)
git rebase     # replay commits for linear history
git pull       # fetch + merge (or rebase)

# History cleanup
git rebase -i  # squash / reorder / rename commits before PR

# Branching
git branch     # list branches
git checkout -b <branch>  # create & switch

# Share work
git push       # upload commits
git push --force-with-lease  # after rebase

# Inspect
git status     # state of files
git diff       # see changes
git log --oneline --graph  # history

# Temporary save
git stash      # save uncommitted work

### The "Linear History" Workflow

git checkout main && git pull
git checkout feature && git rebase main
git rebase -i main (Squash/Rename)
git push origin feature --force-with-lease
```
