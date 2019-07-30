---
redirect_from:
  - "/chapters/06/dataframes"
interact_link: content/chapters/06/DataFrames.ipynb
kernel_name: python3
has_widgets: false
title: 'DataFrames'
prev_page:
  url: /chapters/05/3/More_on_Arrays
  title: 'More on Arrays'
next_page:
  url: /chapters/06/1/Sorting_Rows
  title: 'Sorting Rows'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---




# DataFrames

DataFrames are a fundamental object type for representing data sets. A DataFrame can be viewed in two ways:

* a sequence of named columns that each describe a single aspect of all entries in a data set, or
* a sequence of rows that each contain all information about a single entry in a data set.

In order to use DataFrames, import the module called `pandas`, from a Python library commonly used in data science.

Though you may simply `import pandas`, it is common to rename the module for quick reference within our code.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
import pandas as pd
```
</div>

</div>



The pandas `DataFrame` may be constructed in a number of ways, depending on its data source.

Underlying each column of a `DataFrame` is a pandas `Series`.

A straight-forward manner of constructing a `DataFrame` is to specify its data as a Python `dict`, whose keys are column labels and whose values are `list`s or NumPy `array`s.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
pd.DataFrame(
    {
        'Number of petals': [8, 34, 5],
    },
)
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">



<div markdown="0" class="output output_html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Number of petals</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>8</td>
    </tr>
    <tr>
      <th>1</th>
      <td>34</td>
    </tr>
    <tr>
      <th>2</th>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



To specify two (or more) columns, provide the label and values for each column. All columns must have the same length, or an error will occur.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
pd.DataFrame(
    {
        'Name': ['lotus', 'sunflower', 'rose'],
        'Number of petals': [8, 34, 5],
    },
)
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">



<div markdown="0" class="output output_html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Number of petals</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>lotus</td>
      <td>8</td>
    </tr>
    <tr>
      <th>1</th>
      <td>sunflower</td>
      <td>34</td>
    </tr>
    <tr>
      <th>2</th>
      <td>rose</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



We can give this DataFrame a name, and then extend it with another column, using DataFrame method, `assign`.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
flowers = pd.DataFrame(
    {
        'Name': ['lotus', 'sunflower', 'rose'],
        'Number of petals': [8, 34, 5],
    },
)

flowers.assign(
    Color=['pink', 'yellow', 'red'],
)
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">



<div markdown="0" class="output output_html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Number of petals</th>
      <th>Color</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>lotus</td>
      <td>8</td>
      <td>pink</td>
    </tr>
    <tr>
      <th>1</th>
      <td>sunflower</td>
      <td>34</td>
      <td>yellow</td>
    </tr>
    <tr>
      <th>2</th>
      <td>rose</td>
      <td>5</td>
      <td>red</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



The `assign` method creates a new DataFrame each time it is called, so the original DataFrame is not affected. For example, the DataFrame `flowers` still has only the two columns that it had when it was created.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
flowers
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">



<div markdown="0" class="output output_html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Number of petals</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>lotus</td>
      <td>8</td>
    </tr>
    <tr>
      <th>1</th>
      <td>sunflower</td>
      <td>34</td>
    </tr>
    <tr>
      <th>2</th>
      <td>rose</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



Creating DataFrames in this way involves a lot of typing. If the data have already been entered somewhere, it is usually possible to use Python to read it into a DataFrame, instead of typing it all in cell by cell.

Often, DataFrames are created from files that contain comma-separated values. Such files are called CSV files.

Below, we use the pandas function `read_csv` to read a CSV file that contains some of the data used by Minard in his graphic about Napoleon's Russian campaign. The data are placed in a DataFrame named `minard`.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
minard = pd.read_csv(PATH_DATA / 'minard.csv')

minard
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">



<div markdown="0" class="output output_html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Longitude</th>
      <th>Latitude</th>
      <th>City</th>
      <th>Direction</th>
      <th>Survivors</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>32.0</td>
      <td>54.8</td>
      <td>Smolensk</td>
      <td>Advance</td>
      <td>145000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>33.2</td>
      <td>54.9</td>
      <td>Dorogobouge</td>
      <td>Advance</td>
      <td>140000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>34.4</td>
      <td>55.5</td>
      <td>Chjat</td>
      <td>Advance</td>
      <td>127100</td>
    </tr>
    <tr>
      <th>3</th>
      <td>37.6</td>
      <td>55.8</td>
      <td>Moscou</td>
      <td>Advance</td>
      <td>100000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>34.3</td>
      <td>55.2</td>
      <td>Wixma</td>
      <td>Retreat</td>
      <td>55000</td>
    </tr>
    <tr>
      <th>5</th>
      <td>32.0</td>
      <td>54.6</td>
      <td>Smolensk</td>
      <td>Retreat</td>
      <td>24000</td>
    </tr>
    <tr>
      <th>6</th>
      <td>30.4</td>
      <td>54.4</td>
      <td>Orscha</td>
      <td>Retreat</td>
      <td>20000</td>
    </tr>
    <tr>
      <th>7</th>
      <td>26.8</td>
      <td>54.3</td>
      <td>Moiodexno</td>
      <td>Retreat</td>
      <td>12000</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



We will use this small data set to demonstrate some useful DataFrame methods. We will then use those same methods, and develop other methods, on much larger tables of data.



### The Shape of the Data

The `shape` of a DataFrame is its number of rows and columns.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
minard.shape
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
(8, 5)
```


