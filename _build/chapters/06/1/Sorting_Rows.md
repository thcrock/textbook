---
redirect_from:
  - "/chapters/06/1/sorting-rows"
interact_link: content/chapters/06/1/Sorting_Rows.ipynb
kernel_name: python3
has_widgets: false
title: 'Sorting Rows'
prev_page:
  url: /chapters/06/DataFrames
  title: 'DataFrames'
next_page:
  url: /chapters/06/2/Selecting_Rows
  title: 'Selecting Rows'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---




# Sorting Rows

"The NBA is the highest paying professional sports league in the world," [reported CNN](http://edition.cnn.com/2015/12/04/sport/gallery/highest-paid-nba-players/) in March 2016. The DataFrame `nba_salaries` will contain the salaries of all National Basketball Association players in 2015-2016.

Each row represents one player. The columns are:

| **Column Label**   | Description                                         |
|--------------------|-----------------------------------------------------|
| `PLAYER`           | Player's name                                       |
| `POSITION`         | Player's position on team                           |
| `TEAM`             | Team name                                           |
|`'15-'16 SALARY`    | Player's salary in 2015-2016, in millions of dollars|
 
The code for the positions is PG (Point Guard), SG (Shooting Guard), PF (Power Forward), SF (Small Forward), and C (Center). But what follows doesn't involve details about how basketball is played.

The first row shows that Paul Millsap, Power Forward for the Atlanta Hawks, had a salary of almost $\$18.7$ million in 2015-2016.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# These data can be found online: https://www.statcrunch.com/app/index.php?dataid=1843341

nba_salaries = pd.read_csv(PATH_DATA / 'nba_salaries.csv')

nba_salaries
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
      <th>'15-'16 SALARY</th>
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



The data contain 417 rows, one for each player. Pandas has been configured to show only 10 of the rows by default, (the first and last 5).

The `head` method allows us to specify a number of rows, starting from the "head" or beginning of the data, with the default (no specification) being 5 rows of data.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba_salaries.head(3)
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
      <th>'15-'16 SALARY</th>
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
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



Alternatively, we may inspect the "tail" of the data.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba_salaries.tail(3)
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
      <th>'15-'16 SALARY</th>
    </tr>
  </thead>
  <tbody>
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



Finally, if necessary, we may even tweak a Pandas configuration temporarily.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
with pd.option_context('display.max_rows', 20):
    nba_salaries.head(20)
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
      <th>'15-'16 SALARY</th>
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
      <th>5</th>
      <td>Thabo Sefolosha</td>
      <td>SF</td>
      <td>Atlanta Hawks</td>
      <td>4.000000</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Mike Scott</td>
      <td>PF</td>
      <td>Atlanta Hawks</td>
      <td>3.333333</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Kent Bazemore</td>
      <td>SF</td>
      <td>Atlanta Hawks</td>
      <td>2.000000</td>
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
      <th>10</th>
      <td>Walter Tavares</td>
      <td>C</td>
      <td>Atlanta Hawks</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Jason Richardson</td>
      <td>SG</td>
      <td>Atlanta Hawks</td>
      <td>0.947276</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Lamar Patterson</td>
      <td>SG</td>
      <td>Atlanta Hawks</td>
      <td>0.525093</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Terran Petteway</td>
      <td>SG</td>
      <td>Atlanta Hawks</td>
      <td>0.525093</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Avery Bradley</td>
      <td>PG</td>
      <td>Boston Celtics</td>
      <td>7.730337</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Isaiah Thomas</td>
      <td>PG</td>
      <td>Boston Celtics</td>
      <td>6.912869</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Jae Crowder</td>
      <td>SF</td>
      <td>Boston Celtics</td>
      <td>6.796117</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Jonas Jerebko</td>
      <td>PF</td>
      <td>Boston Celtics</td>
      <td>5.000000</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Marcus Smart</td>
      <td>PG</td>
      <td>Boston Celtics</td>
      <td>3.431040</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Evan Turner</td>
      <td>SG</td>
      <td>Boston Celtics</td>
      <td>3.425510</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



Judging by the above, the data appear to be in alphabetical order by team name. It's also possible to list the same rows in alphabetical order by player name using the `sort_values` method. The first argument to `sort_values` is a sequence of column labels.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba_salaries.sort_values(['PLAYER'])
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
      <th>'15-'16 SALARY</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>68</th>
      <td>Aaron Brooks</td>
      <td>PG</td>
      <td>Chicago Bulls</td>
      <td>2.250000</td>
    </tr>
    <tr>
      <th>291</th>
      <td>Aaron Gordon</td>
      <td>PF</td>
      <td>Orlando Magic</td>
      <td>4.171680</td>
    </tr>
    <tr>
      <th>59</th>
      <td>Aaron Harrison</td>
      <td>SG</td>
      <td>Charlotte Hornets</td>
      <td>0.525093</td>
    </tr>
    <tr>
      <th>235</th>
      <td>Adreian Payne</td>
      <td>PF</td>
      <td>Minnesota Timberwolves</td>
      <td>1.938840</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Al Horford</td>
      <td>C</td>
      <td>Atlanta Hawks</td>
      <td>12.000000</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>95</th>
      <td>Wilson Chandler</td>
      <td>SF</td>
      <td>Denver Nuggets</td>
      <td>10.449438</td>
    </tr>
    <tr>
      <th>233</th>
      <td>Zach LaVine</td>
      <td>PG</td>
      <td>Minnesota Timberwolves</td>
      <td>2.148360</td>
    </tr>
    <tr>
      <th>181</th>
      <td>Zach Randolph</td>
      <td>PF</td>
      <td>Memphis Grizzlies</td>
      <td>9.638555</td>
    </tr>
    <tr>
      <th>86</th>
      <td>Zaza Pachulia</td>
      <td>C</td>
      <td>Dallas Mavericks</td>
      <td>5.200000</td>
    </tr>
    <tr>
      <th>26</th>
      <td>Zoran Dragic</td>
      <td>SG</td>
      <td>Boston Celtics</td>
      <td>1.706225</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



To examine the players' salaries, it would be much more helpful if the data were ordered by salary.

To do this, we will first simplify the label of the column of salaries (just for convenience), and then sort by the new label `SALARY`. 

This arranges all the rows of the table in *increasing* (or "ascending") order of salary, with the lowest salary appearing first. The output is a new DataFrame with the same columns as the original but with the rows rearranged.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba = nba_salaries.rename(
    columns={
        "'15-'16 SALARY": 'SALARY',
    },
)

nba.sort_values(['SALARY'])
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



These figures are somewhat difficult to compare as some of these players changed teams during the season and received salaries from more than one team; only the salary from the last team appears in the table. Point Guard Phil Pressey, for example, moved from Philadelphia to Phoenix during the year, and might be moving yet again to the Golden State Warriors. 

The CNN report is about the other end of the salary scale – the players who are among the highest paid in the world. 

To order the rows of the table in *decreasing* order of salary, we must use `sort_values` with the option `ascending=False`.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
nba.sort_values(['SALARY'], ascending=False)
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
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>200</th>
      <td>Elliot Williams</td>
      <td>SG</td>
      <td>Memphis Grizzlies</td>
      <td>0.055722</td>
    </tr>
    <tr>
      <th>324</th>
      <td>Orlando Johnson</td>
      <td>SG</td>
      <td>Phoenix Suns</td>
      <td>0.055722</td>
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
      <th>267</th>
      <td>Thanasis Antetokounmpo</td>
      <td>SF</td>
      <td>New York Knicks</td>
      <td>0.030888</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



Kobe Bryant, in his final season with the Lakers, was the highest paid at a salary of $\$25$ million. Notice that the MVP Stephen Curry doesn't appear among the top 10. He is quite a bit further down the list, as we will see later.



### Named Arguments

The `ascending=False` portion of this call expression is called a *named argument*. When a function or method is called, each argument has both a position and a name. Both are evident from the help text of a function or method.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
help(nba.sort_values)
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">
{:.output_stream}
```
Help on method sort_values in module pandas.core.frame:

sort_values(by, axis=0, ascending=True, inplace=False, kind='quicksort', na_position='last') method of pandas.core.frame.DataFrame instance
    Sort by the values along either axis
    
    Parameters
    ----------
            by : str or list of str
                Name or list of names to sort by.
    
                - if `axis` is 0 or `'index'` then `by` may contain index
                  levels and/or column labels
                - if `axis` is 1 or `'columns'` then `by` may contain column
                  levels and/or index labels
    
                .. versionchanged:: 0.23.0
                   Allow specifying index or column level names.
    axis : {0 or 'index', 1 or 'columns'}, default 0
         Axis to be sorted
    ascending : bool or list of bool, default True
         Sort ascending vs. descending. Specify list for multiple sort
         orders.  If this is a list of bools, must match the length of
         the by.
    inplace : bool, default False
         if True, perform operation in-place
    kind : {'quicksort', 'mergesort', 'heapsort'}, default 'quicksort'
         Choice of sorting algorithm. See also ndarray.np.sort for more
         information.  `mergesort` is the only stable algorithm. For
         DataFrames, this option is only applied when sorting on a single
         column or label.
    na_position : {'first', 'last'}, default 'last'
         `first` puts NaNs at the beginning, `last` puts NaNs at the end
    
    Returns
    -------
    sorted_obj : DataFrame
    
    Examples
    --------
    >>> df = pd.DataFrame({
    ...     'col1' : ['A', 'A', 'B', np.nan, 'D', 'C'],
    ...     'col2' : [2, 1, 9, 8, 7, 4],
    ...     'col3': [0, 1, 9, 4, 2, 3],
    ... })
    >>> df
        col1 col2 col3
    0   A    2    0
    1   A    1    1
    2   B    9    9
    3   NaN  8    4
    4   D    7    2
    5   C    4    3
    
    Sort by col1
    
    >>> df.sort_values(by=['col1'])
        col1 col2 col3
    0   A    2    0
    1   A    1    1
    2   B    9    9
    5   C    4    3
    4   D    7    2
    3   NaN  8    4
    
    Sort by multiple columns
    
    >>> df.sort_values(by=['col1', 'col2'])
        col1 col2 col3
    1   A    1    1
    0   A    2    0
    2   B    9    9
    5   C    4    3
    4   D    7    2
    3   NaN  8    4
    
    Sort Descending
    
    >>> df.sort_values(by='col1', ascending=False)
        col1 col2 col3
    4   D    7    2
    5   C    4    3
    2   B    9    9
    0   A    2    0
    1   A    1    1
    3   NaN  8    4
    
    Putting NAs first
    
    >>> df.sort_values(by='col1', ascending=False, na_position='first')
        col1 col2 col3
    3   NaN  8    4
    4   D    7    2
    5   C    4    3
    2   B    9    9
    0   A    2    0
    1   A    1    1

```
</div>
</div>
</div>



At the very top of this `help` text, the *signature* of the `sort_values` method appears:

    sort_values(by, axis=0, ascending=True, inplace=False, kind='quicksort', na_position='last')

This describes the positions, names, and default values of the six arguments to `sort_values`. When calling this method, you can use either positional arguments or named arguments, so the following three calls do exactly the same thing.

    sort_values(['SALARY'], 0, False)
    sort_values(['SALARY'], ascending=False)
    sort_values(by=['SALARY'], ascending=False)

When an argument is simply `True` or `False`, it's a useful convention to include the argument name so that it's more obvious what the argument value means.

