# Mysql


##Run SQL statements on the command line 
Useful for use in bash shell scripts.  This will auto-login and does not prompt for password which can cause the bash shell script to stall.
```bash
 $ mysql $MYSQL_ARGS -e "$SQL_STATEMENT"
 # example: 
 $ mysql -u[username] -p[password] -h [host] [database_name] -e "select * from my_table limit 10;"
 ```

##Load data from csv file into the DB table on the command line 
Useful for use in a bash script.  Note: You can use any field delimiter you like such as pipes ('|') or tabs.
```bash
mysql $MYSQL_ARGS --local-infile -e "LOAD DATA LOCAL INFILE 'csvfile.csv' INTO TABLE <tableName> FIELDS TERMINATED BY ',' IGNORE 1 LINES;"
```

## Some useful SQL statements

Query log files to group by date 
```sql 
SELECT date(`datetime_column`), count(*) 
FROM TABLE_NAME 
GROUP BY date(`datetime_column`)  
ORDER BY `datetime_column` desc 
LIMIT 10;

```

Delete all data in a table
```sql
truncate tableName
```

List the next autoincrement id
```sql
SELECT TABLE_NAME, `AUTO_INCREMENT` 
FROM  INFORMATION_SCHEMA.TABLES 
WHERE TABLE_NAME like 'tablename%';
```