</div>
</div>
</div>



The number of rows can therefore be retrieved from the sequence returned by the `shape` property.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
minard.shape[0]
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
8
```


</div>
</div>
</div>



…or the number of columns:



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
minard.shape[1]
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
5
```


</div>
</div>
</div>



### Column Labels
The property `columns` can be used to list the labels of all the columns. With `minard` we don't gain much by this, but it can be very useful for tables that are so large that not all columns are visible on the screen.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
minard.columns.to_list()
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
['Longitude', 'Latitude', 'City', 'Direction', 'Survivors']
```


</div>
</div>
</div>



We can change column labels using the `rename` method. This creates a new DataFrame and leaves `minard` unchanged.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
minard.rename(
    columns={
        'City': 'City Name',
    },
)
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">



<div markdown="0" class="output output_html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Longitude</th>
      <th>Latitude</th>
      <th>City Name</th>
      <th>Direction</th>
      <th>Survivors</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>32.0</td>
      <td>54.8</td>
      <td>Smolensk</td>
      <td>Advance</td>
      <td>145000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>33.2</td>
      <td>54.9</td>
      <td>Dorogobouge</td>
      <td>Advance</td>
      <td>140000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>34.4</td>
      <td>55.5</td>
      <td>Chjat</td>
      <td>Advance</td>
      <td>127100</td>
    </tr>
    <tr>
      <th>3</th>
      <td>37.6</td>
      <td>55.8</td>
      <td>Moscou</td>
      <td>Advance</td>
      <td>100000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>34.3</td>
      <td>55.2</td>
      <td>Wixma</td>
      <td>Retreat</td>
      <td>55000</td>
    </tr>
    <tr>
      <th>5</th>
      <td>32.0</td>
      <td>54.6</td>
      <td>Smolensk</td>
      <td>Retreat</td>
      <td>24000</td>
    </tr>
    <tr>
      <th>6</th>
      <td>30.4</td>
      <td>54.4</td>
      <td>Orscha</td>
      <td>Retreat</td>
      <td>20000</td>
    </tr>
    <tr>
      <th>7</th>
      <td>26.8</td>
      <td>54.3</td>
      <td>Moiodexno</td>
      <td>Retreat</td>
      <td>12000</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



However, this method does not change the original table. 



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
minard
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">



<div markdown="0" class="output output_html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Longitude</th>
      <th>Latitude</th>
      <th>City</th>
      <th>Direction</th>
      <th>Survivors</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>32.0</td>
      <td>54.8</td>
      <td>Smolensk</td>
      <td>Advance</td>
      <td>145000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>33.2</td>
      <td>54.9</td>
      <td>Dorogobouge</td>
      <td>Advance</td>
      <td>140000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>34.4</td>
      <td>55.5</td>
      <td>Chjat</td>
      <td>Advance</td>
      <td>127100</td>
    </tr>
    <tr>
      <th>3</th>
      <td>37.6</td>
      <td>55.8</td>
      <td>Moscou</td>
      <td>Advance</td>
      <td>100000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>34.3</td>
      <td>55.2</td>
      <td>Wixma</td>
      <td>Retreat</td>
      <td>55000</td>
    </tr>
    <tr>
      <th>5</th>
      <td>32.0</td>
      <td>54.6</td>
      <td>Smolensk</td>
      <td>Retreat</td>
      <td>24000</td>
    </tr>
    <tr>
      <th>6</th>
      <td>30.4</td>
      <td>54.4</td>
      <td>Orscha</td>
      <td>Retreat</td>
      <td>20000</td>
    </tr>
    <tr>
      <th>7</th>
      <td>26.8</td>
      <td>54.3</td>
      <td>Moiodexno</td>
      <td>Retreat</td>
      <td>12000</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



A common pattern is to assign the original name `minard` to the new DataFrame, so that all future uses of `minard` will refer to the relabeled data.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
minard = minard.rename(
    columns={
        'City': 'City Name',
    },
)

minard
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">



<div markdown="0" class="output output_html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Longitude</th>
      <th>Latitude</th>
      <th>City Name</th>
      <th>Direction</th>
      <th>Survivors</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>32.0</td>
      <td>54.8</td>
      <td>Smolensk</td>
      <td>Advance</td>
      <td>145000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>33.2</td>
      <td>54.9</td>
      <td>Dorogobouge</td>
      <td>Advance</td>
      <td>140000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>34.4</td>
      <td>55.5</td>
      <td>Chjat</td>
      <td>Advance</td>
      <td>127100</td>
    </tr>
    <tr>
      <th>3</th>
      <td>37.6</td>
      <td>55.8</td>
      <td>Moscou</td>
      <td>Advance</td>
      <td>100000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>34.3</td>
      <td>55.2</td>
      <td>Wixma</td>
      <td>Retreat</td>
      <td>55000</td>
    </tr>
    <tr>
      <th>5</th>
      <td>32.0</td>
      <td>54.6</td>
      <td>Smolensk</td>
      <td>Retreat</td>
      <td>24000</td>
    </tr>
    <tr>
      <th>6</th>
      <td>30.4</td>
      <td>54.4</td>
      <td>Orscha</td>
      <td>Retreat</td>
      <td>20000</td>
    </tr>
    <tr>
      <th>7</th>
      <td>26.8</td>
      <td>54.3</td>
      <td>Moiodexno</td>
      <td>Retreat</td>
      <td>12000</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



### Accessing the Data in a Column
We can use a column's label to access the series of data in the column.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
minard['Survivors']
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
0    145000
1    140000
2    127100
3    100000
4     55000
5     24000
6     20000
7     12000
Name: Survivors, dtype: int64
```


