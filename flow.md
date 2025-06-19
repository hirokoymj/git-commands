## HyreCar

1. JIRA ticket
2. git pull to get the latest code from master
3. create a branch
4. coding
5. done localhost:3000
6. make my localhost url to a public using ngrok command
7. A tester will test business logic and a UI designer test UI
8. Raise Pull Request
9. Check the codes by other developers. -> Push to master branch.

## Hays Japan

1. (develop) git pull // Gets the latest develop
2. (my-branch) git checkout my-branch // Switch a branch
3. (my-branch) git pull origin develop // REBASE BETWEEN develop and my-branch.
4. (my-branch) ==== When conflicts happens, fix them manually.
5. (my-branch) git add .
6. (my-branch) git rebase --continue
7. (my-branch) git reset origin/develop // SQUASH MULTIPLE COMMITS HERE!!!
8. (my-branch) git add .
9. (my-branch) git commit -m 'some commit message'
10. (my-branch) git push my-branch --no-verify --force

- https://stackoverflow.com/questions/2472254/when-should-i-use-git-pull-rebase

```js
git reset origin/master
```

## git reflog

- listed all the tips of branches.

```js
// checking all logs
git reflog

//you can rollback at hash number 12345
git reset --hard 12345
```
