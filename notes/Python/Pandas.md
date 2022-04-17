<h1>Pandas</h1>
- is a module in python used to edit and create data
- can be used to make .CSV files
- uses dataframes



### Creating a DataFrame: reading data from a file
- Often you want to use the data from a file that is stored on your computer. pandas has functions that allow you to do it.

- One of the most popular text formats is .csv, which stands for comma-separated values. This format can store tabular data; each row in a file represents a row in a table, and values corresponding to different columns are separated by commas.

```python
df = pd.read_csv("textfile.txt" , sep = '')

```

<h2>functions</h2>
- ### .iloc(number, number)
	- Integer locator
	- `iloc[<row selection>, <optional column section]`

- ### .loc(rows, col)
	- Label based, `loc[<row selection>, <optional column section]`
	- `.loc` can take:
		-   a single row label
		-   a list of row labels
		-   a slice of row labels
		-   a result of conditional statements (a boolean array)
		-   we could also pass columns as the second argument in a similar manner: a single label, a list, or a slice.
	 - ![[Pasted image 20220411184426.png]]

	``` python
	# If we pass a single argument, Pandas will return a series:
	df.loc['third']  
	```
	- 	![[Pasted image 20220411184217.png]]

	 ``` python
	 df.loc['third', 'last_name']

	 # output: `Doe`
	 ```
	 - we can get multiple indexes
	 ```python
	 df.loc[['first','fourth'], ['last_name', 'birthday']]
```
	-  	 ![[Pasted image 20220411190007.png]]
	- we can get 1st and 4th row and the `last_name` and `birthday`

	- We can also get a slice of rows
	```python
	df.loc['second':'fourth']
```

	-	![[Pasted image 20220411190137.png]]

	- we can also assign a condition to the query
	```python
	df.loc[df.birthday == '12.05.1979', 'last_name':'birthday':2]
```
	- ![[Pasted image 20220411190431.png]]



### Working with missing values
- A missing value is **the absence of data**.
- `NaN`s do not necessarily stand for missing numbers, but for missing strings, dates, or any other data types as well.
- 1) `pandas.DataFrame.isnull()` to mark which value is `NaN` and which is not
- It returns `True` if the value is missing, and `False` otherwise:
- ![[Pasted image 20220411193949.png]]
- 2) A combination of methods to calculate a proportion of `NaN`s per feature:
```python
data.isnull().sum() / data.shape[0]
```
- ![[Pasted image 20220411194224.png]]
- `.isnull` calculates which values are null/`NaN` and `sum()` calculates how many true values per feature there are. then divide by `/ data.shape[0]` divides the number of missing values per feature by the number of rows. Finally, we get a proportion of missing values per column. 
- ![[Pasted image 20220411194500.png]]
- .3 school means that 30% of the data is missing
- `data.isnull().any()`
	- checks if there are any missing values
- ##### How to deal with them?
	- We can drop all the rows which contain missing values with `pandas.DataFrame.dropna(axis=0)`
	- we can also drop COLUMNS with `data.dropna(axis=1)`
	- In order for the changes to be saved in the original DataFrame set the `inplace=True` parameter.
	- drop rows that consist of more than half of missing values and fill remaining NaNs with certain values


### Modifying a dataframe
- In Pandas, it's possible to create new columns on the fly. Just address the DataFrame with a new column name and pass the values:
-  `df['mood'] = ['sleepy', 'happy', 'thinking', 'excited']`
- ![[Pasted image 20220411223740.png]]
- You can also derive a new column based on the existing one. Suppose, you want to create the `pairs_of_legs` column based on the `legs` column. You take and divide it by 2:
-  `df['pairs_of_legs'] = df.legs/2`
- ![[Pasted image 20220411223921.png]]

- As a result, we have a float-type column. It's possible to use other types of mathematical operations. We can also use string operations, like concatenation. Let's create a new column called `description` from `mood` and `species`:
- `df['description'] = df.mood + ' ' + df.species`
- ![[Pasted image 20220411224034.png]]
- If you need to add a row, use the `DataFrame.append()` method. The first parameter adds the information to your DataFrame, it could be a dictionary, a series, or a whole DataFrame. The second parameter is `ignore_index`. It is `False` by default. If we set it as `True`, the DataFrame will be reindexed from 0 up to the new row. `.append()` doesn't change the data, it returns the new DataFrame with the row, added to the end. If you want to add a row from a dictionary, set `ignore_index=True`, otherwise, it'll cause an error. Fine, let's do it:
```python
new_row = {'pet_name': 'Turtle',   
            'species': 'turtle',  
            'legs': 4,  
            'wings': 0,  
            'homeless': 'no',  
            'mood': 'skeptical',  
            'pairs_of_legs': 2,  
            'description': 'skeptical turtle'}  
df = df.append(new_row, ignore_index=True)  
df.head()
```
- ![[Pasted image 20220411224512.png]]

