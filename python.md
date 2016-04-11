# Python

Error Handling
```python
# define your own exceptions for custom handling
class MyCustomException(Exception):
  pass
  
def main():
  try: 
    ... block of code ...
    raise MyCustomException
    ...
  except MyCustomException as e:
    print "something bad happened"
  except KeyError as e:
    print "missing key in json object or dictionary: %s" % str(e)
  exception Exception as e:
    print str(e)
```

# Requests (REST Web Services)


# SQL Alchemy (Object Relation Mapping)

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
