# Pandas

## Link

- [Official documentation](https://pandas.pydata.org/docs/index.html)

## Import data

- **pd.read\_csv([FILENAME])**
- **pd.read\_json([FILENAME])**
- **pd.read\_excel([FILENAME])**

## Explore data

- DataFrame.head(n): first n rows of the dataframe
- DataFrame.tail(n): last n rows of the dataframe
- DataFrame.shape
- DataFrame.dtypes: types of all variables (columns)
- DataFrame.values: numpy.Array of the values

## Accessors

- DataFrame["columnName"] -> Series
- DataFrame[["columnName1", "columnName2"]] -> DataFrame
- DataFrame.iloc[indexLine, indexColumn] -> value
- DataFrame.iloc[:10, 2]
- DataFrame.iloc[:10, :]
- DataFrame.iloc[:10, [1, 3]]

### Filtering

- DataFrame.loc[condition on lines, codition on columns]
- prets.loc[(prets['revenue'] > 4000) & (prets['taux'] < 10, :]
- prets.loc[(prets['revenue'] > 4000) & (prets['taux'] < 10, 'identifier']

### indexes

- iloc accesses to lines using the actual order of lines in the DF. **sort_values** can for example change this order.
- loc accesses to lines using their indexthat can be non numerical.

- DataFrame.reset_index(): reset index but save old values in a new column names "index" by default.
- DataFrame.reset_index(drop=True): drops old indexes

## Modifiers

- DataFrame["columnName"] = value : All the column will be replaced with this value and the type too
- DataFrame["columnName"] = Array : You can also replace a column with a Series or an Array of the same size. If the size don"t match an error is raised.
- DataFrame[mask, "columnName"] = value
- prets[mask, "taux"] = prets[mask, "taux"] + 0.05


### Delete a column

- DataFrame.drop(columns="columnName") -> DataFrame copy without the column (Doesn't affect the original DataFrame)
- del DataFrame["columnName"] -> void
- DataFrame.pop("columnName") -> Series

### Rename a column

- DataFrame.rename(columns= {"oldColumnName": "newColumnName"}) -> DataFrame (The original DataFrame isn't modified unless the inplace=True argument is used)

### Change column type

- DataFrame["columnName"].astype(float): Doesn't it change in place or return a series?


### Sort a DataFrame

- DataFrame.sort_values("columnName")
- DataFrame.sort_values("columnName", ascending=False)
- DataFrame.sort_values(["columnName1", "columnName2"])
- DataFrame.sort_values(["columnName1", "columnName2"], ascending=[True, False])

## Aggregation

```python
prets.groupby('ville').sum()
prets.groupby(['ville', 'type']).sum()
prets.groupby(['ville', 'type'])['remboursement'].sum()
prets.groupby('ville').agg({'remboursement': ['sum', 'mean'], 'revenu': 'max'})
```

### Pivot tables

```python
prets.pivot_table(
	index = 'ville',
	columns = 'type',
	values = 'remboursement',
	aggfunc = 'sum'
)
```

The reverse process is don with **melt**

```python
data.melt(
	id_vars='ville',
	value_vars=['automobile', 'immobilier']
)
```

## Merging DataFrames

- pd.merge(A, B)
- A.merge(B)

by default it's a natural join (pandas will check the common columns between A and B and use them as keys).

### Choose merging keys

- pd.merge(A, B, on='id'): when the name of the column is the same in both dataframes.
- pd.merge(A, B, right_on='idInB', left_on='idInA')

### Types of joins

#### inner join

keys are in both dataframes

pd.merge(A, B, on='id', how='inner')

#### left join

Use all (and only) keys from the first dataframe. If there is no correspondance in the second dataframe a default value value is used.

pd.merge(A, B, on='id', how='left')

#### right join

Use all (and only) keys from the second dataframe. If there is no correspondance in the first dataframe a default value value is used.

pd.merge(A, B, on='id', how='right')

#### outer join

Use all keys from both the first and the second dataframe. If there is no correspondance in the other dataframe a default value value is used.

pd.merge(A, B, on='id', how='outer')

## Concatenate dataframes

The dataframes needs to have the sames structure (key types and columns).

- pd.concat([df1, df2])
- pd.concat([df1, df2], ignore\_index=True): Concat doesn't care for the index and we might endup with doubles. This toggle is equivalent to applying **reset\_index()**.