</div>
</div>
</div>



For simple column labels, such as Survivors, we can even treat the column like a standard property of the DataFrame.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
minard.Survivors
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
0    145000
1    140000
2    127100
3    100000
4     55000
5     24000
6     20000
7     12000
Name: Survivors, dtype: int64
```


</div>
</div>
</div>



(Note, however, that this latter syntax won't work for column labels containing spaces or punctuation beyond underscores – the label "this is cool!" cannot be accessed in this manner. Rather, it would have to be referred to as `minard['this is cool!']`.)



The 8 items in the series are indexed starting with 0, by default – 0, 1, 2, and so on, up to 7. The items in the column can be accessed as well.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
minard['Survivors'][0]
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
145000
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
minard['Survivors'][5]
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
24000
```


</div>
</div>
</div>



### Working with the Data in a Column

Because columns are underpinned by arrays, we can use array operations on them to discover new information. For example, we can create a new column that contains the percent of all survivors at each city after Smolensk.



Because in this case we actually *want* to modify the original DataFrame – rather than preserve both – we'll use direct assignment, rather than the `assign` method.

(This has the added benefit that we can more easily specify a sophisticated label, which contains spaces. However, it is often a safe default course of action to create a new DataFrame, via `assign`.)



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
initial_count = minard['Survivors'][0]

