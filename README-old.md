## Squash my last X commits together

```js
// Check how many commits you want to combine.
git log
// Combine three commits
git reset --soft HEAD~3 &&
git commit

// Push to remote
git push origin test-branch
```

**BEFORE squashing**

```js
% git log
commit 9b1d29626cb4fae62da7492028048fcea0f159b5 (HEAD -> master)
Author: Hiroko Yamaji <hiroko@hirokoymj.com>
Date:   Tue Jan 18 17:55:28 2022 +0900

    second commit

commit d2fd9e8a62b6518e07890fb352694d172b633b54
Author: Hiroko Yamaji <hiroko@hirokoymj.com>
Date:   Tue Jan 18 17:55:02 2022 +0900

    first commit

commit d0499f4c9f87da9b98a8fbffbeb40c408d51fdc6 (origin/master)
Author: Hiroko Yamaji <hiroko@hirokoymj.com>
Date:   Tue Jan 18 14:42:01 2022 +0900

    Updated readme
```

**AFTER squashing**

```js
commit b6be0711908dccaa83150e57f3c3932b72596b9a (HEAD -> master)
Author: Hiroko Yamaji <hiroko@hirokoymj.com>
Date:   Tue Jan 18 17:57:22 2022 +0900

    Combined two commits here!

commit d0499f4c9f87da9b98a8fbffbeb40c408d51fdc6 (origin/master)
Author: Hiroko Yamaji <hiroko@hirokoymj.com>
Date:   Tue Jan 18 14:42:01 2022 +0900

    Updated readme
```

<hr />

## Squash my last X commits together(after pushing to remote)

```js
// Check how many commits you want to combine.
git log
// Combine three commits
git reset --soft HEAD~3 &&
git commit

// Push to remote with force option
git push origin test --force
```

<hr />

## Merge

Trying to merge `test-branch` to `master` branch.

1. Check if you are currently master branch.
   ```js
   git branch
   ```
2. Merge `test-branch` to `master`
   ```js
   git merge test-branch
   ```
3. Push the upated master branch to remote repository
   ```js
   git push origin master
   ```

<hr />

## Pull

Get the latest code from remote repository so your local repository could be updated. When your co-workers update a master branch, you should get the latest one!

```js
git pull master
```

<hr />

## Stash

Using `stash` command, you can hold your all changes temporary and makes clean working directory. So you can merege the latest master into your own branch.

```js
git stash //-----> Hold all your changes and your branch becomes clean.
git merge master //---> you can merge the latest master here!
git stash apply	// ---> Changed back to your changes.
```

<hr />

## Log

Trying to see the git log.

```js
git log ---graph --oneline
```

<hr />

## Delete Remote Branch

```js
git push origin --delete <remote branch name>
```

```js
hiroko@owners-MacBook-Pro git-command % git push origin --delete demo
To https://github.com/hirokoymj/git-command.git
 - [deleted]         demo
```

<hr />

## Delete Local Branch

```js
git branch -D <branch name>
```

<hr />

## Show remote repository in your local

```js
git remote show origin

git fetch
git checkout test
```

<hr />

## git reset HEAD^

https://dzone.com/articles/git-reset-head

## Rename local branch

If you want to rename a branch while pointed to any branch, do:

```js
git branch -m <oldname> <newname>
```

If you want to rename the current branch, you can do:

```js
git branch -m <newname>
```

## Switching current repo to another one

```js
git remote set-url origin <new repository> to update your config
```

git remove -v to see your current repository

## Undo your commit

```js
git reset HEAD~
```

## Checkout remote branch

Use `checkout` instead of `git pull branch-name`

```js
git checkout [remote branch name]
```

## Modify a commit message

- Run `git commit --amend`.

```js
git commit --amend
```

- In Editor mode you can change a current message.

```js
comment 1

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# Date:      Fri Dec 17 11:51:29 2021 +0900
#
```

### References:

- [Squash my last X commits together using Git](https://stackoverflow.com/questions/5189560/squash-my-last-x-commits-together-using-git)
- [Revert to a commit by a SHA hash in Git?](https://stackoverflow.com/questions/1895059/revert-to-a-commit-by-a-sha-hash-in-git)
