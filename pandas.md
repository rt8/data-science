# Pandas

## Setup Pandas and associated packages
Miniconda is the easiest way to install Pandas and requires the least disk space.
```sh
$ bash Miniconda2-latest-Linux-x86_64.sh        # Download the install file and then run:
$ conda create -n <envName> python=3.4 pandas   # Create environment and install pandas
$ source activate <envName>                     # Activate the new environment
$ conda install scikit-learn                    # install Scikit-learn
$ conda install jupyter                         # Install Jupyter Notebook
$ conda install matplotlib                      # Install Matplotlib
$ conda search <package_name>                   # Find packages to install
$ conda env list                                # Show environments
$ conda list                                    # Show installed packages
$ ipython notebook                              # Start Jupyter in browser
```

## Pandas usage
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# read csv file into dataframe
df = pd.read_csv("file_name", sep=",", encoding="", index_col="field_name")

# write dataframe to csv file
outputPath = "my.csv"
df.to_csv(path_or_buf=outputPath, index=False)

# rename column
colsList = {oldColName1 : newColName1,
            oldColName2 : newColName2,
            }
df = df.rename(columns=colsList)

# convert column to datetime
dateFormat = '%m/%d/%Y %I:%M:%S %p'
df['colname'] = pd.to_datetime(df['colname'], format=dateFormat)

# get min and max values
df.colname.min()
df.colname.max()

# show data types of dataframe
df.dtypes

# use Grouper to group dataframe rows by time frequency (ie. monthly)
df_grouped = df.groupby(pd.Grouper(key='datetimeColName', freq='M'), sort=False)

# Delete column in dataframe
df = df.drop('colName', axis=1)

# join dataframes
dflist = [df1, df2, df3]
result = pd.concat(dflist)

```

### Apply lambda functions
Note: You can pass the cell or the entire dataframe as a parameter for the lambda function.
```python 
# pass cell in dataframe as parameter
def somefunc(a):
  pass

# pass entire dataframe as parameter
def calcScore(df):
  if pd.isnull(df['colName']):
    return ""
  else:
    ... do some calculations..
    # set value of the dataframe cell
    return value

def main():
  ... some code...
  df['colName'] = df['colName'].apply(lambda x: somefunc(x))
  df['colName'] = df['colName'].apply(lambda x: x.capitalize())
```

### Split one column into 2 columns of the dataframe
```python
def splitName(a):
  return a.split(' ')
  
def main():
  ... some code...
  df['car_brand'], df['car_model'] = zip(*df['car_fullname'].apply(lambda x: splitName(x)))
```


### NOT operator (~)
```python
bigSet = pdf.read_csv(fileName)['colName']
smallSet = df2['colName']
result = ~smallSet.isin(bigSet)
```

### Merge dataframes 
Like a join in SQL relational databases
```python 

```