minard['Percent Surviving'] = minard['Survivors'] / initial_count

minard
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">



<div markdown="0" class="output output_html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Longitude</th>
      <th>Latitude</th>
      <th>City Name</th>
      <th>Direction</th>
      <th>Survivors</th>
      <th>Percent Surviving</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>32.0</td>
      <td>54.8</td>
      <td>Smolensk</td>
      <td>Advance</td>
      <td>145000</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>33.2</td>
      <td>54.9</td>
      <td>Dorogobouge</td>
      <td>Advance</td>
      <td>140000</td>
      <td>0.965517</td>
    </tr>
    <tr>
      <th>2</th>
      <td>34.4</td>
      <td>55.5</td>
      <td>Chjat</td>
      <td>Advance</td>
      <td>127100</td>
      <td>0.876552</td>
    </tr>
    <tr>
      <th>3</th>
      <td>37.6</td>
      <td>55.8</td>
      <td>Moscou</td>
      <td>Advance</td>
      <td>100000</td>
      <td>0.689655</td>
    </tr>
    <tr>
      <th>4</th>
      <td>34.3</td>
      <td>55.2</td>
      <td>Wixma</td>
      <td>Retreat</td>
      <td>55000</td>
      <td>0.379310</td>
    </tr>
    <tr>
      <th>5</th>
      <td>32.0</td>
      <td>54.6</td>
      <td>Smolensk</td>
      <td>Retreat</td>
      <td>24000</td>
      <td>0.165517</td>
    </tr>
    <tr>
      <th>6</th>
      <td>30.4</td>
      <td>54.4</td>
      <td>Orscha</td>
      <td>Retreat</td>
      <td>20000</td>
      <td>0.137931</td>
    </tr>
    <tr>
      <th>7</th>
      <td>26.8</td>
      <td>54.3</td>
      <td>Moiodexno</td>
      <td>Retreat</td>
      <td>12000</td>
      <td>0.082759</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



To make the proportions in the new column appear as percentages, we can use the `format` method of the DataFrame's `style` property. The `format` method accepts a single formatting function or formatting string, or a dictionary of formatters to apply by column.

