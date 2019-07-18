---
redirect_from:
  - "/chapters/03/4/introduction-to-dataframes"
interact_link: content/chapters/03/4/Introduction_to_DataFrames.ipynb
kernel_name: python3
has_widgets: false
title: 'Introduction to DataFrames'
prev_page:
  url: /chapters/03/3/Calls
  title: 'Call Expressions'
next_page:
  url: /chapters/04/Data_Types
  title: 'Data Types'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---






# Introduction to DataFrames

We can now apply Python to analyze data. We will work with data stored in the pandas library's `DataFrame` structure.

DataFrames are a fundamental way of representing data sets. A DataFrame can be viewed in two ways:
* a sequence of named columns that each describe a single attribute of all entries in a data set, or
* a sequence of rows that each contain all information about a single individual in a data set.

We will study DataFrames in great detail in the next several chapters. For now, we will just introduce a few methods without going into technical details. 

The DataFrame `cones` has been imported for us; later we will see how, but here we will just work with it. First, let's take a look at it.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cones
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
      <th>Flavor</th>
      <th>Color</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>strawberry</td>
      <td>pink</td>
      <td>3.55</td>
    </tr>
    <tr>
      <th>1</th>
      <td>chocolate</td>
      <td>light brown</td>
      <td>4.75</td>
    </tr>
    <tr>
      <th>2</th>
      <td>chocolate</td>
      <td>dark brown</td>
      <td>5.25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>strawberry</td>
      <td>pink</td>
      <td>5.25</td>
    </tr>
    <tr>
      <th>4</th>
      <td>chocolate</td>
      <td>dark brown</td>
      <td>5.25</td>
    </tr>
    <tr>
      <th>5</th>
      <td>bubblegum</td>
      <td>pink</td>
      <td>4.75</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



The DataFrame has six rows. Each row corresponds to one ice cream cone. The ice cream cones are the *individuals*.

Each cone has three attributes: flavor, color, and price. Each column contains the data on one of these attributes, and so all the entries of any single column are of the same kind. Each column has a label. We will refer to columns by their labels.

A DataFrame method is just like a function, but it must operate on a DataFrame. So in general the call looks like:

    name_of_dataframe.method(arguments)

On the other hand, a DataFrame property returns a new object for operation, such as the Python *slice* operation, `[start:stop:interval]`:

    name_of_dataframe.property[start:stop:interval]

For example, if you want to see just the first two rows of data, you can use the DataFrame property `iloc`, for *integer-location* based look-up by position in the row index.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cones.iloc[:2]
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
      <th>Flavor</th>
      <th>Color</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>strawberry</td>
      <td>pink</td>
      <td>3.55</td>
    </tr>
    <tr>
      <th>1</th>
      <td>chocolate</td>
      <td>light brown</td>
      <td>4.75</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



You can replace 2 by any number of rows. If you ask for more than six, you will only get six, because `cones` only has six rows.



### Choosing Sets of Columns
The property `loc` provides access to groups of rows and columns by *label*.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cones.loc[:, ['Flavor']]
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
      <th>Flavor</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>strawberry</td>
    </tr>
    <tr>
      <th>1</th>
      <td>chocolate</td>
    </tr>
    <tr>
      <th>2</th>
      <td>chocolate</td>
    </tr>
    <tr>
      <th>3</th>
      <td>strawberry</td>
    </tr>
    <tr>
      <th>4</th>
      <td>chocolate</td>
    </tr>
    <tr>
      <th>5</th>
      <td>bubblegum</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



This leaves the original table unchanged.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cones
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
      <th>Flavor</th>
      <th>Color</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>strawberry</td>
      <td>pink</td>
      <td>3.55</td>
    </tr>
    <tr>
      <th>1</th>
      <td>chocolate</td>
      <td>light brown</td>
      <td>4.75</td>
    </tr>
    <tr>
      <th>2</th>
      <td>chocolate</td>
      <td>dark brown</td>
      <td>5.25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>strawberry</td>
      <td>pink</td>
      <td>5.25</td>
    </tr>
    <tr>
      <th>4</th>
      <td>chocolate</td>
      <td>dark brown</td>
      <td>5.25</td>
    </tr>
    <tr>
      <th>5</th>
      <td>bubblegum</td>
      <td>pink</td>
      <td>4.75</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



