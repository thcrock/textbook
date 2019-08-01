---
redirect_from:
  - "/chapters/06/2/selecting-rows"
interact_link: content/chapters/06/2/Selecting_Rows.ipynb
kernel_name: python3
has_widgets: false
title: 'Selecting Rows'
prev_page:
  url: /chapters/06/1/Sorting_Rows
  title: 'Sorting Rows'
next_page:
  url: /chapters/06/3/Example_Trends_in_the_Population_of_the_United_States
  title: 'Example: Population Trends'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---






# Selecting Rows

Often, we would like to extract just those rows that correspond to entries with a particular feature. For example, we might want only the rows corresponding to the Warriors, or to players who earned more than \\$10 million. Or we might just want the top five earners.



### Specified Rows

The DataFrame property `iloc` allows for the selection of rows by their integer position in the index. It supports argument signatures including a single row index or an array of indices; and it returns, respectively, the row's underlying Series or a new DataFrame consisting of only those rows.

For example, if we wanted just the first row of `nba`, we could use `iloc` as follows.



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



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba.iloc[[0]]
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
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



This is a new DataFrame with just the single row that we specified.

Note that, by default, the index starts with the integer `0`.

We could also get the fourth, fifth, and sixth rows by specifying a range of indices as the argument – starting at index `3` and ending (before) index `6`.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
list(range(3, 6))
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
[3, 4, 5]
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba.iloc[range(3, 6)]
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
      <th>5</th>
      <td>Thabo Sefolosha</td>
      <td>SF</td>
      <td>Atlanta Hawks</td>
      <td>4.000000</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



More typically, we might specify such a range using Python's `slice` syntax.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba.iloc[3:6]
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
      <th>5</th>
      <td>Thabo Sefolosha</td>
      <td>SF</td>
      <td>Atlanta Hawks</td>
      <td>4.000000</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



If we want a DataFrame of the top 5 highest paid players, we can first sort the data by salary and then select the first five rows:



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba.sort_values(['SALARY'], ascending=False).iloc[:5]
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
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



### Rows Corresponding to a Specified Feature

More often, we will want to access data in a set of rows that have a certain feature, but whose indices we don't know ahead of time. For example, we might want data on all the players who made more than $10 million, but we don't want to spend time counting rows in the sorted DataFrame.

The DataFrame property `loc` does the job for us. It supports the output of a DataFrame with the same columns as the original but only the rows where the feature occurs.

This is specified to `loc` using a Boolean sequence, indicating the rows satisfying our condition, such as:

    [True, False, True]

…and which we may generate from a simple conditional expression in Python, applied to the Pandas `Series` of data underlying the feature itself.

In the first example, we extract the data for all those who earned more than $10 million.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba['SALARY']
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
0      18.671659
1      12.000000
2       9.756250
3       8.000000
4       5.746479
         ...    
412     2.139000
413     2.000000
414     1.920240
415     1.100602
416     0.561716
Name: SALARY, dtype: float64
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba['SALARY'] > 10
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
0       True
1       True
2      False
3      False
4      False
       ...  