Pandas uses the formatting string `"{:.2%}"` against data values as follows.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
"{:.2%}".format(0.082759)
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
'8.28%'
```


</div>
</div>
</div>



And so we can apply this formatting string to our new column.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
minard.style.format(
    {
        'Percent Surviving': "{:.2%}",
    },
)
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">



<div markdown="0" class="output output_html">
<style  type="text/css" >
</style><table id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9" ><thead>    <tr>        <th class="blank level0" ></th>        <th class="col_heading level0 col0" >Longitude</th>        <th class="col_heading level0 col1" >Latitude</th>        <th class="col_heading level0 col2" >City Name</th>        <th class="col_heading level0 col3" >Direction</th>        <th class="col_heading level0 col4" >Survivors</th>        <th class="col_heading level0 col5" >Percent Surviving</th>    </tr></thead><tbody>
                <tr>
                        <th id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9level0_row0" class="row_heading level0 row0" >0</th>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row0_col0" class="data row0 col0" >32</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row0_col1" class="data row0 col1" >54.8</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row0_col2" class="data row0 col2" >Smolensk</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row0_col3" class="data row0 col3" >Advance</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row0_col4" class="data row0 col4" >145000</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row0_col5" class="data row0 col5" >100.00%</td>
            </tr>
            <tr>
                        <th id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9level0_row1" class="row_heading level0 row1" >1</th>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row1_col0" class="data row1 col0" >33.2</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row1_col1" class="data row1 col1" >54.9</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row1_col2" class="data row1 col2" >Dorogobouge</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row1_col3" class="data row1 col3" >Advance</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row1_col4" class="data row1 col4" >140000</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row1_col5" class="data row1 col5" >96.55%</td>
            </tr>
            <tr>
                        <th id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9level0_row2" class="row_heading level0 row2" >2</th>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row2_col0" class="data row2 col0" >34.4</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row2_col1" class="data row2 col1" >55.5</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row2_col2" class="data row2 col2" >Chjat</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row2_col3" class="data row2 col3" >Advance</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row2_col4" class="data row2 col4" >127100</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row2_col5" class="data row2 col5" >87.66%</td>
            </tr>
            <tr>
                        <th id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9level0_row3" class="row_heading level0 row3" >3</th>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row3_col0" class="data row3 col0" >37.6</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row3_col1" class="data row3 col1" >55.8</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row3_col2" class="data row3 col2" >Moscou</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row3_col3" class="data row3 col3" >Advance</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row3_col4" class="data row3 col4" >100000</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row3_col5" class="data row3 col5" >68.97%</td>
            </tr>
            <tr>
                        <th id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9level0_row4" class="row_heading level0 row4" >4</th>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row4_col0" class="data row4 col0" >34.3</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row4_col1" class="data row4 col1" >55.2</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row4_col2" class="data row4 col2" >Wixma</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row4_col3" class="data row4 col3" >Retreat</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row4_col4" class="data row4 col4" >55000</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row4_col5" class="data row4 col5" >37.93%</td>
            </tr>
            <tr>
                        <th id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9level0_row5" class="row_heading level0 row5" >5</th>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row5_col0" class="data row5 col0" >32</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row5_col1" class="data row5 col1" >54.6</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row5_col2" class="data row5 col2" >Smolensk</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row5_col3" class="data row5 col3" >Retreat</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row5_col4" class="data row5 col4" >24000</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row5_col5" class="data row5 col5" >16.55%</td>
            </tr>
            <tr>
                        <th id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9level0_row6" class="row_heading level0 row6" >6</th>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row6_col0" class="data row6 col0" >30.4</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row6_col1" class="data row6 col1" >54.4</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row6_col2" class="data row6 col2" >Orscha</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row6_col3" class="data row6 col3" >Retreat</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row6_col4" class="data row6 col4" >20000</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row6_col5" class="data row6 col5" >13.79%</td>
            </tr>
            <tr>
                        <th id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9level0_row7" class="row_heading level0 row7" >7</th>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row7_col0" class="data row7 col0" >26.8</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row7_col1" class="data row7 col1" >54.3</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row7_col2" class="data row7 col2" >Moiodexno</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row7_col3" class="data row7 col3" >Retreat</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row7_col4" class="data row7 col4" >12000</td>
                        <td id="T_1f7373f2_a9bd_11e9_94b2_e7bf19016fc9row7_col5" class="data row7 col5" >8.28%</td>
            </tr>
    </tbody></table>
</div>


</div>
</div>
</div>



And we can hang onto our formatting specification for reuse.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
minard_format = {
    'Percent Surviving': "{:.2%}",
}

minard.style.format(minard_format)
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">



<div markdown="0" class="output output_html">
<style  type="text/css" >
</style><table id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9" ><thead>    <tr>        <th class="blank level0" ></th>        <th class="col_heading level0 col0" >Longitude</th>        <th class="col_heading level0 col1" >Latitude</th>        <th class="col_heading level0 col2" >City Name</th>        <th class="col_heading level0 col3" >Direction</th>        <th class="col_heading level0 col4" >Survivors</th>        <th class="col_heading level0 col5" >Percent Surviving</th>    </tr></thead><tbody>
                <tr>
                        <th id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9level0_row0" class="row_heading level0 row0" >0</th>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row0_col0" class="data row0 col0" >32</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row0_col1" class="data row0 col1" >54.8</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row0_col2" class="data row0 col2" >Smolensk</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row0_col3" class="data row0 col3" >Advance</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row0_col4" class="data row0 col4" >145000</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row0_col5" class="data row0 col5" >100.00%</td>
            </tr>
            <tr>
                        <th id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9level0_row1" class="row_heading level0 row1" >1</th>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row1_col0" class="data row1 col0" >33.2</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row1_col1" class="data row1 col1" >54.9</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row1_col2" class="data row1 col2" >Dorogobouge</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row1_col3" class="data row1 col3" >Advance</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row1_col4" class="data row1 col4" >140000</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row1_col5" class="data row1 col5" >96.55%</td>
            </tr>
            <tr>
                        <th id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9level0_row2" class="row_heading level0 row2" >2</th>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row2_col0" class="data row2 col0" >34.4</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row2_col1" class="data row2 col1" >55.5</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row2_col2" class="data row2 col2" >Chjat</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row2_col3" class="data row2 col3" >Advance</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row2_col4" class="data row2 col4" >127100</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row2_col5" class="data row2 col5" >87.66%</td>
            </tr>
            <tr>
                        <th id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9level0_row3" class="row_heading level0 row3" >3</th>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row3_col0" class="data row3 col0" >37.6</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row3_col1" class="data row3 col1" >55.8</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row3_col2" class="data row3 col2" >Moscou</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row3_col3" class="data row3 col3" >Advance</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row3_col4" class="data row3 col4" >100000</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row3_col5" class="data row3 col5" >68.97%</td>
            </tr>
            <tr>
                        <th id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9level0_row4" class="row_heading level0 row4" >4</th>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row4_col0" class="data row4 col0" >34.3</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row4_col1" class="data row4 col1" >55.2</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row4_col2" class="data row4 col2" >Wixma</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row4_col3" class="data row4 col3" >Retreat</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row4_col4" class="data row4 col4" >55000</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row4_col5" class="data row4 col5" >37.93%</td>
            </tr>
            <tr>
                        <th id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9level0_row5" class="row_heading level0 row5" >5</th>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row5_col0" class="data row5 col0" >32</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row5_col1" class="data row5 col1" >54.6</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row5_col2" class="data row5 col2" >Smolensk</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row5_col3" class="data row5 col3" >Retreat</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row5_col4" class="data row5 col4" >24000</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row5_col5" class="data row5 col5" >16.55%</td>
            </tr>
            <tr>
                        <th id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9level0_row6" class="row_heading level0 row6" >6</th>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row6_col0" class="data row6 col0" >30.4</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row6_col1" class="data row6 col1" >54.4</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row6_col2" class="data row6 col2" >Orscha</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row6_col3" class="data row6 col3" >Retreat</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row6_col4" class="data row6 col4" >20000</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row6_col5" class="data row6 col5" >13.79%</td>
            </tr>
            <tr>
                        <th id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9level0_row7" class="row_heading level0 row7" >7</th>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row7_col0" class="data row7 col0" >26.8</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row7_col1" class="data row7 col1" >54.3</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row7_col2" class="data row7 col2" >Moiodexno</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row7_col3" class="data row7 col3" >Retreat</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row7_col4" class="data row7 col4" >12000</td>
                        <td id="T_1f7373f3_a9bd_11e9_94b2_e7bf19016fc9row7_col5" class="data row7 col5" >8.28%</td>
            </tr>
    </tbody></table>
</div>


</div>
</div>
</div>



### Choosing Sets of Columns

The property `loc` may be used to create a new DataFrame that contains only the specified columns.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
minard.loc[:, ['Longitude', 'Latitude']]
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">



<div markdown="0" class="output output_html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Longitude</th>
      <th>Latitude</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>32.0</td>
      <td>54.8</td>
    </tr>
    <tr>
      <th>1</th>
      <td>33.2</td>
      <td>54.9</td>
    </tr>
    <tr>
      <th>2</th>
      <td>34.4</td>
      <td>55.5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>37.6</td>
      <td>55.8</td>
    </tr>
    <tr>
      <th>4</th>
      <td>34.3</td>
      <td>55.2</td>
    </tr>
    <tr>
      <th>5</th>
      <td>32.0</td>
      <td>54.6</td>
    </tr>
    <tr>
      <th>6</th>
      <td>30.4</td>
      <td>54.4</td>
    </tr>
    <tr>
      <th>7</th>
      <td>26.8</td>
      <td>54.3</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



The same selection can be made directly against the DataFrame.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
minard[['Longitude', 'Latitude']]
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">



<div markdown="0" class="output output_html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Longitude</th>
      <th>Latitude</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>32.0</td>
      <td>54.8</td>
    </tr>
    <tr>
      <th>1</th>
      <td>33.2</td>
      <td>54.9</td>
    </tr>
    <tr>
      <th>2</th>
      <td>34.4</td>
      <td>55.5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>37.6</td>
      <td>55.8</td>
    </tr>
    <tr>
      <th>4</th>
      <td>34.3</td>
      <td>55.2</td>
    </tr>
    <tr>
      <th>5</th>
      <td>32.0</td>
      <td>54.6</td>
    </tr>
    <tr>
      <th>6</th>
      <td>30.4</td>
      <td>54.4</td>
    </tr>
    <tr>
      <th>7</th>
      <td>26.8</td>
      <td>54.3</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



The result of this syntax is a new DataFrame, even when you name just one column.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
minard[['Survivors']]
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">



<div markdown="0" class="output output_html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Survivors</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>145000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>140000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>127100</td>
    </tr>
    <tr>
      <th>3</th>
      <td>100000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>55000</td>
    </tr>
    <tr>
      <th>5</th>
      <td>24000</td>
    </tr>
    <tr>
      <th>6</th>
      <td>20000</td>
    </tr>
    <tr>
      <th>7</th>
      <td>12000</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



Notice that the result is a DataFrame, unlike when we used only a single pair of brackets, which returns the underlying Series.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
minard['Survivors']
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
0    145000
1    140000
2    127100
3    100000
4     55000
5     24000
6     20000
7     12000
Name: Survivors, dtype: int64
```


