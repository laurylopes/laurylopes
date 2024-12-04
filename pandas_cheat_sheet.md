
# Pandas Cheat Sheet
<img width="527" alt="image" src="https://github.com/user-attachments/assets/a6f18a27-6575-462c-b9c1-6eaf0b495565">


``` python
# f print python
print(f' My name is : {name} and I am {age} years old')
```

``` python
# open all columns in df
pd.set_option('max_columns', None)
```

### String manipulation 
``` python
# contains 
df['ColumnName'].str.contains('containString')

# replace
df['ColumnName'].str.replace('old', 'new')

# start with
df['ColumnName'].str.startswith('A')
```

### Anti-join
``` python
merge = pd.merge(df_1, df_2, on ='key', how='inner')
array = merge['column'].unique() # keep values of interest to filter
df[~df['ColumName'].isin(array)]
```

### Columns manipulation
``` python
# drop columns
df.drop(['ColumnName1', 'ColumnName2'])

# rename columns
df.rename(columns={'OldName' : 'NewName'})

# keep only selected columns
df = df[['col1', 'col2']]
```

### Concatenation
``` python
# concat several df 
pd.concat([df1, df2, df3], ignore_index=True)

# concat excel sheets in file
df = pd.concat(pd.read_excel('excelNameFile.xlsx', sheet_name=None), ignore_index=True)

# concat all files in a folder
import os
import pandas as pd

# 1. list data in a folder called data
os.listdir('Data') 

# 2. create a list of files
files_list = os.listdir('Data')

# 3. create a df for each file in list 
df_files = [pd.read_csv(os.path.join('Data', file), on_bad_lines ='skip', skiprows = 3, sep = '\t', parse_dates=False) for file in files_list]

# 4. concat all df_files into df
df = pd.concat(df_files, ignore_index =False)
```

### Date Time Format
``` python
# transform data into dateTime value type
pd.to_datetime(df['DateColumnName'])

# extract year, month and day and create new column with data
df['year'] = df['DateColumnName'].dt.year
df['month'] = df['DateColumnName'].dt.month
df['day'] = df['DateColumnName'].dt.day

# debug erros
pd.to_datetime(df['column'], errors='coerce')
```

### Duplicates
``` python
# drop duplicates
df.drop_duplicates(subset = 'ColumnName')
```

### Group By
``` python
# group by with more than one aggregate

# 1. create disctionnary with 'columnName' : 'function'
dico_agg = {'columnName1': ['agg1'], 'ColumeName2': ['agg2'], 'ColumName3' : ['agg3']}

# 2. run group by and aggregate
df.groupby('ColumnName').agg(dico_agg)
```

### Order By
``` python
# sort values by column
sort_values(by=['Col'], ascending=False)
```

### Selection
``` python
# iloc selection
df.iloc[:,:8] # first row , second columns # :all before 8 index starts at 0
```
