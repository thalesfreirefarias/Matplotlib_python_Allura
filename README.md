# Python_Basic
Basic commands to use in Python


# DailyStudy

![GitHub repo size](https://img.shields.io/github/repo-size/iuricode/README-template?style=for-the-badge)
![GitHub language count](https://img.shields.io/github/languages/count/iuricode/README-template?style=for-the-badge)
![GitHub forks](https://img.shields.io/github/forks/iuricode/README-template?style=for-the-badge)
![Bitbucket open issues](https://img.shields.io/bitbucket/issues/iuricode/README-template?style=for-the-badge)
![Bitbucket open pull requests](https://img.shields.io/bitbucket/pr-raw/iuricode/README-template?style=for-the-badge)

### Day 1: Data loading:
- Read CSV FILE
  ```
  df=pd.read_csv('.csv')
  ```
-Read excel File
```
df= pd.read_excel('file.xlsx')
```
- Read SQL file
```
df=pd.read_sql('query_connection')
###In the SQL query file, you should include what you're looking for, such as a filter, e.g., SELECT * FROM my_table WHERE condition. For the connection, you should use the SQL connection, like this:
###connection = sqlite3.connect('my_database.db')
```

### Day 2 Data inspection
### Top Rows (Display)
```
df.head()
```
### Bottom Rows(Display)
```
df.tail()
```
### Data Types
```
df.dtypes
```

```
###Summary Statistic
including:
mean, standard deviation, minimum, maximum, and percentiles for numerical columns.
df.Describe()
```

```
df.info()
### Display Index, Columns, Data
general overview of the DataFrame, including:
Total number of entries (rows)
Column names
Number of non-null values in each column
Data types of each column
Memory usage
```

### Day 3 Data Cleaning

### Check for missing values
```
df.isnull().sum()
```
### fill Missing values
```
df = df.fillna(value)
print(df)
```
### Drop Missing Values
```
df.dropna()
```
### Rename Columns
```
df.rename(columns ={'old_name': 'new_name'})
```
### Drop Column
```
df.drop(columns=['columns_name'])
```

### Day 4 Data Transformation

```
### Applies a function to each value in the "column"
df['column'].apply(lambda:function(x))
df['valor total']=df['Valor'].apply(lambda x: x*2)
df
```

```
### Groupby and Aggegate
df.groupby('Categoria').agg({'Valor': 'sum'})

```

```
###Pivot tables- > Calculates the mean of columns2 for each unique value in columns1.

df.pivot_table(index='Categoria', values='Valor', aggfunc='mean')
```

```
### Merge Dataframes -> Function combines two DataFrames (df1 and df2) based on a common column.
pd.merge(df1,df2, on = 'column')

df1 = pd.DataFrame({'column': [1, 2, 3], 'values1': ['A', 'B', 'C']})
df2 = pd.DataFrame({'column': [2, 3, 4], 'values2': ['X', 'Y', 'Z']})

result = pd.merge(df1, df2, on='column')

## excludes 1 and 4 because don't have a common column
```

```
###Concateate Dataframes
pd.concat([df1,df2])

result = pd.merge(df1, df2, on='customer_id', how='left')
how-> inner( just with values), outer(fill when NaN,right
```

### Day 5 Data Transformation

```
###Histogram
df['column'].hist()
or
import matplotlib.pyplot as plt

df['Valor'].hist(bins=20, edgecolor='black')
plt.xlabel('Valores')
plt.ylabel('Quantidade')
plt.title('Histograma de valores')
plt.show()
```

```
###boxplot
df.boxplot(column=['column1', 'column2'])
df.boxplot(column=['Valor', 'valor total'])
```

```
###Scatter plot
df.plot.scatter(x='col1', y='col2')
df.plot.scatter(x='Valor',y='valor total')
```

```
###Line plot
df.plot.line(x='Data', y='Valor')


import pandas as pd
import matplotlib.pyplot as plt

# Criando o DataFrame
df = pd.DataFrame(dados)

# Criando o gráfico de linha
df.plot.line(x='Data', y='Valor')

# Adicionando título e rótulos
plt.title('Gráfico de Linhas Data x valores')

plt.xlabel('Datas')
plt.ylabel('Valores')
# Exibindo o gráfico
plt.show()



```

```
###Bar chart
df['column'].value.counts().plot.bar()
df['column'].value_counts().plot(kind='bar', color='skyblue', edgecolor='black')


import pandas as pd
import matplotlib.pyplot as plt

plt.figure(figsize=(10, 6)) 

df['Categoria'].value_counts().plot.bar()

plt.title('Distribuição de Valores Totais')
plt.xlabel('Categoria')
plt.ylabel('Quantidade')

plt.xticks(fontsize=9, rotation=45)  

plt.show()


```

### Day 6 Statistical Analysis
```
###correlation Matrix
df.corr()
```

```
###covariance matrix
df.cov()
```

```
###Value counts
df['column'}.value_counts()
```

```
df['column'].unique()
```

```
df['column'].nunique()
```

### Day 7 Indexing and Selection
```
### Select Column
DF['column']
```

```
###Select Multiple Columns
DF.[['col1','col2']]
```

```
###Select Rows by position
DF.ILOC[0:5]
```
```
###Select Rows by lobel
DF.LOC[0:5]
```
```
#Condition Selection
DF[DF['column']>value]
```

### Day 8 Data Formatting and Conversion
```
###Convert Dataypes
df[`column`].astype[`type`]
```

```
###String Operations
df[`column`].str.lower()
```
```
###datetime conversion
pf.to_datatime(df.[`column`])
```
```
###setting Index
df.set_index(`column`)
```

### Day 9 Advanced Data Transformation
```
### Lmabda Functions
df.apply(lambda x:x+1
```
```
### Pivot longer/under Format
df.metlt(id_vars=['col1']
```
```
###Sstack/unstack
df.stack()
df.unstack()
```
```
### cross tabulations
pd.crosstab(df['col1'],df['col2'])
```
### Day  10 handling time series data

```
###SET DATETIME INDEX... Transform one column to datetime
df.set_index(pd.to_datetime(df['date']))
df = df.set_index(pd.to_datetime(df['date']))
```

```
###Resampling Data
df.resamble('ME').mean()
mes = df.resample('ME').mean(numeric_only=True)
print(mes)
```
```
###Rolling window Operation.. calcule the mean of the values
df.rolling(window=5).mean()
df_numeric = df.select_dtypes(include=['float64', 'int64'])
mes = df_numeric.rolling(window=5).mean()
print(mes)
```


### Day 11  File export

```
###write to CSV
df.to_CSV('filename.csv')

###If you want to download instead
from google.colab import files
df.to_csv('filename.csv', index=False)
files.download('filename.csv')
```


```
###write to Excel
df.to_excel('filename.xls')
```


```
###write to Database
df.to_sql('table_name',connection)
```

### Day 12  Data exploration techniques
```
!pip install ydata-profiling
###profile report with pandas profiling
from pandas_profiling import ProfileReport

profile = ProfileReport(df, title="Pandas Profiling Report", explorative=True)
profile.to_notebook_iframe()
```
```
###pairplot with seaborn
import seaborn as sns
import matplotlib.pyplot as plt

# Filter just numbers
numeric_df = df.select_dtypes(include='number')

# Create heatmap
sns.heatmap(numeric_df.corr(), annot=True, cmap='coolwarm')
plt.show()


```

```
###heatmap for correlation with seaborn
# Using just numbers
numeric_df = df.select_dtypes(include='number')
sns.pairplot(numeric_df)

```

### Day 13  Data exploration techniques
```
###query function
df.qyery('column>value')
value = 90  # Define the variable first
df.query('Valor > @value')  # Use @ to reference Python variables inside query

```

```
###Filtering with isin
df[df['column1'].isin([value1,value2)]]
df[df['Categoria'].isin(['A', 'C'])]
```

### Adjustments and improvements.

The project is still under development, and the upcoming updates will focus on the following tasks:

- [x] Advanced courses about Phyton

The following tools were used in the construction of the project:

- [Python](<https://www.python.org/doc//>)



## 🤝 Creator

<table>
  <tr>
    <td align="center">
      <a href="#" title="Thales Farias">
        <img src="grecia.jpg" width="100" alt="Foto do Thales Farias no GitHub"/><br>
        <sub>
          <b><a href="https://www.linkedin.com/in/thalesfreirefarias/" target="_blank">Thales Farias</b>
        </sub>
      </a>
    </td>
  </tr>
</table>
