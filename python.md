# Python

##Error Handling
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

##JSON

```python
import json
# convert string to json 
jdata = json.loads(aJsonString)

# convert json to string
print json.dumps(aJsonObject)

# pretty print json
def prettypring(jdata):
  return json.dumps(jdata, sort_keys=True, indent=4, separators=(',', ': '))

# access nested json objects
jdata = json.loads(aJsonString)
print jdata['people'][1]['name']
for idx in range(0, len(jdata['people'])):
  print jdata['people'][idx]['name']
```

## Requests (REST Web Services)
Access REST web services. Also: 

1. Send http authentication headers and json in body with http request.  
2. Check response for error.
```python
import requests
response = requests.post('https://www.web.com/resource', 
                         headers={'header1':'value1'},
                         data=json.dumps({"field":"value"})
if 'Error' in json.loads(response.text):
  responseMsg = str(r.status_code) + "\n" + str(r.headers) + str(r.content)
  raise Exception("[error] %s" % responseMsg) 
```

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
  def create_new_row(cls, textValue):
    engine = create_engine('ENGINE_STRING')
    Base.metadata.bind = engine
    session = sessionmaker(bind=engine) 
    new_row = cls(fieldOne=textValue)
    session.add(new_row)
    session.commit()
    session.close()
```


## SQL Alembic (Database Schema Migrations)

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

## Pip (Package Management)
```bash
$ pip install <SomePackage>             # install package
$ pip show --files <SomePackage>        # list files installed for packaged
$ pip list                              # list packages
$ pip list --outdated                   # list old packages
$ pip install --upgrade <SomePackage>   # update package
$ pip uninstall <SomePackage>           # uninstall package
$ pip install -r <requirements.txt>     # import package dependencies
```


## VirutalEnv (Environment Manager)

* Installing VirutalEnv will also install the latest version of pip
* When VirtualEnv is activated, any packages installed by pip will be stored in the VirtualEnv site-packages directory

```bash
$ curl -O https://pypi.python.org/packages/source/v/virtualenv/virtualenv-X.X.tar.gz    # download virtualenv
$ tar xvfz virtualenv-X.X.tar.gz                                                        # uncompress
$ cd virtualenv-X.X 
$ python virtualenv.py myVE                                                             # create new virutal env
$ source bin/activate                                                                   # activate env dependencies
$ deactivate                                                                            # deactivate env dependencies
```
