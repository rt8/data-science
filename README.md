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
