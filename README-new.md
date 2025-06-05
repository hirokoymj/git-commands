# Git

- https://www.datacamp.com/blog/git-interview-questions-and-answers
- https://www.youtube.com/watch?v=e9lnsKot_SQ&t=75s
- https://git-scm.com/docs/git-branch
- https://www.youtube.com/watch?v=AWayLpQHJeE

## Four locatinos in Git

1. Working Directory - your local development environment where you make changes to your code
2. Staging Area
3. Local Repository
4. Remote Repository

![](./screen/four-locations.png)

## git clone

- From an existing Remote repository to Local Repository
- Clone a repository into a new directory
- https://git-scm.com/docs/git-clone

```js
$ git clone git://git.kernel.org/pub/scm/.../linux.git my-linux
$ cd my-linux
```

## git add

- Save files from Workind Directory to Staging Area to prepare the next commit snapshot.
- prepares them for staging.
- https://git-scm.com/docs/git-add

```js
git add .
git add filename
```

## git commit

- Save changes from Staging area to Local Repo. (With a comment)
- take a snapshot of the staging area and saves it to your local repo.
- Each commit creates a unique identifier, allowing you to track the history of changes in the repository.
- https://git-scm.com/docs/git-commit

```js
git commit -m "first commit"
git commit -am ## Stage and commit changes in one step.
```

## git pull

- To integrate your teammates's work, you use git pull which fetches changes from remote repository and merges them into your local repo.

## Git branching

Git branching allows you to diverge from the main codebase to develop a new feature without impacting the main code.

## git branch

- List, create, or delete branches
- List: `git branch` or `git branch --list`
- Create: `git branch <branchname>`
- Delete: `git branch -D <branchname>`
- https://git-scm.com/docs/git-branch

- Branching enables isolated development and ollaboration workflows.

## git switch

- Switch branches
- `git switch branchname`
- https://git-scm.com/docs/git-switch

## git checkout

- Switch branches or restore working tree files
- `git checkout -b my-branch` - Create a new branch named "new-branch" and check the resulting branch out.
- https://git-scm.com/docs/git-checkout

<!-- Git Merge/Git Rebase
resolving merge confilict s hwen changes overlap
Brancing enables isolated development and collaborating workflows. -->

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

## git status

- Displays the current state of the repository in Git.
- modified, Untracked, new file
- identify which files are staged for the next commit.
- A file in red ===> Unstaged
- A file in green ===> Staged
- https://git-scm.com/docs/git-status

<hr />

9. What is merge in Git?

**References:**

- https://stackoverflow.com/questions/9162271/fatal-not-a-valid-object-name-master
- https://stackoverflow.com/questions/66209755/how-do-i-create-git-branch-and-switch-at-a-time-when-creating-a-branch

# Memory notes
