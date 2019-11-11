Lab 10: Regular Expressions
================
Gaston Sanchez

> ### Learning Objectives
> 
>   - String manipulation
>   - Base R functions for strings
>   - Work with the package `"stringr"`
>   - String manipulation
>   - More regular expressions
>   - A bit of data cleaning

### General Instructions

  - Write your descriptions, explanations, and code in an `Rmd` (R
    markdown) file.
  - Name this file as `lab10-first-last.Rmd`, where `first` and `last`
    are your first and last names (e.g. `lab10-gaston-sanchez.Rmd`).
  - Knit your `Rmd` file as an html document (default option).
  - Submit your `Rmd` and `html` files to bCourses, in the corresponding
    lab assignment.
  - Due date displayed in the syllabus (see github repo).

-----

# Part 1) Basics of String Manipulation\*

In this second part of the lab, you will be using the row names of the
data frame `USArrests` (this data comes already in R):

``` r
head(USArrests)
```

    ##            Murder Assault UrbanPop Rape
    ## Alabama      13.2     236       58 21.2
    ## Alaska       10.0     263       48 44.5
    ## Arizona       8.1     294       80 31.0
    ## Arkansas      8.8     190       50 19.5
    ## California    9.0     276       91 40.6
    ## Colorado      7.9     204       78 38.7

``` r
states <- rownames(USArrests)
head(states)
```

    ## [1] "Alabama"    "Alaska"     "Arizona"    "Arkansas"   "California"
    ## [6] "Colorado"

Here are some functions that you may need to use in this lab:

  - `nchar()`
  - `tolower()`
  - `toupper()`
  - `casefold()`
  - `paste()`
  - `paste0()`
  - `substr()`

### Number of characters

`nchar()` allows you to count the number of characters in a string. Use
it on `states` to get the number of characters of each state:

### Case folding

There are 3 functions to do case-folding: `tolower()`, `toupper()`, and
`casefold()`. Apply each function on `states` to see what happens

### Length of State Names

We just saw how to use `nchar()` to count the number of characters in
each state name:

``` r
# number of charcaters
num_chars <- nchar(states)
```

Use the vector `num_chars` to obtain a frequency table called
`char_freqs`, and then plot the frequencies with a bar chart:

### Pasting strings

R provides the `paste()` function. This function allows you to **paste**
(i.e. append, concatenate) character vectors separated by a blank space:

``` r
paste('Pumpkin', 'Pie')
```

    ## [1] "Pumpkin Pie"

You can give it any number of vector inputs

``` r
paste('a', 'b', 'c', 'd', 'e')
```

    ## [1] "a b c d e"

You can change the separator with `sep`

``` r
paste('a', 'b', 'c', 'd', 'e', sep = '-')
```

    ## [1] "a-b-c-d-e"

`paste()` is vectorized:

``` r
paste('a', 1:5, sep = '.')
```

    ## [1] "a.1" "a.2" "a.3" "a.4" "a.5"

There’s a special wrapper around `paste()` called `paste0()` which is
equivalent to `paste(..., sep = "")`

``` r
# paste0() -vs- paste(..., sep = "")
paste0('Pumpkin', 'Pie')
```

    ## [1] "PumpkinPie"

``` r
paste('Pumpkin', 'Pie', sep = '')
```

    ## [1] "PumpkinPie"

``` r
# paste0() is also vectorized
paste0('a', 1:5)
```

    ## [1] "a1" "a2" "a3" "a4" "a5"

### Your Turn\*: `paste()`

Use `paste()` to form a new vector with the first five states and their
number of characters like this:

`"Alabama = 7" "Alaska = 6" "Arizona = 7" "Arkansas = 8" "California
= 10"`

Now use `paste()`’s argument `collapse = ''` to *collapse* the first
five states like this:

`"AlabamaAlaskaArizonaArkansasCalifornia"`

### Your Turn\*: Permutations

Find the number of permutations that can be formed by using all the
given letters in `ALABAMA`. For instance: `"ALAMABA"`, `"AMALABA"`,
`"AAAABML"`.