412    False
413    False
414    False
415    False
416    False
Name: SALARY, dtype: bool
```


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba.loc[nba['SALARY'] > 10]
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
      <th>29</th>
      <td>Joe Johnson</td>
      <td>SF</td>
      <td>Brooklyn Nets</td>
      <td>24.894863</td>
    </tr>
    <tr>
      <th>30</th>
      <td>Thaddeus Young</td>
      <td>PF</td>
      <td>Brooklyn Nets</td>
      <td>11.235955</td>
    </tr>
    <tr>
      <th>42</th>
      <td>Al Jefferson</td>
      <td>C</td>
      <td>Charlotte Hornets</td>
      <td>13.500000</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>368</th>
      <td>DeMar DeRozan</td>
      <td>SG</td>
      <td>Toronto Raptors</td>
      <td>10.050000</td>
    </tr>
    <tr>
      <th>383</th>
      <td>Gordon Hayward</td>
      <td>SF</td>
      <td>Utah Jazz</td>
      <td>15.409570</td>
    </tr>
    <tr>
      <th>400</th>
      <td>John Wall</td>
      <td>PG</td>
      <td>Washington Wizards</td>
      <td>15.851950</td>
    </tr>
    <tr>
      <th>401</th>
      <td>Nene Hilario</td>
      <td>C</td>
      <td>Washington Wizards</td>
      <td>13.000000</td>
    </tr>
    <tr>
      <th>402</th>
      <td>Marcin Gortat</td>
      <td>C</td>
      <td>Washington Wizards</td>
      <td>11.217391</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba.loc[nba['SALARY'] > 10].shape
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">


{:.output_data_text}
```
(69, 4)
```


</div>
</div>
</div>



There are 69 rows in the new DataFrame, corresponding to the 69 players who made more than \\$10 million dollars. Arranging these rows in order makes the data easier to analyze. DeMar DeRozan of the Toronto Raptors was the "poorest" of this group, at a salary of just over \\$10 million dollars.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba.loc[nba['SALARY'] > 10].sort_values(['SALARY'])
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
      <th>368</th>
      <td>DeMar DeRozan</td>
      <td>SG</td>
      <td>Toronto Raptors</td>
      <td>10.050000</td>
    </tr>
    <tr>
      <th>298</th>
      <td>Gerald Wallace</td>
      <td>SF</td>
      <td>Philadelphia 76ers</td>
      <td>10.105855</td>
    </tr>
    <tr>
      <th>204</th>
      <td>Luol Deng</td>
      <td>SF</td>
      <td>Miami Heat</td>
      <td>10.151612</td>
    </tr>
    <tr>
      <th>144</th>
      <td>Monta Ellis</td>
      <td>SG</td>
      <td>Indiana Pacers</td>
      <td>10.300000</td>
    </tr>
    <tr>
      <th>95</th>
      <td>Wilson Chandler</td>
      <td>SF</td>
      <td>Denver Nuggets</td>
      <td>10.449438</td>
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



How much did Stephen Curry make? For the answer, we have to access the row where the value of `PLAYER` is equal to `Stephen Curry`. That is placed in a DataFrame consisting of just one row:



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba.loc[nba['PLAYER'] == 'Stephen Curry']
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



Curry made just under \\$11.4 million dollars. That's a lot of money, but it's less than half the salary of LeBron James. You'll find that salary in the "Top 5" table earlier in this section, or you could find it replacing `'Stephen Curry'` by `'LeBron James'` in the line of code above.

In that code, rather than the "greater than" operator, `>`, we used the "equality" operator, `==`. Thus for example you can alternatively construct a DataFrame of all the Warriors:



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba.loc[nba['TEAM'] == 'Golden State Warriors']
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



This portion of the data is already sorted by salary, because the original data listed players sorted by salary within the same team.



### Multiple Features
You can access rows that have multiple specified features, by using `loc` repeatedly. For example, here is a way to extract all the Point Guards whose salaries were over \\$15 million.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba.loc[nba['POSITION'] == 'PG'].loc[nba['SALARY'] > 15]
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
      <th>60</th>
      <td>Derrick Rose</td>
      <td>PG</td>
      <td>Chicago Bulls</td>
      <td>20.093064</td>
    </tr>
    <tr>
      <th>74</th>
      <td>Kyrie Irving</td>
      <td>PG</td>
      <td>Cleveland Cavaliers</td>
      <td>16.407501</td>
    </tr>
    <tr>
      <th>156</th>
      <td>Chris Paul</td>
      <td>PG</td>
      <td>Los Angeles Clippers</td>
      <td>21.468695</td>
    </tr>
    <tr>
      <th>269</th>
      <td>Russell Westbrook</td>
      <td>PG</td>
      <td>Oklahoma City Thunder</td>
      <td>16.744218</td>
    </tr>
    <tr>
      <th>400</th>
      <td>John Wall</td>
      <td>PG</td>
      <td>Washington Wizards</td>
      <td>15.851950</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



Alternatively, you can combine conditions using Python's "bitwise" operators, `&` and `|`, and pass the resulting specification to a single invocation of `loc`.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba.loc[(nba['POSITION'] == 'PG') & (nba['SALARY'] > 15)]
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
      <th>60</th>
      <td>Derrick Rose</td>
      <td>PG</td>
      <td>Chicago Bulls</td>
      <td>20.093064</td>
    </tr>
    <tr>
      <th>74</th>
      <td>Kyrie Irving</td>
      <td>PG</td>
      <td>Cleveland Cavaliers</td>
      <td>16.407501</td>
    </tr>
    <tr>
      <th>156</th>
      <td>Chris Paul</td>
      <td>PG</td>
      <td>Los Angeles Clippers</td>
      <td>21.468695</td>
    </tr>
    <tr>
      <th>269</th>
      <td>Russell Westbrook</td>
      <td>PG</td>
      <td>Oklahoma City Thunder</td>
      <td>16.744218</td>
    </tr>
    <tr>
      <th>400</th>
      <td>John Wall</td>
      <td>PG</td>
      <td>Washington Wizards</td>
      <td>15.851950</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



Though the above invocation of `loc` was, in a sense, more straight-forward, note that parentheses were required to group our operations; otherwise, Python would have misinterpreted the expression.

Though more verbose, we could make this clearer – and preserve our conditions for reuse – by assigning them names.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba_position_equals_pg = nba['POSITION'] == 'PG'

nba_salary_more_than_15 = nba['SALARY'] > 15

nba.loc[nba_position_equals_pg & nba_salary_more_than_15]
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
      <th>60</th>
      <td>Derrick Rose</td>
      <td>PG</td>
      <td>Chicago Bulls</td>
      <td>20.093064</td>
    </tr>
    <tr>
      <th>74</th>
      <td>Kyrie Irving</td>
      <td>PG</td>
      <td>Cleveland Cavaliers</td>
      <td>16.407501</td>
    </tr>
    <tr>
      <th>156</th>
      <td>Chris Paul</td>
      <td>PG</td>
      <td>Los Angeles Clippers</td>
      <td>21.468695</td>
    </tr>
    <tr>
      <th>269</th>
      <td>Russell Westbrook</td>
      <td>PG</td>
      <td>Oklahoma City Thunder</td>
      <td>16.744218</td>
    </tr>
    <tr>
      <th>400</th>
      <td>John Wall</td>
      <td>PG</td>
      <td>Washington Wizards</td>
      <td>15.851950</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



### General Form

By now you will have realized that the general way to create a new DataFrame by selecting rows with a given feature is to use `loc` with the appropriate Boolean sequence – or "mask" – for our condition(s):

    DATA_FRAME.loc[MASK]
    
Where a "mask" is generated by performing a logical operation on a column of our data:

    DATA_FRAME[COLUMN_LABEL] LOGICAL_OPERATOR CONDITION_VALUE
    
And these masks may be composed:

    MASK0 BITWISE_OPERATOR MASK1



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba.loc[(nba['SALARY'] >= 10) & (nba['SALARY'] < 10.3)]
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
      <th>204</th>
      <td>Luol Deng</td>
      <td>SF</td>
      <td>Miami Heat</td>
      <td>10.151612</td>
    </tr>
    <tr>
      <th>298</th>
      <td>Gerald Wallace</td>
      <td>SF</td>
      <td>Philadelphia 76ers</td>
      <td>10.105855</td>
    </tr>
    <tr>
      <th>356</th>
      <td>Danny Green</td>
      <td>SG</td>
      <td>San Antonio Spurs</td>
      <td>10.000000</td>
    </tr>
    <tr>
      <th>368</th>
      <td>DeMar DeRozan</td>
      <td>SG</td>
      <td>Toronto Raptors</td>
      <td>10.050000</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



Notice that the DataFrame above includes Danny Green who made \\$10 million, but *not* Monta Ellis who made \\$10.3 million. This is because we used the "greater than or equal to" operator, `>=`, with the condition value `10`, and the "strictly less than" operator, `<`, with the condition value 10.3.



If we specify a condition that isn't satisfied by any row, we get a DataFrame with column labels but no rows.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba.loc[nba['PLAYER'] == 'Barack Obama']
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
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



### Some More Conditions

Here are the logical operators in Python, as they apply to conditional selection of data.

| **Logical operator**                | Name                | Description                         |
| --------------------------- | ------------------- | ----------------------------------- |
| `==`                        | Equal to            | True if data cell value is equal to condition value |
| `>`                         | Greater than        | True if data cell value is greater than condition value |
| `>=`                        | Greater than or equal to | True if data cell value is greater than or equal to condition value |
| `<`                         | Less than           | True if data cell value is less than condition value |
| `<=`                        | Less than or equal  | True if data cell value is less than or equal to condition value |

And here are the bitwise operators with which you may combine conditions.

| **Bitwise operator** | Name           | Description                         |
| -------------------- | -------------- | ----------------------------------- |
| `&`                  | Bitwise AND    | True if BOTH conditions are True    |
| `|`                  | Bitwise OR     | True if EITHER condition is True    |



We end the section with a series of examples. 



Another common condition is that a string value *contains* another string. Pandas supports this type of comparision with its own method, `contains`, provided through its `str` property.

This can help save some typing. For example, you can just specify that the team name contains the word `Warriors` instead of that it is exactly equal to the phrase `Golden State Warriors`.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba.loc[nba['TEAM'].str.contains('Warriors')]
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



Or you can extract data for all the guards, both Point Guards and Shooting Guards:



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba.loc[nba['POSITION'].str.contains('G')]
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
      <th>8</th>
      <td>Dennis Schroder</td>
      <td>PG</td>
      <td>Atlanta Hawks</td>
      <td>1.763400</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Tim Hardaway Jr.</td>
      <td>SG</td>
      <td>Atlanta Hawks</td>
      <td>1.304520</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Jason Richardson</td>
      <td>SG</td>
      <td>Atlanta Hawks</td>
      <td>0.947276</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>409</th>
      <td>Alan Anderson</td>
      <td>SG</td>
      <td>Washington Wizards</td>
      <td>4.000000</td>
    </tr>
    <tr>
      <th>411</th>
      <td>Ramon Sessions</td>
      <td>PG</td>
      <td>Washington Wizards</td>
      <td>2.170465</td>
    </tr>
    <tr>
      <th>412</th>
      <td>Gary Neal</td>
      <td>PG</td>
      <td>Washington Wizards</td>
      <td>2.139000</td>
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



Or you can get all the players who were not Cleveland Cavaliers and had a salary of no less than \\$20 million:



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba.loc[(nba['TEAM'] != 'Cleveland Cavaliers') & (nba['SALARY'] >= 20)]
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
      <th>29</th>
      <td>Joe Johnson</td>
      <td>SF</td>
      <td>Brooklyn Nets</td>
      <td>24.894863</td>
    </tr>
    <tr>
      <th>60</th>
      <td>Derrick Rose</td>
      <td>PG</td>
      <td>Chicago Bulls</td>
      <td>20.093064</td>
    </tr>
    <tr>
      <th>131</th>
      <td>Dwight Howard</td>
      <td>C</td>
      <td>Houston Rockets</td>
      <td>22.359364</td>
    </tr>
    <tr>
      <th>156</th>
      <td>Chris Paul</td>
      <td>PG</td>
      <td>Los Angeles Clippers</td>
      <td>21.468695</td>
    </tr>
    <tr>
      <th>169</th>
      <td>Kobe Bryant</td>
      <td>SF</td>
      <td>Los Angeles Lakers</td>
      <td>25.000000</td>
    </tr>
    <tr>
      <th>201</th>
      <td>Chris Bosh</td>
      <td>PF</td>
      <td>Miami Heat</td>
      <td>22.192730</td>
    </tr>
    <tr>
      <th>202</th>
      <td>Dwyane Wade</td>
      <td>SG</td>
      <td>Miami Heat</td>
      <td>20.000000</td>
    </tr>
    <tr>
      <th>255</th>
      <td>Carmelo Anthony</td>
      <td>SF</td>
      <td>New York Knicks</td>
      <td>22.875000</td>
    </tr>
    <tr>
      <th>268</th>
      <td>Kevin Durant</td>
      <td>SF</td>
      <td>Oklahoma City Thunder</td>
      <td>20.158622</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



As you can see, the use of `loc` with conditional masks gives you great flexibility in accessing rows with features that interest you. Don't hesitate to experiment!

