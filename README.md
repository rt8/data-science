# Datascience

# Mysql

Run sql on the command line (eg. in a bash shell script).  This will auto-login and does not prompt for password which can cause the bash shell script to stall.
```bash
 $ mysql $MYSQL_ARGS -e "$SQL_STATEMENT"
 # example: 
 $ mysql -u[username] -p[password] -h [host] [database_name] -e "select * from my_table limit 10;"
 ```

Load data from csv file into the DB table on the command line (eg. in a bash script).  Note: You can use any field delimiter you like such as pipes ('|') or tabs.
```bash
mysql $MYSQL_ARGS --local-infile -e "LOAD DATA LOCAL INFILE 'csvfile.csv' INTO TABLE <tableName> FIELDS TERMINATED BY ',' IGNORE 1 LINES;"
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
Frequently used
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

Merge branches that have conflicts
```bash
$ git checkout -b <newBranch>
$ git merge <branch1> <branch2>
$ git diff    #or use git mergetool
... now proceed to resolve branch conflicts using editor (eg. vim, eclipse, atom)...
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



