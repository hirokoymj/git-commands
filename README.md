# Git commands

## Four locations

1. Working Directory (your local development env)
2. Staging Area
3. Local Repository
4. Remote Repository

![](./screen/git-4-locations.png)
![](./screen/git-local-locations.png)

## git clone

- An existing Remote Repo -> Local Repo.
- Clone a repository into a new directory.
- https://git-scm.com/docs/git-clone

## git add

- Save files from Workind Directory to the staging area to prepare the next commit snapshot.
- Working Directory -> State Area
- https://git-scm.com/docs/git-add

## git commit

- Save changes from Staging Srea to Local Repo with a comment.
- take a snapshot of the staging area and saves it to your local repo.
- A commit hash == a unique identifier
- https://git-scm.com/docs/git-commit
  ![](./screen/commit-hash.png)

## git pull

- To integrate your teammates's work, you use `git pull` which **fetches** changes from remote repository and **merges** them into your local repo.
- Fetch and Merge.
- https://git-scm.com/docs/git-pull

![](./screen/git-fetch-git-pull.png)

## git fetch vs git pull?

**git fetch:**

- The git fetch command retrieves changes from a remote repository to the local repository.
- but it does not update the working directory or merge any changes into the current branch.
- This means that after fetching, you can review the changes made in the remote repository without affecting your local work.

**git pull**

- fetching changes from a remote repo and merging them into the current your branch in **one step**. Fetch and Merge.

<hr />

## git branch

- List, create, or delete branches
- List: `git branch` or `git branch --list`
- Create: `git branch <branchname>`
- Delete: `git branch -D <branchname>`
- Git branching - allows you to diverge from the main codebase to develop a new feature without impacting the main code.
- https://git-scm.com/docs/git-branch

## git switch

- Switch branches
- `git switch branchname`
- https://git-scm.com/docs/git-switch

## git checkout

- Switch branches or restore working tree files.
- `git checkout -b my-branch` - Create a new branch named "new-branch" and check the resulting branch out.
- https://git-scm.com/docs/git-checkout

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

## What is a conflict in Git?

- https://www.youtube.com/watch?v=DloR0BOGNU0

1. `git merge` or `git pull`
2. `git status` - check which files are conflicted.
3. Conflict markers:

- `HEAD` marker: - your branch changes.

  ```js
  <<<HEAD marker (Current change)
  ```

- Incoming marker: changes from another branch.
  ```js
  >>>>>main (Incoming Change)
  ```

4. Manually pick the changes either HEAD marker or Incoming marker. Merge conflict doesn't overwide the changes in your branch automatically.
5. Run `git status` again but git doesn't know your change so run `git add` to add the changes to the state area each file.

## What is HEAD in Git?

```
% cat .git/HEAD
ref: refs/heads/test1
```

## git status

- Displays the current state of the repository in Git.
- modified, Untracked, new file
- identify which files are staged for the next commit.
- A file in red ===> Unstaged
- A file in green ===> Staged
- https://git-scm.com/docs/git-status

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

<hr />

## git checkout . !!!Careful!!

- Deleted all uncommited changes forever!

## References:

- https://www.datacamp.com/blog/git-interview-questions-and-answers
- https://www.youtube.com/watch?v=e9lnsKot_SQ&t=75s
- https://git-scm.com/docs/git-branch
- https://stackoverflow.com/questions/9162271/fatal-not-a-valid-object-name-master
- https://stackoverflow.com/questions/66209755/how-do-i-create-git-branch-and-switch-at-a-time-when-creating-a-branch