You can select more than one column, by separating the column labels by commas.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cones.loc[:, ['Flavor', 'Price']]
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
      <th>Flavor</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>strawberry</td>
      <td>3.55</td>
    </tr>
    <tr>
      <th>1</th>
      <td>chocolate</td>
      <td>4.75</td>
    </tr>
    <tr>
      <th>2</th>
      <td>chocolate</td>
      <td>5.25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>strawberry</td>
      <td>5.25</td>
    </tr>
    <tr>
      <th>4</th>
      <td>chocolate</td>
      <td>5.25</td>
    </tr>
    <tr>
      <th>5</th>
      <td>bubblegum</td>
      <td>4.75</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



You can also *drop* columns you don't want. The table above can be created by dropping the `Color` column.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cones.drop(columns=['Color'])
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
      <th>Flavor</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>strawberry</td>
      <td>3.55</td>
    </tr>
    <tr>
      <th>1</th>
      <td>chocolate</td>
      <td>4.75</td>
    </tr>
    <tr>
      <th>2</th>
      <td>chocolate</td>
      <td>5.25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>strawberry</td>
      <td>5.25</td>
    </tr>
    <tr>
      <th>4</th>
      <td>chocolate</td>
      <td>5.25</td>
    </tr>
    <tr>
      <th>5</th>
      <td>bubblegum</td>
      <td>4.75</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



You can name this new table and look at it again by just typing its name.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
no_colors = cones.drop(columns=['Color'])

no_colors
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
      <th>Flavor</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>strawberry</td>
      <td>3.55</td>
    </tr>
    <tr>
      <th>1</th>
      <td>chocolate</td>
      <td>4.75</td>
    </tr>
    <tr>
      <th>2</th>
      <td>chocolate</td>
      <td>5.25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>strawberry</td>
      <td>5.25</td>
    </tr>
    <tr>
      <th>4</th>
      <td>chocolate</td>
      <td>5.25</td>
    </tr>
    <tr>
      <th>5</th>
      <td>bubblegum</td>
      <td>4.75</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



As with the `loc` property, the `drop` method creates a smaller DataFrame and leaves the original DataFrame unchanged. In order to explore your data, you can create any number of smaller DataFrames by using choosing or dropping columns. It will do no harm to your original data DataFrame.



### Sorting Rows



The `sort_values` method creates a new DataFrame by arranging the rows of the original DataFrame in ascending order of the values in the specified column. Here the `cones` DataFrame has been sorted in ascending order of the price of the cones.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cones.sort_values('Price')
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
      <th>Flavor</th>
      <th>Color</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>strawberry</td>
      <td>pink</td>
      <td>3.55</td>
    </tr>
    <tr>
      <th>1</th>
      <td>chocolate</td>
      <td>light brown</td>
      <td>4.75</td>
    </tr>
    <tr>
      <th>5</th>
      <td>bubblegum</td>
      <td>pink</td>
      <td>4.75</td>
    </tr>
    <tr>
      <th>2</th>
      <td>chocolate</td>
      <td>dark brown</td>
      <td>5.25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>strawberry</td>
      <td>pink</td>
      <td>5.25</td>
    </tr>
    <tr>
      <th>4</th>
      <td>chocolate</td>
      <td>dark brown</td>
      <td>5.25</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



To sort in descending order, you can use an *optional* argument to `sort_values`. As the name implies, optional arguments don't have to be used, but they can be used if you want to change the default behavior of a method. 

By default, `sort_values` sorts in increasing order of the values in the specified column. To sort in decreasing order, use the optional argument `ascending=False`.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cones.sort_values('Price', ascending=False)
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
      <th>Flavor</th>
      <th>Color</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>chocolate</td>
      <td>dark brown</td>
      <td>5.25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>strawberry</td>
      <td>pink</td>
      <td>5.25</td>
    </tr>
    <tr>
      <th>4</th>
      <td>chocolate</td>
      <td>dark brown</td>
      <td>5.25</td>
    </tr>
    <tr>
      <th>1</th>
      <td>chocolate</td>
      <td>light brown</td>
      <td>4.75</td>
    </tr>
    <tr>
      <th>5</th>
      <td>bubblegum</td>
      <td>pink</td>
      <td>4.75</td>
    </tr>
    <tr>
      <th>0</th>
      <td>strawberry</td>
      <td>pink</td>
      <td>3.55</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



Like `drop`, the `sort_values` method leaves the original DataFrame unchanged.



### Selecting Rows that Satisfy a Condition

The `loc` property also allows you to create a new DataFrame consisting only of those rows specified by a given Boolean series, such as:

    [True, False, True]

