---
redirect_from:
  - "/chapters/01/3/plotting-the-classics"
interact_link: content/chapters/01/3/Plotting_the_Classics.ipynb
kernel_name: python3
has_widgets: false
title: 'Plotting the Classics'
prev_page:
  url: /chapters/01/2/why-data-science
  title: 'Why Data Science?'
next_page:
  url: /chapters/01/3/1/Literary_Characters
  title: 'Literary Characters'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---




# Plotting the classics

In this example, we will explore statistics for two classic novels: *The Adventures of Huckleberry Finn* by Mark Twain, and *Little Women* by Louisa May Alcott. The text of any book can be read by a computer at great speed. Books published before 1923 are currently in the *public domain*, meaning that everyone has the right to copy or use the text in any way. [Project Gutenberg](http://www.gutenberg.org/) is a website that publishes public domain books online. Using Python, we can load the text of these books directly from the web.

This example is meant to illustrate some of the broad themes of this text. Don't worry if the details of the program don't yet make sense. Instead, focus on interpreting the images generated below. Later sections of the text will describe most of the features of the Python programming language used below.

First, we read the text of both books into lists of chapters, called `huck_finn_chapters` and `little_women_chapters`. In Python, a name cannot contain any spaces, and so we will often use an underscore `_` to stand in for a space. The `=` in the lines below give a name on the left to the result of some computation described on the right. A *uniform resource locator* or *URL* is an address on the Internet for some content; in this case, the text of a book. The `#` symbol starts a comment, which is ignored by the computer but helpful for people reading the code.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# Read two books, fast!

huck_finn_url = 'https://uchicagods.github.io/textbook/data/huck_finn.txt'
huck_finn_text = read_url(huck_finn_url)
huck_finn_chapters = huck_finn_text.split('CHAPTER ')[44:]

little_women_url = 'https://uchicagods.github.io/textbook/data/little_women.txt'
little_women_text = read_url(little_women_url)
little_women_chapters = little_women_text.split('CHAPTER ')[1:]
```
</div>

</div>



While a computer cannot understand the text of a book, it can provide us with some insight into the structure of the text. The name `huck_finn_chapters` is currently bound to a list of all the chapters in the book. We can place them into a table to see how each chapter begins.



<div markdown="1" class="cell code_cell">
<div class="input_area" markdown="1">
```python
# Display the chapters of Huckleberry Finn in a table.

pd.DataFrame(
    {
        'Chapters': huck_finn_chapters,
    },
    pd.RangeIndex(1, 44),
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
      <td>I. YOU don't know about me without you have re...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>II. WE went tiptoeing along a path amongst the...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>III. WELL, I got a good going-over in the morn...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>IV. WELL, three or four months run along, and ...</td>
    </tr>
    <tr>
      <th>5</th>
      <td>V. I had shut the door to. Then I turned aroun...</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
    </tr>
    <tr>
      <th>39</th>
      <td>XXXIX. IN the morning we went up to the villag...</td>
    </tr>
    <tr>
      <th>40</th>
      <td>XL. WE was feeling pretty good after breakfast...</td>
    </tr>
    <tr>
      <th>41</th>
      <td>XLI. THE doctor was an old man; a very nice, k...</td>
    </tr>
    <tr>
      <th>42</th>
      <td>XLII. THE old man was uptown again before brea...</td>
    </tr>
    <tr>
      <th>43</th>
      <td>THE LAST THE first time I catched Tom private ...</td>
    </tr>
  </tbody>
</table>
</div>
</div>


</div>
</div>
</div>



Each chapter begins with a chapter number in Roman numerals, followed by the first sentence of the chapter. Project Gutenberg has printed the first word of each chapter in upper case. 