#### Deleting columns and rows
- We can delete a whole DataFrame with a single method — `DataFrame.drop()`. Since we have the `description` column, we don't need `species` and `mood` any more, so let's get rid of them! We can call `.drop` and pass these labels to the `columns` argument. This method also returns a DataFrame by default, but we can also set `inplace` to `True` for the changes to take place:
```python
df.drop(columns=['species', 'mood'], inplace=True)  
df.head()
```
- ![[Pasted image 20220411225112.png]]
- If you want to delete rows, follow the same rules but use the `index` argument:
```python
df.drop(index=4, inplace=True)
# or
df.drop(['column_name'], axis = 1, inplace=True)
```
- ![[Pasted image 20220411225253.png]]
- There are a few things to mention — we passed an integer row label (as we have an ordinal integer index). The DataFrame index now is not sequentially numbered. It doesn't contain `3`, and if we want to fix that, we have to use `.reset_index(drop=True, inplace=True)`. The most popular way to delete rows is to filter DataFrame against a condition and put the selection (skip the rows you don't need) to `df` or any other DataFrame variable. We will master the art of selection in the topics to come.

#### Handling missing values
- ####### Stating a problem:
	- Why can't we always delete `NaN`s (= missing values) and forget about them? Let's look at [the dataset](https://stepik.org/media/attachments/lesson/571584/flatstoydata.csv) below.
	```python
	    district  totsp  balconysp  dist2subway  price  security  
0   Python-beach   77.0        5.8          NaN  142.0       NaN  
1      East Java  100.0        8.6          0.9    NaN       NaN  
2      East Java   64.0        NaN          0.7  120.0       0.0  
3      East Java    NaN        4.1          0.7  110.0       1.0  
4   Python-beach   75.0        NaN          1.6  143.0       NaN  
5   Python-beach   60.0        4.2          NaN  155.0       NaN  
6      East Java   71.0        NaN          0.3  170.0       NaN  
7    Kotlin-side   75.0        4.1          0.8  122.0       1.0  
8            NaN   76.0        5.1          1.2  131.0       NaN  
9    Kotlin-side  134.0        8.8          NaN  730.0       NaN  
10   Kotlin-side   58.0        NaN          2.8  108.0       NaN  
11     East Java   79.0        6.1          NaN  130.0       1.0  
12  Python-beach   79.0        NaN          1.1  118.0       NaN  
13  Python-beach   80.0        5.8          NaN  160.0       NaN  
14   Kotlin-side   63.0        3.4          NaN   95.0       NaN  
15  Python-beach   85.0        4.8          1.3    NaN       NaN
```
- We apply delete-all-rows-with-NaNs method:
- `data.dropna()`
```python
      district  totsp  balconysp  dist2subway  price  security  
7  Kotlin-side   75.0        4.1          0.8  122.0       1.0
```
- That happened because each row in our toy dataset contains a missing value. In reality, even a good dataset can contain 80% of rows with `NaN`s in different columns. `dropna()` would delete 80% of the data. This method isn't suitable for us because together with missing values we would lose a lot of valuable information.
- However, it makes sense to drop `security` column, which consists almost entirely of missing values.
- `data.dropna(axis=1, thresh=10, inplace=True)`
- Recall the parameters: `axis=1` deletes columns instead of rows, `thresh=10` requires that a column has at least 10 non-`NaN`s to survive, and `inplace=True` saves the changes in the original DataFrame.
- Result:
	```
	        district  totsp  balconysp  dist2subway  price  
	0   Python-beach   77.0        5.8          NaN  142.0  
	1      East Java  100.0        8.6          0.9    NaN  
	2      East Java   64.0        NaN          0.7  120.0  
	3      East Java    NaN        4.1          0.7  110.0  
	4   Python-beach   75.0        NaN          1.6  143.0  
	5   Python-beach   60.0        4.2          NaN  155.0  
	6      East Java   71.0        NaN          0.3  170.0  
	7    Kotlin-side   75.0        4.1          0.8  122.0  
	8            NaN   76.0        5.1          1.2  131.0  
	9    Kotlin-side  134.0        8.8          NaN  730.0  
	10   Kotlin-side   58.0        NaN          2.8  108.0  
	11     East Java   79.0        6.1          NaN  130.0  
	12  Python-beach   79.0        NaN          1.1  118.0  
	13  Python-beach   80.0        5.8          NaN  160.0  
	14   Kotlin-side   63.0        3.4          NaN   95.0  
	15  Python-beach   85.0        4.8          1.3    NaN
	```

#### Guessing missing data
- In this section, we will get rid of `NaN`s without deleting any of them. There are different methods to handle missing values in categorical and numerical features. For all cases, we will use `pandas.Series.fillna()`, which basically takes a value and fills all the holes in a column.
- To move further we need to know the data context. The dataset above contains information about flats in Hyperskill city:
- `district` is district  
- `totsp` is the total area of an apartment (m2)  
- `balconysp` is an area of a balcony in the apartment (m2)  
- `dist2subway` is a distance to the nearest subway station (km)  
- `price` is a flat's cost in thousands of dollars

- 1.) Fill `NaN`s with **the most frequent value** (**the mode** in the language of statistics) for categorical features

