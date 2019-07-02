---
redirect_from:
  - "/chapters/01/3/1/literary-characters"
interact_link: content/chapters/01/3/1/Literary_Characters.ipynb
kernel_name: python3
has_widgets: false
title: 'Literary Characters'
prev_page:
  url: /chapters/01/3/Plotting_the_Classics
  title: 'Plotting the Classics'
next_page:
  url: /chapters/01/3/2/Another_Kind_Of_Character
  title: 'Another Kind of Character'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---






# Literary Characters

*The Adventures of Huckleberry Finn* describes a journey that Huck and Jim take along the Mississippi River. Tom Sawyer joins them towards the end as the action heats up. Having loaded the text, we can quickly visualize how many times these characters have each been mentioned at any point in the book.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# Count how many times the names Jim, Tom, and Huck appear in each chapter.

name_counts = pd.DataFrame(
    {
        'Jim': np.char.count(huck_finn_chapters, 'Jim'),
        'Tom': np.char.count(huck_finn_chapters, 'Tom'),
        'Huck': np.char.count(huck_finn_chapters, 'Huck'),
    },
    pd.RangeIndex(1, 44, name='Chapter'),
)


# Plot the cumulative counts:
# how many times in Chapter 1, how many times in Chapters 1 and 2, and so on.

name_cumulative = name_counts.cumsum()
name_cumulative.plot(title='Cumulative Number of Times Each Name Appears');
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">

{:.output_png}
![png](../../../../images/chapters/01/3/1/Literary_Characters_3_0.png)

</div>
</div>
</div>



In the plot above, the horizontal axis shows chapter numbers and the vertical axis shows how many times each character has been mentioned up to and including that chapter. 

You can see that Jim is a central character by the large number of times his name appears. Notice how Tom is hardly mentioned for much of the book until he arrives and joins Huck and Jim, after Chapter 30. His curve and Jim's rise sharply at that point, as the action involving both of them intensifies. As for Huck, his name hardly appears at all, because he is the narrator. 



*Little Women* is a story of four sisters growing up together during the civil war. In this book, chapter numbers are spelled out and chapter titles are written in all capital letters.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# The chapters of Little Women, in a table

pd.DataFrame(
    {
        'Chapters': little_women_chapters,
    },
    pd.RangeIndex(1, 48),
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
      <th>Chapters</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>ONE\n\nPLAYING PILGRIMS\n\n"Christmas won't be...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>TWO\n\nA MERRY CHRISTMAS\n\nJo was the first t...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>THREE\n\nTHE LAURENCE BOY\n\n"Jo!  Jo!  Where ...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>FOUR\n\nBURDENS\n\n"Oh, dear, how hard it does...</td>
    </tr>
    <tr>
      <th>5</th>
      <td>FIVE\n\nBEING NEIGHBORLY\n\n"What in the world...</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
    </tr>
    <tr>
      <th>43</th>
      <td>FORTY-THREE\n\nSURPRISES\n\nJo was alone in th...</td>
    </tr>
    <tr>
      <th>44</th>
      <td>FORTY-FOUR\n\nMY LORD AND LADY\n\n"Please, Mad...</td>
    </tr>
    <tr>
      <th>45</th>
      <td>FORTY-FIVE\n\nDAISY AND DEMI\n\nI cannot feel ...</td>
    </tr>
    <tr>
      <th>46</th>
      <td>FORTY-SIX\n\nUNDER THE UMBRELLA\n\nWhile Lauri...</td>
    </tr>
    <tr>
      <th>47</th>
      <td>FORTY-SEVEN\n\nHARVEST TIME\n\nFor a year Jo a...</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



We can track the mentions of main characters to learn about the plot of this book as well.  The protagonist Jo interacts with her sisters Meg, Beth, and Amy regularly, up until Chapter 27 when she moves to New York alone.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# Counts of names in the chapters of Little Women

name_counts = pd.DataFrame(
    {
        'Amy': np.char.count(little_women_chapters, 'Amy'),
        'Beth': np.char.count(little_women_chapters, 'Beth'),
        'Jo': np.char.count(little_women_chapters, 'Jo'),
        'Meg': np.char.count(little_women_chapters, 'Meg'),
        'Laurie': np.char.count(little_women_chapters, 'Laurie'),
    },
    pd.RangeIndex(1, 48, name='Chapter'),
)

# Plot the cumulative counts.

name_cumulative = name_counts.cumsum()
name_cumulative.plot(title='Cumulative Number of Times Each Name Appears');
```
</div>

<div class="output_wrapper" markdown="1">
<div class="output_subarea" markdown="1">

{:.output_png}
![png](../../../../images/chapters/01/3/1/Literary_Characters_8_0.png)

</div>
</div>
</div>



Laurie is a young man who marries one of the girls in the end. See if you can use the plots to guess which one.

