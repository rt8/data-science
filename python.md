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
Engine string to connect to database
```python
mysql+pymysql://<username>:<password>@<host_name>:3306/<database_name>
```

Database table model
```python
import datetime
from sqlalchemy import Column, Integer, DateTime, String
from sqlalchemy import create_engine
from sqlalchemy.orm import sessionmaker
from sqlalchemy.ext.declarative import declarative_base

Base = declarative_base()

class NewTable(Base):
  __tablename__ = "NewTable"
  pk = Column(Integer, primary_key=True)
  date = Column(DateTime, default=datetime.datetime.now())
  fieldOne = Column(String(20)) 

  @classmethod
  def new_itinerary(cls,new_res_id):
    session = init_db_session() 
    new_row = cls(fieldOne='someText')
    session.add(new_row)
    session.commit()
    session.close()
```


# SQL Alembic (Database Schema Migrations)

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

# Pip (Package Management)
```bash
$ pip install <SomePackage>             # install package
$ pip show --files <SomePackage>        # list files installed for packaged
$ pip list                              # list packages
$ pip list --outdated                   # list old packages
$ pip install --upgrade <SomePackage>   # update package
$ pip uninstall <SomePackage>           # uninstall package
$ pip install -r <requirements.txt>     # import package dependencies
```