### Substrings

R provieds the function `substr()` to extract substrings in a character
vector:

``` r
# extract first 3 characters
substr('Berkeley', 1, 3)
```

    ## [1] "Ber"

Use `substr()` to shorten the state names using the first 3-letters:

Use `substr()` to shorten the state names using the last 3-letters:

How would you shorten the state names using the first letter and the
last 3-letters? For instance: `"Aama"` `"Aska"` `"Aona"` `"Asas"` etc.

### Challenge

We already obtained a frequency table `char_freqs` with the counts of
state names by number of characters. You can use those frequencies to
get those state-names with 4-characters or 10-characters:

``` r
# 4-char states
states[num_chars == 4]
```

    ## [1] "Iowa" "Ohio" "Utah"

``` r
# 10-char states
states[num_chars == 10]
```

    ## [1] "California" "New Jersey" "New Mexico" "Washington"

You can use `paste()` to join the 4-character states in one single
string (i.e. *collapsing*) like this—separated by a comma and space—:

``` r
# collapse 4-char states
paste(states[num_chars == 4], collapse = ", ")
```

    ## [1] "Iowa, Ohio, Utah"

Write code (using a for-loop) to obtain a list `states_list` containing
the collapsed names by number of characters. If the number of characters
is an even number, then the state names should be in capital letters.
Otherwise, they should be in lower case letters.

Each list element of `states_list` must be named with the number of
characters, followed by a dash, followed by the word `chars`:
e.g. `'4-chars'`, `'5-chars'`, etc. In total, `states_list` should have
the same length as `char_freqs`.

Here’s what `states_list` should look like for the first three elements:

    $`4-chars`
    [1] "IOWA, OHIO, UTAH"
    
    $`5-chars`
    [1] "idaho, maine, texas"
    
    $`6-chars`
    [1] "ALASKA, HAWAII, KANSAS, NEVADA, OREGON"

-----

# Part 2) Intro to Regular Expressions

In this second part of the lab, we get our first contact with regular
expressions (*aka* regex).

## Data “Emotion in Text”

You’ll be working with the data file `text-emotion.csv` available in the
course github repository.

<https://raw.githubusercontent.com/ucb-stat133/stat133-labs/master/data/text-emotion.csv>

The original source is the data set “Emotion in Text” from the website
Crowd Flower Data for Everyone
<https://www.crowdflower.com/data-for-everyone/>

The file contains four columns:

  - `tweet_id`: tweet identifier
  - `sentiment`: class or sentiment label
  - `author`: username author of the tweet
  - `content`: content of the tweet

**In your `Rmd` file write R code to do computations in order to answer
each of the following questions**