```python
mode_district = data['district'].mode()[0] # calculate the mode  
data['district'].fillna(mode_district, inplace=True) # replace NaNs with that mode
```

- 2) For numerical features use **a column average**
```python
mean_totsp = data["totsp"].mean() # calculate the average  
data["totsp"].fillna(mean_totsp, inplace=True) # replace NaNs with that average
```

- We left `dist2subway`, which is a distance to the nearest subway station. Let's be more elegant here. The knowledge of the district of a flat helps to guess the distance more accurately than the average for all data. Let's fill missing values with the average for the district, where the given flat is located.
```python
data["dist2subway"] = data.groupby("district")["dist2subway"].apply(lambda x: x.fillna(x.mean()))
```
- Looks complicated but let's take it step by step. Firstly, `data.groupby("district")` groups samples by their districts. Secondly, we take `dist2subway` column to processing. Then, we use `apply()` method to apply a function inside, which is `lambda x: ...`, group-wise. The function takes a set of samples, which belong to the same district, calculates the average distance, and fills missing values in the group with that average.

- 3) Fill missing values with **a median value** for numerical features  
We usually choose this way when a feature has outliers. They affect an average, so it no longer represents a typical value of this feature. Fortunately, outliers don't bother median value.

```python
median_price = data["price"].median() # calculate the median value  
data["price"].fillna(median_price, inplace=True) # replace NaNs with that value
```

- 4) Replace all `NaN`s with **some** **value**  
We try to guess a value, which is meaningful. Sometimes it's not possible. In our toy dataset, we suppose that `NaN` in `balconysp` means that there is no balcony in a flat, so its area equals zero. We replace missing values with `0` and it makes some sense.

When we can't find a meaningful value, we fill `NaN`s with `-1` to differentiate these observations as a separate group based on the absence of a value in some feature. Note that the method works for both categorical and numerical features.

Finally, we got the data without missing values:

```python
        district  totsp  balconysp  dist2subway  price  
0   Python-beach   77.0        5.8         1.30  142.0  
1      East Java  100.0        8.6         0.90  130.5  
2      East Java   64.0        0.0         0.70  120.0  
3      East Java   78.4        4.1         0.70  110.0  
4   Python-beach   75.0        0.0         1.60  143.0  
5   Python-beach   60.0        4.2         1.30  155.0  
6      East Java   71.0        0.0         0.30  170.0  
7    Kotlin-side   75.0        4.1         0.80  122.0  
8   Python-beach   76.0        5.1         1.20  131.0  
9    Kotlin-side  134.0        8.8         1.80  730.0  
10   Kotlin-side   58.0        0.0         2.80  108.0  
11     East Java   79.0        6.1         0.65  130.0  
12  Python-beach   79.0        0.0         1.10  118.0  
13  Python-beach   80.0        5.8         1.30  160.0  
14   Kotlin-side   63.0        3.4         1.80   95.0  
15  Python-beach   85.0        4.8         1.30  130.5

```

![[Pasted image 20220412003849.png]]
- Median : Deals with outliers
- Average : if there are no outliers
- mode : most frequent value



#### Summarizing categorical columns
- Pandas is famous for its analytical tools. When we need to compare datasets or evaluate the data that is grouped by categories, we need to refer to the summary statistics. Entry-by-entry data comparison is impractical. Moreover, an analyst should describe the myriad of small data discrepancies in more general terms. Let's take a look at the most basic possible discrepancies – quantity discrepancies.

##### Counting
- AFTER importing your dataset, we need to count the following values:
		1.  non-null values,
		2. Missing Values
		3.  all values, including the missing values,
		4.  the number of unique values.
- non-null values:
	`df.columnName.count()`
- Nulls:
	`df.columnName.isna()`
	- for the total of null values:
		`df.columnName.isna().sum()`
- all Values:
	`df.shape[0]`
- Unique Values:
	`df.columnName.value_counts()`
	`df.columnName.nunique()`


##### Series.value_counts & Series.unique
- value_counts
	 `df.columnName.value_counts()`
	 - counts the different types of data in a series
	 - ![[Pasted image 20220414161356.png]]
- unique
	`df.columnName.unique()`
	- prints the different values of data that appears within the series
	- ![[Pasted image 20220414161408.png]]
- 