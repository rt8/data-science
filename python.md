# Python

# Requests

# SQL Alembic

Check the version of current database schema
```bash
$ alembic current
```

Check the version of most recent migration script
```bash
$ alembic heads
```

Generate migration script
```bash
$ alembic revision autogenerate -m "your message"
```

Execute migration script on datbase
```bash
$ alembic upgrade heads
```

Reverse changes of migration script
```bash
$ alembic downgrade -1
```
