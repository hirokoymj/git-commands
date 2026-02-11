# Git commands

## Four locations

1. Working Directory: File you edit, can be unstaged or staged.
2. Staging Area (index): Changes marked for the next commit, git add
3. Local Repository (.git): the hidden .git database that stores all commits, branches, and history on your machine.
4. Remote Repository (GitHub)

```bash
Working Directory
   ↓ git add
Staging Area
   ↓ git commit
Local Repository
```

- The local repository is the hidden .git database that stores all commits, branches, and history on your machine.

Q: How to “see” the local repository. See commits.
A: `git log --oneline`

Q: How to “see” the local repository. See branches (local repository)
A: `git branch`

## git fetch | git merge | git pull

- `git fetch` → download remote updates (==invisible the changes)
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

## git add

- Save changes to the staging area for the next commit
- Working Directory -> State Area

## git commit

- Save staged changes to the local repository

## git clone

- Copy a remote repository to a local directory

## git pull

- fetch + merge (automatic)
- fetch and merge remote changes into the current branch

## git push

- upload local commits to the remote repository

## git branch

- List all local branches

## git branch xxx

- Create a new branch (does not switch to it)

## git checkout -b new-branch

- Create a new branch and switch to it immediately

## git status

- show current repository state, staged vs unstaged changes.
- Red → unstaged
- Green → staged

## git diff

- show changes in working directory vs staging area

## git stash

- temporarily save uncommitted changes to reapply later

```bash
git stash
git pull origin master
git stash apply
```

## Merge conflict

- Merge Conflict occurs when changes made to the same part of the same file on two different branch.
- Resolve by checking the conflict markers (HEAD for current branch, incoming branch markers) and fixing manually.

## screenshots

![](./screen/git-4-locations.png)

## git rebase -i HEAD~x

- Git rebase is a handy tool to have for creating nice clean history in your git repository
- Ex. Squash 3 commits history to one

```
git log
git rebase -i HEAD~3
pick 1b9d9cb commit 1
pick 9917593 commit 2
pick a571ceb commit 3
------------>Suash commit 2 and 3
pick 1b9d9cb commit 1
squash 9917593 commit 2
squash a571ceb commit 3
:wq!
ESC key
------------> Edit the comment for 3 commits.
# This is a combination of 3 commits.
# This is the 1st commit message:

commit 1

# This is the commit message #2:

#commit 2

# This is the commit message #3:

#commit 3
:wq!
ESC key
------------
```

- https://www.youtube.com/watch?v=AWayLpQHJeE

## What is HEAD in Git?

- pointer to the current commit on the checked-out branch
  ![](./screen/HEAD-main.png)
  ![](./screen/HEAD-branch.png)

=======

## git reset vs git revert

- Undo a git commit.
- git reset -> Remove git commit history entirely.
- git revert -> add revert history.
- Already pushed ? `git revert` : `git reset`

![](/screen/git-reset.png)
![](/screen/git-revert-history.png)
![](/screen/git-reset-vs-git-revert.png)

- https://www.youtube.com/watch?v=GytsxgB4-HU
- Check if already pushed or not.

  `git log --oneline --branches --not --remotes`

**Summary**

```js
git log --oneline
git reset HEAD~1
git reset HEAD~3
git reset 3bde3a5
git revert a649881 //=> Edit a comment => Done! => the commit "a649881" Not Removed!!
```

<!-- ## git checkout .

- Deleted all uncommited changes forever! -->

## Pull Request (PR)

- A pull request is a proposal to merge changes from one branch into another. In a pull request, collaborators can review and discuss the proposed changes before integrating them into the main codebase
- Select `base` branch where you want to merge the curent branch. -> Add the title and description for a PR. -> create pull request.

![](./screen/pull-request.png)

![](./screen/merge-conflict.png)

- https://www.youtube.com/watch?v=FDXSgyDGmho
- https://www.youtube.com/watch?v=DloR0BOGNU0

## Pull Request merge options

**Create a merge commit (default)**

- [Git official doc](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/about-pull-request-merges#merge-your-commits)
- All commits from the feature branch are added to the base branch in a merge commit.

**Squash and merge**

- [Git official doc](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/about-pull-request-merges#squash-and-merge-your-commits)
- The pull request's commits are squashed into a single commit.

![](./screen/merge-options.png)

## git log --all --decorate --graph --oneline

- Shows git history with graphs.
- `A Dog` = `git log --all --decorate --oneline --graph`
  ![](./screen/git-log-adog.png)

## Daily coding routine with git

```js
git clone remote_repo
git branch mybranch
git checkout mybranch
//working...
git push origin mybranch
//Updating teammate's changes into mybranch
git switch main
git pull origin main
git switch mybranch
//When a merge conflict occurs, fixed them manually.
//Keep working
//Done mybranch
git add .
git commit -m "Done my tasks"
git push origin mybranch
//PR -> review -> Merged mybranch to main in Github.
```

## References:

- https://www.datacamp.com/blog/git-interview-questions-and-answers
- https://www.youtube.com/watch?v=e9lnsKot_SQ&t=75s
- https://git-scm.com/docs/git-branch
- https://stackoverflow.com/questions/9162271/fatal-not-a-valid-object-name-master
- https://stackoverflow.com/questions/66209755/how-do-i-create-git-branch-and-switch-at-a-time-when-creating-a-branch
- https://stackoverflow.com/questions/2304087/what-is-head-in-git
- https://stackoverflow.com/questions/1057564/pretty-git-branch-graphs