</div>
</div>
</div>



Another way to create a new DataFrame consisting of a set of columns is to `drop` the columns you don't want.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
minard.drop(columns=['Longitude', 'Latitude', 'Direction'])
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">



<div markdown="0" class="output output_html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>City Name</th>
      <th>Survivors</th>
      <th>Percent Surviving</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Smolensk</td>
      <td>145000</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Dorogobouge</td>
      <td>140000</td>
      <td>0.965517</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Chjat</td>
      <td>127100</td>
      <td>0.876552</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Moscou</td>
      <td>100000</td>
      <td>0.689655</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Wixma</td>
      <td>55000</td>
      <td>0.379310</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Smolensk</td>
      <td>24000</td>
      <td>0.165517</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Orscha</td>
      <td>20000</td>
      <td>0.137931</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Moiodexno</td>
      <td>12000</td>
      <td>0.082759</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



Neither column selection nor the `drop` method change the original DataFrame. Instead, they create new smaller DataFrames that share the same data. The fact that the original DataFrame is preserved is useful! You can generate multiple different DataFrames that only consider certain columns without worrying that one analysis will affect the other.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
minard.style.format(minard_format)
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">



<div markdown="0" class="output output_html">
<style  type="text/css" >
</style><table id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9" ><thead>    <tr>        <th class="blank level0" ></th>        <th class="col_heading level0 col0" >Longitude</th>        <th class="col_heading level0 col1" >Latitude</th>        <th class="col_heading level0 col2" >City Name</th>        <th class="col_heading level0 col3" >Direction</th>        <th class="col_heading level0 col4" >Survivors</th>        <th class="col_heading level0 col5" >Percent Surviving</th>    </tr></thead><tbody>
                <tr>
                        <th id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9level0_row0" class="row_heading level0 row0" >0</th>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row0_col0" class="data row0 col0" >32</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row0_col1" class="data row0 col1" >54.8</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row0_col2" class="data row0 col2" >Smolensk</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row0_col3" class="data row0 col3" >Advance</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row0_col4" class="data row0 col4" >145000</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row0_col5" class="data row0 col5" >100.00%</td>
            </tr>
            <tr>
                        <th id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9level0_row1" class="row_heading level0 row1" >1</th>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row1_col0" class="data row1 col0" >33.2</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row1_col1" class="data row1 col1" >54.9</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row1_col2" class="data row1 col2" >Dorogobouge</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row1_col3" class="data row1 col3" >Advance</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row1_col4" class="data row1 col4" >140000</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row1_col5" class="data row1 col5" >96.55%</td>
            </tr>
            <tr>
                        <th id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9level0_row2" class="row_heading level0 row2" >2</th>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row2_col0" class="data row2 col0" >34.4</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row2_col1" class="data row2 col1" >55.5</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row2_col2" class="data row2 col2" >Chjat</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row2_col3" class="data row2 col3" >Advance</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row2_col4" class="data row2 col4" >127100</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row2_col5" class="data row2 col5" >87.66%</td>
            </tr>
            <tr>
                        <th id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9level0_row3" class="row_heading level0 row3" >3</th>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row3_col0" class="data row3 col0" >37.6</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row3_col1" class="data row3 col1" >55.8</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row3_col2" class="data row3 col2" >Moscou</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row3_col3" class="data row3 col3" >Advance</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row3_col4" class="data row3 col4" >100000</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row3_col5" class="data row3 col5" >68.97%</td>
            </tr>
            <tr>
                        <th id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9level0_row4" class="row_heading level0 row4" >4</th>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row4_col0" class="data row4 col0" >34.3</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row4_col1" class="data row4 col1" >55.2</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row4_col2" class="data row4 col2" >Wixma</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row4_col3" class="data row4 col3" >Retreat</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row4_col4" class="data row4 col4" >55000</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row4_col5" class="data row4 col5" >37.93%</td>
            </tr>
            <tr>
                        <th id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9level0_row5" class="row_heading level0 row5" >5</th>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row5_col0" class="data row5 col0" >32</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row5_col1" class="data row5 col1" >54.6</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row5_col2" class="data row5 col2" >Smolensk</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row5_col3" class="data row5 col3" >Retreat</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row5_col4" class="data row5 col4" >24000</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row5_col5" class="data row5 col5" >16.55%</td>
            </tr>
            <tr>
                        <th id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9level0_row6" class="row_heading level0 row6" >6</th>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row6_col0" class="data row6 col0" >30.4</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row6_col1" class="data row6 col1" >54.4</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row6_col2" class="data row6 col2" >Orscha</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row6_col3" class="data row6 col3" >Retreat</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row6_col4" class="data row6 col4" >20000</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row6_col5" class="data row6 col5" >13.79%</td>
            </tr>
            <tr>
                        <th id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9level0_row7" class="row_heading level0 row7" >7</th>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row7_col0" class="data row7 col0" >26.8</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row7_col1" class="data row7 col1" >54.3</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row7_col2" class="data row7 col2" >Moiodexno</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row7_col3" class="data row7 col3" >Retreat</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row7_col4" class="data row7 col4" >12000</td>
                        <td id="T_1f7373f4_a9bd_11e9_94b2_e7bf19016fc9row7_col5" class="data row7 col5" >8.28%</td>
            </tr>
    </tbody></table>
</div>


</div>
</div>
</div>



All of the methods that we have used above can be applied to any DataFrame.

