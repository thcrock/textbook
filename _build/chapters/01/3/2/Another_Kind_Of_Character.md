---
redirect_from:
  - "/chapters/01/3/2/another-kind-of-character"
interact_link: content/chapters/01/3/2/Another_Kind_Of_Character.ipynb
kernel_name: python3
has_widgets: false
title: 'Another Kind of Character'
prev_page:
  url: /chapters/01/3/1/Literary_Characters
  title: 'Literary Characters'
next_page:
  url: /chapters/02/causality-and-experiments
  title: 'Causality and Experiments'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---






# Another Kind of Character

In some situations, the relationships between quantities allow us to make predictions. This text will explore how to make accurate predictions based on incomplete information and develop methods for combining multiple sources of uncertain information to make decisions.

As an example of visualizing information derived from multiple sources, let us first use the computer to get some information that would be tedious to acquire by hand. In the context of novels, the word "character" has a second meaning: a printed symbol such as a letter or number or punctuation symbol. Here, we ask the computer to count the number of characters and the number of periods in each chapter of both *Huckleberry Finn* and *Little Women*.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# In each chapter, count the number of all characters;
# call this the "length" of the chapter.
# Also count the number of periods.

def NaturalIndex(sequence, **kwargs):
    """Construct a Pandas RangeIndex appropriate to the given sequence."""
    return pd.RangeIndex(1, len(sequence) + 1, **kwargs)


chars_periods_huck_finn = pd.DataFrame(
    {
        'Chapter Length': [len(chapter) for chapter in huck_finn_chapters],
        'Number of Periods': [chapter.count('.') for chapter in huck_finn_chapters],
    },
    NaturalIndex(huck_finn_chapters, name='Huck Finn Chapter'),
)

chars_periods_little_women = pd.DataFrame(
    {
        'Chapter Length': [len(chapter) for chapter in little_women_chapters],
        'Number of Periods': [chapter.count('.') for chapter in little_women_chapters],
    },
    NaturalIndex(little_women_chapters, name='Little Women Chapter'),
)
```
</div>

</div>



Here are the data for *Huckleberry Finn*. Each row of the table corresponds to one chapter of the novel and displays the number of characters as well as the number of periods in the chapter. Not surprisingly, chapters with fewer characters also tend to have fewer periods, in general: the shorter the chapter, the fewer sentences there tend to be, and vice versa. The relation is not entirely predictable, however, as sentences are of varying lengths and can involve other punctuation such as question marks. 



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
chars_periods_huck_finn
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
      <th>Chapter Length</th>
      <th>Number of Periods</th>
    </tr>
    <tr>
      <th>Huck Finn Chapter</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>7088</td>
      <td>66</td>
    </tr>
    <tr>
      <th>2</th>
      <td>12113</td>
      <td>117</td>
    </tr>
    <tr>
      <th>3</th>
      <td>8612</td>
      <td>72</td>
    </tr>
    <tr>
      <th>4</th>
      <td>6892</td>
      <td>84</td>
    </tr>
    <tr>
      <th>5</th>
      <td>8269</td>
      <td>91</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>39</th>
      <td>10962</td>
      <td>96</td>
    </tr>
    <tr>
      <th>40</th>
      <td>11632</td>
      <td>60</td>
    </tr>
    <tr>
      <th>41</th>
      <td>13545</td>
      <td>77</td>
    </tr>
    <tr>
      <th>42</th>
      <td>15901</td>
      <td>92</td>
    </tr>
    <tr>
      <th>43</th>
      <td>21880</td>
      <td>228</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



Here are the corresponding data for *Little Women*.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
chars_periods_little_women
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
      <th>Chapter Length</th>
      <th>Number of Periods</th>
    </tr>
    <tr>
      <th>Little Women Chapter</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>21952</td>
      <td>189</td>
    </tr>
    <tr>
      <th>2</th>
      <td>22384</td>
      <td>188</td>
    </tr>
    <tr>
      <th>3</th>
      <td>20815</td>
      <td>231</td>
    </tr>
    <tr>
      <th>4</th>
      <td>25689</td>
      <td>195</td>
    </tr>
    <tr>
      <th>5</th>
      <td>23657</td>
      <td>255</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>43</th>
      <td>33481</td>
      <td>305</td>
    </tr>
    <tr>
      <th>44</th>
      <td>10383</td>
      <td>95</td>
    </tr>
    <tr>
      <th>45</th>
      <td>12646</td>
      <td>96</td>
    </tr>
    <tr>
      <th>46</th>
      <td>27691</td>
      <td>234</td>
    </tr>
    <tr>
      <th>47</th>
      <td>41377</td>
      <td>392</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



You can see that the chapters of *Little Women* are in general longer than those of *Huckleberry Finn*. Let us see if these two simple variables – the length and number of periods in each chapter – can tell us anything more about the two books. One way to do this is to plot both sets of data on the same axes. 

In the plot below, there is a dot for each chapter in each book. Blue dots correspond to *Huckleberry Finn* and gold dots to *Little Women*. The horizontal axis represents the number of periods and the vertical axis represents the number of characters.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
chars_periods_plot = chars_periods_huck_finn.plot.scatter(
    x='Number of Periods',
    y='Chapter Length',
    color='darkblue',
    label='Huck Finn',
    figsize=(8, 8),
)

chars_periods_little_women.plot.scatter(
    x='Number of Periods',
    y='Chapter Length',
    color='gold',
    label='Little Women',
    ax=chars_periods_plot,
)

chars_periods_plot.set_xlabel('Number of periods in chapter')
chars_periods_plot.set_ylabel('Number of characters in chapter');
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">

{:.output_png}
![png](../../../../images/chapters/01/3/2/Another_Kind_Of_Character_9_0.png)

</div>
</div>
</div>



The plot shows us that many but not all of the chapters of *Little Women* are longer than those of *Huckleberry Finn*, as we had observed by just looking at the numbers. But it also shows us something more. Notice how the blue points are roughly clustered around a straight line, as are the yellow points. Moreover, it looks as though both colors of points might be clustered around the *same* straight line.



Now look at all the chapters that contain about 100 periods. The plot shows that those chapters contain about 10,000 characters to about 15,000 characters, roughly. That's about 100 to 150 characters per period.

Indeed, it appears from looking at the plot that on average both books tend to have somewhere between 100 and 150 characters between periods, as a very rough estimate. Perhaps these two great 19th century novels were signaling something so very familiar to us now: the 140-character limit of Twitter.