Also, while you work on this lab you may want to look at the cheat
sheets for:

  - [stringr](https://github.com/ucb-stat133/stat133-cheatsheets/blob/master/stringr-cheatsheet.pdf)
  - [regex](https://github.com/ucb-stat133/stat133-cheatsheets/blob/master/regular-expressions-cheatsheet.pdf)

-----

## 1\) Number of characters per tweet\*

  - Count the number of characters in the tweet contents; create a
    vector for this purpose. It is possible that you find tweets
    containing more than 140 characters. This has to do with the
    so-called *predefined XML entities* such as
    
      - `&amp;` which represents an ampersand `&`
      - `&quot;` which represent quotes `"`
      - `&lt;` which represents less-than symbol `<`
      - `&gt;` which represents greater-than symbol `>`

  - Display the `summary()` of the vector obtained above.

  - Likewise, graph a histogram of these counts. To plot the histogram,
    use a bin width of 5 units: 1-5, 6-10, 11-15, 16-20, etc. In other
    words: the first bin involves tweets between 1 and 5 characters
    (inclusive), the second bin involves tweets containing between 6 and
    10 characters (inclusive), and so on.

  - Are there any tweets with 0 characters? (*write a command that
    answers this question*).

  - Are there any tweets with 1 character? If yes (*write commands that
    answer these questions*):
    
      - how many?
      - what is their content?
      - what is their location (i.e. index or position)?

  - What is the tweet with the most characters (i.e. max length)?
    (*write a command that answers these questions*).
    
      - the number of characters
      - display its content
      - what is its location (i.e. index or position)?

-----

## 2\) Author (usernames)\*

According to Twitter, usernames:

  - cannot be longer than 15 characters
  - can only contain alphanumeric characters (letters A-Z, numbers 0-9)
    with the exception of underscores (i.e. cannot contain any symbols,
    dashes or spaces, except underscores)
  - *If you want to know more about twitter usernames, visit:*

<https://help.twitter.com/en/managing-your-account/twitter-username-rules>

Confirm that the values in column `author` follow each of the rules for
valid usernames:

  - No longer than 15 characters *(if you find usernames longer than 15
    characters, display them)*

  - Contain alphanumeric characters and underscores. If you find
    usernames containing other symbols, display them. *Hint*: The
    non-word character class is `"\\W"` is your friend.

  - What is the number of characters of the shortest usernames? And what
    are the names of these authors? *(write commands to answer these
    questions)*

-----

## 3\) Various Symbols and Strings\*

  - How many tweets contain at least one caret symbol `"^"` *(write a
    command to answer this question)*.

  - How many tweets contain three or more consecutive dollar symbols
    `"$"` *(write a command to answer this question)*.

  - How many tweets do NOT contain the characters `"a"` or `"A"` *(write
    a command to answer this question)*.

  - Display the first 10 elements of the tweets that do NOT contain the
    characters `"a"` or `"A"` *(write a command to answer this
    question)*.

  - Number of exclamation symbols `"!"`: compute a vector with the
    number of exclamation symbols in each tweet, and display its
    `summary()`.

  - What’s the tweet (content) with the largest number of exclamation
    symbols `!`? Display its content. *(write a command to answer this
    question)*

-----

## 4\) Sentiment\*

  - What are the different types of sentiments (i.e. categories)?
    (*write a command that answers this question*)

  - Compute the frequencies (i.e. counts) of each sentiment (and display
    these frequencies).

  - Graph the relative frequencies (i.e. proportions) with a horizontal
    barplot (bars horizontally oriented) in decreasing order, including
    names of sentiment types.

  - Sentiment and length of tweets: compute a table with the average
    length of characters per sentiment (i.e. average number of
    characters for `neutral` tweets, for `happy` tweets, etc.). Display
    this table.

-----

## 5\) Optional Challenge: Hashtags

People use the hashtag symbol `#` before a relevant keyword or phrase in
their tweet to categorize those Tweets and help them show more easily in
Twitter search. According to Twitter, hashtags cannot contain spaces or
punctuation symbols, and cannot start with or use only numbers.

  - Count the number of (valid) hashtags in the tweet contents.

  - Display such frequencies, and make a barplot of these counts
    (i.e. number of tweets with 0 hashtags, with 1 hashtag, with 2
    hashtags, etc).

  - What is the average length of the hashtags?

  - What is the most common length (i.e. the mode) of the hashtags?

-----

## 6\) Optional Challenge: OMG

  - How many tweets contain the *individual* strings `"omg"` or `"OMG"`
    *(write a command to answer this question)*. For example:
    
      - `omg I just saw them again` (this would be a match)
      - `OMG I just saw them again` (this would be a match)
      - `I just saw them again omg` (this would be a match)
      - `I just saw them again OMG` (this would be a match)
      - `I just saw them omg can't believe it` (this would be a match)
      - `I just saw them OMG can't believe it` (this would be a match)
      - `omg: I just saw them again` (this would NOT be a match)
      - `OMG,I just saw them again` (this would NOT be a match)
      - `I just saw them again omg!!!` (this would NOT be a match)
      - `I just saw them again omgomgomg` (this would NOT be a match)
      - `I just saw them again lol-omg!!!` (this would NOT be a match)
