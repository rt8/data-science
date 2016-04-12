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
    ... block of code ...
  except MyCustomException as e:
    print "something bad happened"
  except KeyError as e:
    print "missing key in json object or dictionary: %s" % str(e)
  exception Exception as e:
    print str(e)
```

JSON
```python
# convert string to json 
jdata = json.loads(aJsonString)

# convert json to string
print json.dumps(aJsonObject)
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

# Pip
```bash
$ pip install SomePackage				      # install package
$ pip show --files SomePackage			  # list files installed for packaged
$ pip list                            # list packages
$ pip list --outdated					        # list old packages
$ pip install --upgrade SomePackage		# update package
$ pip uninstall SomePackage			      # uninstall package
$ pip install -r requirements.txt			# import package dependencies


```