We can generate such a series as simply as constructing a conditional expression in Python.

In this section we will work with a very simple condition, which is that the value in a specified column must be equal to a value that we also specify.

We will create a DataFrame consisting only of those rows corresponding to *chocolate* cones.



Unlike in our first example with `loc`, wherein we constructed a new `DataFrame` given the one-item list of columns –

    ['Flavor']

– in this example we will select only the `Series` of data underlying that column, by specifying only the column name.

In the cell below, the data is the same, but it is not presented as a table, because it is not a `DataFrame`.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cones.loc[:, 'Flavor']
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
0    strawberry
1     chocolate
2     chocolate
3    strawberry
4     chocolate
5     bubblegum
Name: Flavor, dtype: object
```


</div>
</div>
</div>



Because this is a very common operation, this expression can be shortened, such that the operation is applied to the DataFrame itself, as though it were a common Python `dict`.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cones['Flavor']
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
0    strawberry
1     chocolate
2     chocolate
3    strawberry
4     chocolate
5     bubblegum
Name: Flavor, dtype: object
```


</div>
</div>
</div>



From this `Series`, we can construct a new one indicating those rows whose values are `chocolate`.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cones['Flavor'] == 'chocolate'
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
0    False
1     True
2     True
3    False
4     True
5    False
Name: Flavor, dtype: bool
```


</div>
</div>
</div>



Putting it all together, we can hand this Boolean series to `loc`, to select only the rows corresponding to chocolate cones.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
where_chocolate = cones['Flavor'] == 'chocolate'
cones.loc[where_chocolate]
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
      <th>Flavor</th>
      <th>Color</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>chocolate</td>
      <td>light brown</td>
      <td>4.75</td>
    </tr>
    <tr>
      <th>2</th>
      <td>chocolate</td>
      <td>dark brown</td>
      <td>5.25</td>
    </tr>
    <tr>
      <th>4</th>
      <td>chocolate</td>
      <td>dark brown</td>
      <td>5.25</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



It is important to provide the value exactly. For example, if we specify `Chocolate` instead of `chocolate`, then the condition correctly finds no rows where the flavor is `Chocolate`.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
where_chocolate = cones['Flavor'] == 'Chocolate'
where_chocolate
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
0    False
1    False
2    False
3    False
4    False
5    False
Name: Flavor, dtype: bool
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
cones.loc[where_chocolate]
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
      <th>Flavor</th>
      <th>Color</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



### Example: Salaries in the NBA



"The NBA is the highest paying professional sports league in the world," [reported CNN](http://edition.cnn.com/2015/12/04/sport/gallery/highest-paid-nba-players/) in March 2016. The table `nba` contains the [salaries of all National Basketball Association players](https://www.statcrunch.com/app/index.php?dataid=1843341) in 2015-2016.

Each row represents one player. The columns are:

| **Column Label**   | Description                                         |
|--------------------|-----------------------------------------------------|
| `PLAYER`           | Player's name                                       |
| `POSITION`         | Player's position on team                           |
| `TEAM`             | Team name                                           |
|`SALARY`    | Player's salary in 2015-2016, in millions of dollars|
 
The code for the positions is PG (Point Guard), SG (Shooting Guard), PF (Power Forward), SF (Small Forward), and C (Center). But what follows doesn't involve details about how basketball is played.

The first row shows that Paul Millsap, Power Forward for the Atlanta Hawks, had a salary of almost $\$18.7$ million in 2015-2016.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba
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
      <th>PLAYER</th>
      <th>POSITION</th>
      <th>TEAM</th>
      <th>SALARY</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Paul Millsap</td>
      <td>PF</td>
      <td>Atlanta Hawks</td>
      <td>18.671659</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Al Horford</td>
      <td>C</td>
      <td>Atlanta Hawks</td>
      <td>12.000000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Tiago Splitter</td>
      <td>C</td>
      <td>Atlanta Hawks</td>
      <td>9.756250</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Jeff Teague</td>
      <td>PG</td>
      <td>Atlanta Hawks</td>
      <td>8.000000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Kyle Korver</td>
      <td>SG</td>
      <td>Atlanta Hawks</td>
      <td>5.746479</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>412</th>
      <td>Gary Neal</td>
      <td>PG</td>
      <td>Washington Wizards</td>
      <td>2.139000</td>
    </tr>
    <tr>
      <th>413</th>
      <td>DeJuan Blair</td>
      <td>C</td>
      <td>Washington Wizards</td>
      <td>2.000000</td>
    </tr>
    <tr>
      <th>414</th>
      <td>Kelly Oubre Jr.</td>
      <td>SF</td>
      <td>Washington Wizards</td>
      <td>1.920240</td>
    </tr>
    <tr>
      <th>415</th>
      <td>Garrett Temple</td>
      <td>SG</td>
      <td>Washington Wizards</td>
      <td>1.100602</td>
    </tr>
    <tr>
      <th>416</th>
      <td>Jarell Eddie</td>
      <td>SG</td>
      <td>Washington Wizards</td>
      <td>0.561716</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



Fans of Stephen Curry can find his row by using `loc`.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba.loc[
    nba['PLAYER'] == 'Stephen Curry'
]
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
      <th>PLAYER</th>
      <th>POSITION</th>
      <th>TEAM</th>
      <th>SALARY</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>121</th>
      <td>Stephen Curry</td>
      <td>PG</td>
      <td>Golden State Warriors</td>
      <td>11.370786</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



We can also create a new DataFrame called `warriors` consisting of just the data for the Golden State Warriors.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
warriors = nba.loc[nba['TEAM'] == 'Golden State Warriors']

warriors
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
      <th>PLAYER</th>
      <th>POSITION</th>
      <th>TEAM</th>
      <th>SALARY</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>117</th>
      <td>Klay Thompson</td>
      <td>SG</td>
      <td>Golden State Warriors</td>
      <td>15.501000</td>
    </tr>
    <tr>
      <th>118</th>
      <td>Draymond Green</td>
      <td>PF</td>
      <td>Golden State Warriors</td>
      <td>14.260870</td>
    </tr>
    <tr>
      <th>119</th>
      <td>Andrew Bogut</td>
      <td>C</td>
      <td>Golden State Warriors</td>
      <td>13.800000</td>
    </tr>
    <tr>
      <th>120</th>
      <td>Andre Iguodala</td>
      <td>SF</td>
      <td>Golden State Warriors</td>
      <td>11.710456</td>
    </tr>
    <tr>
      <th>121</th>
      <td>Stephen Curry</td>
      <td>PG</td>
      <td>Golden State Warriors</td>
      <td>11.370786</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>126</th>
      <td>Leandro Barbosa</td>
      <td>SG</td>
      <td>Golden State Warriors</td>
      <td>2.500000</td>
    </tr>
    <tr>
      <th>127</th>
      <td>Festus Ezeli</td>
      <td>C</td>
      <td>Golden State Warriors</td>
      <td>2.008748</td>
    </tr>
    <tr>
      <th>128</th>
      <td>Brandon Rush</td>
      <td>SF</td>
      <td>Golden State Warriors</td>
      <td>1.270964</td>
    </tr>
    <tr>
      <th>129</th>
      <td>Kevon Looney</td>
      <td>SF</td>
      <td>Golden State Warriors</td>
      <td>1.131960</td>
    </tr>
    <tr>
      <th>130</th>
      <td>Anderson Varejao</td>
      <td>PF</td>
      <td>Golden State Warriors</td>
      <td>0.289755</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



Pandas has been configured here to display no more than 10 rows of DataFrames by default. You can use method `to_string` to customize this display. To display the entire table, use `to_string` with no arguments in the parentheses.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
print(warriors.to_string())
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_stream}
```
                PLAYER POSITION                   TEAM     SALARY
