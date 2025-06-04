## Daily development flow

1. Check your current branch.

   ```js
   git branch
   ```

2. Create your branch. A new branch is the copy of your current branch.

   ```
   git branch my-test-branch
   ```

3. Switch the branch that you created.

   ```js
    git checkout my-test-branch
   ```

4. Change code.

5. Commit your changes. Your changes are saved in `Staging Area`

   ```js
   git status
   git add .
   git commit -m "added new function"
   ```

6. Push your change to remote repository

   ```js
   git push origin [your branch name]
   ```

7. Login GitHub and check to see if your branch exists.

## HyreCar flow

1. JIRA ticket
2. git pull to get the latest code from master
3. create a branch
4. coding
5. done localhost:3000
6. make my localhost url to a public using ngrok command
7. A tester will test business logic and a UI designer test UI
8. Raise Pull Request
9. Check the codes by other developers. -> Push to master branch.
