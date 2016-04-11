# Python

# Requests

# SQL Alembic

Check the version of current database schema
```python
$ alembic current
```

Check the version of most recent migration script
```python
$ alembic heads
```

Generate migration script
```python
$ alembic revision autogenerate -m "your message"
```

Execute migration script on datbase
```python
$ alembic upgrade heads
```

Reverse changes of migration script
```python
$ alembic downgrade -1
```
