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

# rename column
df = df.rename(columns={oldColName : newColName})

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
```

### Apply lambda functions
```python 
def somefunc(a):
  pass

def main():
  ... some code...
  df['colName'] = df['colName'].apply(lambdax x: somefunc(x))
```

### Split one column into 2 columns of the dataframe
```python
def splitName(a):
  return a.split(' ')
  
def main():
  ... some code...
  df['car_brand'], df['car_model'] = zip(*df['car_fullname'].apply(lambda x: splitName(x)))
```

### Join Dataframes
```python
dflist = [df1, df2, df3]
result = pd.concat(dflist)
```

