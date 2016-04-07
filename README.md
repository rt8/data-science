# Datascience

# Mysql

Run sql on the command line (eg. in a bash shell script)
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

Squash commits.  This means several commits are combined too look like 1 commit so the code history looks more tidy.
```bash
$ git reset --soft head~2    #2 is the number of previous commits to squash
$ git commit -v
$ git push <remote> <branchName>
$ git push <remote> +<branchName>    # add "+" symbol to force overwrite of remote git repo
```


```
