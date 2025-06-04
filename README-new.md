# Git

- https://www.datacamp.com/blog/git-interview-questions-and-answers
- https://www.youtube.com/watch?v=e9lnsKot_SQ&t=75s
- https://git-scm.com/docs/git-branch

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

## git add

- Save files from Workind Directory to Staging Area to prepare the next commit snapshot.
- prepares them for staging.
- https://git-scm.com/docs/git-add

## git commit

- Save changes from Staging area to Local Repo. (With a comment)
- take a snapshot of the staging area and saves it to your local repo.
- Each commit creates a unique identifier, allowing you to track the history of changes in the repository.
- https://git-scm.com/docs/git-commit
- Record changes to the repository

git pull

- To integrate your teammates's work, you use git pull which fetches changes from remote repository and merges them into your local repo.

Git branching
allows you to diverge from the main codebase to develop a new feature without impacting the main code.

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

**References:**

- https://stackoverflow.com/questions/9162271/fatal-not-a-valid-object-name-master
- https://stackoverflow.com/questions/66209755/how-do-i-create-git-branch-and-switch-at-a-time-when-creating-a-branch

# Memory notes