117      Klay Thompson       SG  Golden State Warriors  15.501000
118     Draymond Green       PF  Golden State Warriors  14.260870
119       Andrew Bogut        C  Golden State Warriors  13.800000
120     Andre Iguodala       SF  Golden State Warriors  11.710456
121      Stephen Curry       PG  Golden State Warriors  11.370786
122     Jason Thompson       PF  Golden State Warriors   7.008475
123   Shaun Livingston       PG  Golden State Warriors   5.543725
124    Harrison Barnes       SF  Golden State Warriors   3.873398
125  Marreese Speights        C  Golden State Warriors   3.815000
126    Leandro Barbosa       SG  Golden State Warriors   2.500000
127       Festus Ezeli        C  Golden State Warriors   2.008748
128       Brandon Rush       SF  Golden State Warriors   1.270964
129       Kevon Looney       SF  Golden State Warriors   1.131960
130   Anderson Varejao       PF  Golden State Warriors   0.289755
```
</div>
</div>
</div>



The `nba` DataFrame is sorted in alphabetical order of the team names. To see how the players were paid in 2015-2016, it is useful to sort the data by salary. Remember that by default, the sorting is in increasing order.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba.sort_values('SALARY')
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
      <th>PLAYER</th>
      <th>POSITION</th>
      <th>TEAM</th>
      <th>SALARY</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>267</th>
      <td>Thanasis Antetokounmpo</td>
      <td>SF</td>
      <td>New York Knicks</td>
      <td>0.030888</td>
    </tr>
    <tr>
      <th>327</th>
      <td>Cory Jefferson</td>
      <td>PF</td>
      <td>Phoenix Suns</td>
      <td>0.049709</td>
    </tr>
    <tr>
      <th>326</th>
      <td>Jordan McRae</td>
      <td>SG</td>
      <td>Phoenix Suns</td>
      <td>0.049709</td>
    </tr>
    <tr>
      <th>324</th>
      <td>Orlando Johnson</td>
      <td>SG</td>
      <td>Phoenix Suns</td>
      <td>0.055722</td>
    </tr>
    <tr>
      <th>325</th>
      <td>Phil Pressey</td>
      <td>PG</td>
      <td>Phoenix Suns</td>
      <td>0.055722</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>131</th>
      <td>Dwight Howard</td>
      <td>C</td>
      <td>Houston Rockets</td>
      <td>22.359364</td>
    </tr>
    <tr>
      <th>255</th>
      <td>Carmelo Anthony</td>
      <td>SF</td>
      <td>New York Knicks</td>
      <td>22.875000</td>
    </tr>
    <tr>
      <th>72</th>
      <td>LeBron James</td>
      <td>SF</td>
      <td>Cleveland Cavaliers</td>
      <td>22.970500</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Joe Johnson</td>
      <td>SF</td>
      <td>Brooklyn Nets</td>
      <td>24.894863</td>
    </tr>
    <tr>
      <th>169</th>
      <td>Kobe Bryant</td>
      <td>SF</td>
      <td>Los Angeles Lakers</td>
      <td>25.000000</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



These figures are somewhat difficult to compare as some of these players changed teams during the season and received salaries from more than one team; only the salary from the last team appears in the table.  

The CNN report is about the other end of the salary scale – the players who are among the highest paid in the world. To identify these players we can sort in descending order of salary and look at the top few rows.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba.sort_values('SALARY', ascending=False).iloc[:10]
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
      <th>PLAYER</th>
      <th>POSITION</th>
      <th>TEAM</th>
      <th>SALARY</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>169</th>
      <td>Kobe Bryant</td>
      <td>SF</td>
      <td>Los Angeles Lakers</td>
      <td>25.000000</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Joe Johnson</td>
      <td>SF</td>
      <td>Brooklyn Nets</td>
      <td>24.894863</td>
    </tr>
    <tr>
      <th>72</th>
      <td>LeBron James</td>
      <td>SF</td>
      <td>Cleveland Cavaliers</td>
      <td>22.970500</td>
    </tr>
    <tr>
      <th>255</th>
      <td>Carmelo Anthony</td>
      <td>SF</td>
      <td>New York Knicks</td>
      <td>22.875000</td>
    </tr>
    <tr>
      <th>131</th>
      <td>Dwight Howard</td>
      <td>C</td>
      <td>Houston Rockets</td>
      <td>22.359364</td>
    </tr>
    <tr>
      <th>201</th>
      <td>Chris Bosh</td>
      <td>PF</td>
      <td>Miami Heat</td>
      <td>22.192730</td>
    </tr>
    <tr>
      <th>156</th>
      <td>Chris Paul</td>
      <td>PG</td>
      <td>Los Angeles Clippers</td>
      <td>21.468695</td>
    </tr>
    <tr>
      <th>268</th>
      <td>Kevin Durant</td>
      <td>SF</td>
      <td>Oklahoma City Thunder</td>
      <td>20.158622</td>
    </tr>
    <tr>
      <th>60</th>
      <td>Derrick Rose</td>
      <td>PG</td>
      <td>Chicago Bulls</td>
      <td>20.093064</td>
    </tr>
    <tr>
      <th>202</th>
      <td>Dwyane Wade</td>
      <td>SG</td>
      <td>Miami Heat</td>
      <td>20.000000</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



Kobe Bryant, since retired, was the highest earning NBA player in 2015-2016.

