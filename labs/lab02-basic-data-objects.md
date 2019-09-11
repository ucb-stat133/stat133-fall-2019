Lab 2: Basic Data Objects
================
Gaston Sanchez

> ### Learning Objectives
>
> -   Work with vectors of different data types
> -   Understand the concept of *atomic* structures
> -   Learn how to subset and slice R vectors
> -   Understand the concept of *vectorization*
> -   Understand *recycling* rules in R

### General Instructions

-   Write your descriptions, explanations, and code in an `Rmd` (R markdown) file.
-   Name this file as `lab02-first-last.Rmd`, where `first` and `last` are your first and last names (e.g. `lab02-gaston-sanchez.Rmd`).
-   Knit your `Rmd` file as an html document (default option).
-   Submit your `Rmd` and `html` files to bCourses, in the corresponding lab assignment.

------------------------------------------------------------------------

Dataset `"starwars"`
--------------------

In this lab, you are going to work with the dataset `starwars` from the R package `"dplyr"`. So, the first step is to install `"dplyr"`:

``` r
# run this command on the console
# (do NOT include this chunk in your Rmd)

# remove existing objects
rm(list = ls())

# install dplyr (you just need to install this once!)
install.packages("dplyr")
```

Once tha package has been installed, now you should be able to load it, and have access to `starwars` (we'll work with columns `name`, `height`, `mass`, `gender`, and `homeworld`):

``` r
# include this chunk in your Rmd
library(dplyr)
data(starwars)
starwars <- na.omit(starwars[ ,c(1,2,3,8,9)])
```

To learn more about the data look at its documentation

``` r
help(starwars)
```

### Vectors

Let's create some some vectors to play with:

``` r
name <- starwars$name

height <- starwars$height

mass <- starwars$mass

gender <- starwars$gender

homeworld <- starwars$homeworld
```

------------------------------------------------------------------------

### Your turn: subsetting vectors

Create a vector `four` by selecting the first four elements in `name`:

``` r
four <- head(name, n = 4)
```

Single brackets `[ ]` are used to subset (i.e. subscript, split, slice) vectors. Without running the code, try to guess the output of the following commands, and then run them to check your guess:

-   number one: `four[1]`
-   an index of zero: `four[0]`?
-   a negative index: `four[-1]`?
-   various negative indices: `four[-c(1,2,3)]`?
-   an index greater than the length of the vector: `four[5]`?
-   repeated indices: `four[c(1,2,2,3,3,3)]`?

Often, you will need to generate vectors of numeric sequences, like the first five elements `1:5`, or from the first till the last element `1:length(player)`. R provides the colon operator `:`, and the functions `seq()`, and `rep()` to create various types of sequences.

### Your turn: sequences and repetitions

Figure out how to use `seq()`, `rep()`, and bracket notation, to extract:

-   all the even elements in `name`
-   all the odd elements in `height`
-   all multiples of 5 (e.g. 5, 10, 15, etc) of `gender`
-   elements in positions 10, 20, 30, 40, etc of `mass`
-   all the even elements in `name` but this time in reverse order

------------------------------------------------------------------------

Logical Subsetting and Comparisons
----------------------------------

Another kind of subsetting/subscripting style is the so-called **logical subsetting**. This kind of subsetting typically takes place when making comparisons. A **comparison operation** occurs when you use comparison operators such as:

-   `>` greater than
-   `>=` greater than or equal
-   `<` less than
-   `<=` less than or equal
-   `==` equal
-   `!=` different

For example:

``` r
height_four <- height[1:4]

# elements greater than 100
height_four[height_four > 100]

# elements less than 100
height_four[height_four < 100]

# elements less than or equal to 10
height_four[height_four <= 10]

# elements different from 10
height_four[height_four != 10]
```

In addition to using comparison operators, you can also use **logical operators** to produce a logical vector. The most common type of logical operators are:

-   `&` AND
-   `|` OR
-   `!` negation

Run the following commands to see what R does:

``` r
# AND
TRUE & TRUE
TRUE & FALSE
FALSE & FALSE

# OR
TRUE | TRUE
TRUE | FALSE
FALSE | FALSE

# NOT
!TRUE
!FALSE
```

Logical operators allow you to combine several comparisons:

``` r
# vectors for first 10 elements
name10 <- name[1:10]
height10 <- height[1:10]
mass10 <- mass[1:10]
gender10 <- gender[1:10]

# names of first 10 individuals with mass greater than 70kg
name10[mass10 > 70]

# names of first 10 individuals with heights between 150 and 200 (exclusive)
name10[height10 > 150 & height10 < 200]
```

### Your turn: logical subsetting

Write commands, using bracket notation, to answer the following questions (you may need to use `is.na()`, `min()`, `max()`, `which()`, `which.min()`, `which.max()`):

-   name of individuals from homeworld Naboo
-   name of individuals from homeworlds Naboo or Corellia
-   name of female individuals
-   name of individuals with largest mass
-   gender of tallest individual
-   gender of individual with smallest mass
-   largest height of all females
-   name of individual(s) with height equal to the median height
-   name of individual(s) with height of at most 180, and mass of at least 120

------------------------------------------------------------------------

Factors
-------

As mentioned before, vectors are the most essential type of data structure in R. They are *atomic* structures (can contain only one type of data): integers, real numbers, logical values, characters, complex numbers.

Related to vectors, there is another important data structure in R called **factor**. Factors are data structures exclusively designed to handle categorical data.

### Creating Factors

Use `factor()` to create an object `gender_fac` by converting `gender` into a factor:

``` r
gender_fac <- factor(gender)
```

If you have a factor, you can invoke `table()` to get a table with the frequencies (i.e. counts) of the factor categories or *levels*:

``` r
table(gender_fac)
```

    ## gender_fac
    ##        female hermaphrodite          male 
    ##            10             1            42

### Your turn: Manipulating Factors

Because factors are internally stored as integers, you can manipulate factors as any other vector:

``` r
gender_fac[1:5]
```

    ## [1] male   male   female male   female
    ## Levels: female hermaphrodite male

Practice manipulating `gender_fac` to get:

-   gender of individuals from homeworld Naboo
-   gender of individuals with mass &gt; 80 kg
-   frequencies (counts) of gender with height &gt; 180
-   frequencies (counts) of 'male' in each homeworld

------------------------------------------------------------------------

Matrices
--------

As we saw in lecture, a vector can be extended into a 2-dimensional object in the form of a **matrix** (which is a 2-dimensional array).

For instance, let's create a matrix with the `height` and `mass` values of the first five individuals:

``` r
# matrix with height and mass of first 5 individuals
HM <- matrix(c(height[1:5], mass[1:5]), nrow = 5, ncol = 2)
HM
```

    ##      [,1] [,2]
    ## [1,]  172   77
    ## [2,]  202  136
    ## [3,]  150   49
    ## [4,]  178  120
    ## [5,]  165   75

You can give names to rows and columns with the functions `rownames()` and `colnames()`:

``` r
rownames(HM) <- name[1:5]
colnames(HM) <- c("height", "mass")
HM
```

    ##                    height mass
    ## Luke Skywalker        172   77
    ## Darth Vader           202  136
    ## Leia Organa           150   49
    ## Owen Lars             178  120
    ## Beru Whitesun lars    165   75

### Your Turn

-   Use the column-binding function `cbind()` to create a matrix `MH` with columns `mass` and `height`, for the first 10 individuals.

-   Use the function `matrix()` to create a matrix `females` with `mass` and `height` values for female individuals.

-   Give names to the rows and columns of the matrix `females` created above.

-   Repeat the previous two steps to create a matrix `males`.

-   Use the function `rbind()` to bind the first 5 rows of both `females` and `males`, name this object `FM`.

-   Extract the last row of `FM`

-   Display `FM` but with rows in reversed order

-   Display `FM` but now with height in 1st column, and mass in 2nd column

-   If you create a matrix `MHW` by combining `mass`, `height` and `homeworld` for all individuals, what is the resulting data type of `MHW`

------------------------------------------------------------------------

Data Frames
-----------

In this part of the lab assignment you will have to use the data frame `starwars`. In other words, do NOT use any of the vectors or matrices created at the beginning of this session.

### Basic functions to explore data frames

Here's a list of common functions used to get information about a data frame. Look at their documentation, and begin learning what they do by running them on `starwars`:

-   `str()`
-   `dim()`
-   `nrow()` and `ncol()`
-   `head()` and `tail()`
-   `summary()`

### Your Turn

Manipulate `starwars`---using bracket notation---in order to perform the following tasks (btw: ideally you should write one command for each task):

-   select the first row

-   select the columns `name` and `homeworld` for the first 5 individuals

-   select Han Solo's information (i.e. row)

-   select subject's info with smallest height

-   get the dataset of female subjects

-   get the dataset for those female subjects with mass less than 50

-   get the gender and homeworld for those subjects with height less than 160

-   display the first 8 rows of `starwars` by reordering the content by `name` alphabetically

-   add a new column `height_mass` to `starwars` containing the product of `height` and `mass`
