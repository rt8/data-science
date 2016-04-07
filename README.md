# Datascience

# Mysql

List the next autoincrement id
```sql
SELECT TABLE_NAME, `AUTO_INCREMENT` FROM  INFORMATION_SCHEMA.TABLES where TABLE_NAME like 'tablename%';
```
