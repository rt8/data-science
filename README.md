# Datascience

# Mysql

Run sql on the command line (eg. in a bash shell script).  This will auto-login and does not prompt for password which can cause the bash shell script to stall.
```bash
 $ mysql $MYSQL_ARGS -e "$SQL_STATEMENT"
 $ mysql -u[username] -p[password] -h [host] [database_name] -e "select * from my_table limit 10;"
 ```

Delete all data in a table
```sql
truncate tableName
```

List the next autoincrement id
```sql
SELECT TABLE_NAME, `AUTO_INCREMENT` FROM  INFORMATION_SCHEMA.TABLES where TABLE_NAME like 'tablename%';
```

# Git 
Frequently
```bash
$ git checkout -b <newBranchName>   # remember to first checkout master branch
$ git checkout <branchName>
$ git checkout -- <filename>
$ git status
$ git diff
$ git diff <fileName>
$ git diff --staged
$ git add <fileName>
$ git stash
$ git commit -v 
$ git remote -v
$ git push <remoteName> <remoteBranchName>
$ git pull <remoteName> <remoteBranchName>
```

Merge branches
```bash
$ git checkout -b <newBranch>
$ git merge <branch1> <branch2>
$ git diff    #or use git mergetool
... resolve branch conflicts ...
$ git add <fileName>
$ git commit -v
$ git push <remoteName> <remoteBranchName>
```



Squash commits.  This means several commits are combined to look like 1 commit so the code history looks more tidy.
```bash
$ git reset --soft head~2    #2 is the number of previous commits to squash
$ git commit -v
$ git push <remote> <branchName>
$ git push <remote> +<branchName>    # add "+" symbol to force overwrite of remote git repo
```



