Lab 7: Programming Part 1
================
Gaston Sanchez

> ### Learning Objectives
> 
>   - Learn how to write simple functions
>   - Get into the habit of writing simple functions
>   - Get into the habit of documenting functions
>   - Use conditionals if-then-else
>   - Practice writing simple loops
>   - Get familiar with the syntax of a `for` loop

### General Instructions

  - Write your descriptions, explanations, and code in an `Rmd` (R
    markdown) file.
  - Name this file as `lab07-first-last.Rmd`, where `first` and `last`
    are your first and last names (e.g. `lab07-gaston-sanchez.Rmd`).
  - Knit your `Rmd` file as an html document (default option).
  - Submit your `Rmd` and `html` files to bCourses, in the corresponding
    lab assignment.

-----

## Introduction

In this lab you will practice writing simple functions, and some basic
examples to make sure that the functions work as expected. Later in the
course we will see how to write assertions (i.e. tests) for your
functions in a more formal way.

In addition to writing the functions, you should also practice
documenting your functions. Writing this type of documentation should
become second nature. To do this, include roxygen comments such as:

  - `#' @title Name of your function`
  - `#' @description What the function does`
  - `#' @param x input(s) of your function`
  - `#' @return output of your function`

### Before you start …

If you use an `Rmd` file to write narrative and code for this practice,
you must include a code chunk at the top of your file like the one in
the following screen
capture:

<img src="lab07-images/error-true.png" width="70%" style="display: block; margin: auto;" />

By setting the global option `error = TRUE` you avoid the knitting
process to be stopped in case a code chunk generates an error.

Since you willl be writing a couple of functions with `stop()`
statements, it is essential that you set up `error = TRUE`, otherwise
`"knitr"` will stop knitting your `Rmd` file if it encounters an error.

### Toy Example

Here’s an example of a function `rect_area()` that computes the area of
a rectangle. Notice the structure of the code below: the first lines
correspond to the documentation of the function using Roxygen comments;
and then you have the actual code of the function `rect_area()`:

``` r
#' @title area of rectangle
#' @description calculates the area of a rectangle
#' @param len length of the rectangle (numeric)
#' @param wid width of the rectangle (numeric)
#' @return computed area
rect_area <- function(len = 1, wid = 1) {
  if (len < 0) {
    stop("len must be positive")
  }
  if (wid < 0) {
    stop("wid must be positive")
  }
  area <- len * wid
  return(area)
}
```

Once the function has been created, we can test it with a couple of
basic examples:

``` r
# default
rect_area()
```

    ## [1] 1

``` r
# len=2, wid=3
rect_area(len = 2, wid = 3)
```

    ## [1] 6

``` r
# bad len
rect_area(len = -2, wid = 3)
```

    ## Error in rect_area(len = -2, wid = 3): len must be positive

-----

## Your Turn: Simple Math Functions

Consider the following mathematical functions:

  - \(f(x) = x^2\)
  - \(g(x) = 2x + 5\)

Write two functions `f()` and `g()` based on the previous equations.
Don’t forget to include roxygen comments to document your function\!

Test your functions with:

``` r
f(2)     # 4
f(-5)    # 25

g(0)     # 5
g(-5/2)  # 0
```

Use your functions `f()` and `g()` to create the following composite
functions:

  - `fog()` for the composite function: \(f \circ g(x)\)
  - `gof()` for the composite function: \(g \circ f(x)\)

Test your composite functions with:

``` r
fog(2)     # 81
fog(-5)    # 25

gof(0)     # 5
gof(-5/2)  # 17.5
```

-----

## Your Turn: Pythagoras

The pythagoras formula is used to compute the length of the hypotenuse,
\(c\), of a right triangle with legs of length \(a\) and
\(b\).

![hypotenuse](https://wikimedia.org/api/rest_v1/media/math/render/svg/5fd521cee81d583ce94bf6710984cc2a9eb7c3da)

Write a function `pythagoras()` that takes two arguments `a` and `b`,
and returns the length of the hypotenuse. Don’t forget to include
roxygen comments to document your function\!

Test your `pythagoras()` with two leg values: `pythagoras(3, 4)`

Modify your function `pythagoras()` so that argument `b` takes the same
value of argument `a`. Test it with just one leg value: `pythagoras(5)`

-----

## Your Turn: Area of a circle

Consider a circle with `radius = 2`. The area of this circle can be
computed in R as:

``` r
# area of circle with radius 2
r <- 2
area <- pi * r^2
area
```

    ## [1] 12.56637

Write a function `circle_area()` that calculates the area of a circle.
This function must take one argument `radius`. Give `radius` a default
value of 1. Don’t forget to include roxygen comments to document your
function\!

For example:

``` r
# default (radius 1)
circle_area()

# radius 3
circle_area(radius = 3)
```

Modify your `circle_area()` function in order to include a `stop()`
statement. If `radius` is negative, then the function should stop with a
message like: `"radius cannot be negative"`.

Test your modified `circle_area()` with `radius = -2`; the function
should return a stop message:

``` r
# bad radius
circle_area(radius = -2)
```

## Your Turn: Surface area of a cylinder

For a given cylinder of radius \(r\) and height \(h\) the surface area
\(A\) is given in the following
diagram:

![area-cylinder](https://d2jmvrsizmvf4x.cloudfront.net/qTLX7DWRme86bgXDbeWg_Cylinderr.gif)

For example. Say you have a cylinder with radius = 2, and height = 3.

``` r
# cylinder variables
r = 2  # radius
h = 3  # height

# area of cylinder
2 * pi * r * h + 2 * pi * r^2
```

    ## [1] 62.83185

Notice that the formula of the area of a cylinder includes the area of a
circle: \(\pi r^2\). Write a function `cylinder_area()`, that calls
`circle_area()`, to compute the area of a cylinder.

This function must take two arguments: `radius` and `height`. Give both
arguments a default value of 1. In addition, the function should stop if
any of `radius` or `height` are negative.

For instance:

``` r
# default (radius 1, height 1)
cylinder_area()

# radius 2, height 3
cylinder_area(radius = 2, height = 3)
```

These should return an error message:

``` r
# bad radius
cylinder_area(radius = -2, height = 1)

# bad height
cylinder_area(radius = 2, height = -1)

# bad radius and height
cylinder_area(radius = -2, height = -1)
```

## Your Turn: Volume of a cylinder

For a given cylinder of radius \(r\) and height \(h\) the volume \(V\)
is given by the product of: pi, radius squared, and height (see diagram
above).

Write a function `cylinder_volume()`, that calls `circle_area()`, to
compute the volume of a cylinder. This function must take two arguments:
`radius` and `height`. Give both arguments a default value of 1.

For example:

``` r
# default (radius 1, height 1)
cylinder_volume()

cylinder_volume(radius = 3, height = 10)
cylinder_volume(height = 10, radius = 3)
```

-----

## If Conditionals

Write R code that will “squish” a number into the interval \[0, 100\],
so that a number less than 0 is replaced by 0 and a number greater than
100 is replaced by 100.

``` r
z <- 100*pi
# Fill in the following if-else statements. You may (or may not) 
# have to add or subtract else if or else statements.
if (TRUE) { # Replace TRUE with a condition.
  
} else if (TRUE) { # Replace TRUE with a condition.
  
} else {
  
}
```

    ## NULL

### Multiple If’s

A common situation involves working with multiple conditions at the same
time. You can chain multiple if-else statements:

``` r
y <- 1 # Change this value!

if (y > 0) {
  print("positive")
} else if (y < 0) {
  print("negative")
} else {
  print("zero?")
}
```

    ## [1] "positive"

## Your Turn: Even number

Write a function `is_even()` that determines whether a number is even
(i.e. multiple of 2). If the input number is even, the output should be
`TRUE`. If the input number is odd, the output should be `FALSE`. If the
input is not a number, the output should be `NA`

Test your function:

``` r
# even number
is_even(10)

# odd number
is_even(33)

# not a number
is_even('a')
```

## Your Turn: Odd number

Use your function `is_even()` to write a function `is_odd()` that
determines if a number is odd (i.e. not a multiple of 2). If a number is
odd, the output should be `TRUE`; if a number is even the output should
be `FALSE`; if the input is not a number the output should be `NA`

Test `is_odd()` with the following cases:

``` r
# odd number
is_odd(1)

# even number
is_odd(4)

# not a number
is_odd('a')
```

-----

## Switch

Working with multiple chained `if`’s becomes cumbersome. Consider the
following example that uses several `if`’s to convert a day of the week
into a number:

``` r
# Convert the day of the week into a number.
day <- "Tuesday" # Change this value!

if (day == 'Sunday') {
  num_day <- 1
} else {
  if (day == "Monday") {
    num_day <- 2
  } else {
    if (day == "Tuesday") {
      num_day <- 3
    } else {
      if (day == "Wednesday") {
        num_day <- 4
      } else {
        if (day == "Thursday") {
          num_day <- 5
        } else {
          if (day == "Friday") {
            num_day <- 6
          } else {
            if (day == "Saturday") {
              num_day <- 7
            }
          }
        }
      }
    }
  }
}


num_day
```

    ## [1] 3

Working with several nested if’s like in the example above can be a
nigthmare.

In R, you can get rid of many of the braces like this:

``` r
# Convert the day of the week into a number.
day <- "Tuesday" # Change this value!

if (day == 'Sunday') {
  num_day <- 1
} else if (day == "Monday") {
  num_day <- 2
} else if (day == "Tuesday") {
  num_day <- 3
} else if (day == "Wednesday") {
  num_day <- 4
} else if (day == "Thursday") {
  num_day <- 5
} else if (day == "Friday") {
  num_day <- 6
} else if (day == "Saturday") {
  num_day <- 7
}

num_day
```

    ## [1] 3

### Your turn: a grading function

Write a function `grade()` that takes a `score` argument (i.e. a numeric
value between 0 and 100), and returns a letter grade (i.e. character)
based on the following grading scheme:

| score        | grade |
| ------------ | ----- |
| \[90 - 100\] | `"A"` |
| \[80 - 90)   | `"B"` |
| \[70 - 80)   | `"C"` |
| \[60 - 70)   | `"D"` |
| \< 60        | `"F"` |

You should be able to call your `grade()` function like this:

``` r
# grade "A"
grade(score = 90)

# grade "B"
grade(score = 89.9999)

# grade "C"
grade(score = 70.0000001)

# grade "F"
grade(score = 50)
```

Modify your `grade()` function to include a `stop()` condition when the
input `score` value is less than zero or greater than 100. The error
message should say something like:

    "score must be a number between 0 and 100"

-----

## The `switch()` function

Consider again the chain of if-then-else’s used to convert a name day
into a number dat. We have too many if’s, and there’s a lot of
repetition in the code. If you find yourself using many if-else
statements with identical structure for slightly different cases, you
may want to consider a **switch** statement instead:

``` r
# Convert the day of the week into a number.
day <- "Tuesday" # Change this value!

switch(day, # The expression to be evaluated.
  Sunday = 1,
  Monday = 2,
  Tuesday = 3,
  Wednesday = 4,
  Thursday = 5,
  Friday = 6,
  Saturday = 7,
  NA) # an (optional) default value if there are no matches
```

    ## [1] 3

Switch statements can also accept integer arguments, which will act as
indices to choose a corresponding element:

``` r
# Convert a number into a day of the week.
day_num <- 3 # Change this value!

switch(day_num,
  "Sunday",
  "Monday",
  "Tuesday",
  "Wednesday",
  "Thursday",
  "Friday",
  "Saturday")
```

    ## [1] "Tuesday"

## Converting Miles to other units

The table below shows the different formulas for converting miles (mi)
into other scales:

| Units  | Formula         |
| ------ | --------------- |
| Inches | mi x 63360      |
| Feet   | mi x 5280       |
| Yards  | mi x 1760       |
| Meters | mi / 0.00062137 |
| Kms    | mi / 0.62137    |

Write the following five functions for each type of conversion. Each
function must take one argument `x` with default value: `x = 1`.

  - `miles2inches()`
  - `miles2feet()`
  - `miles2yards()`
  - `miles2meters()`
  - `miles2kms()`

For example:

``` r
miles2inches(2)
miles2feet(2)
miles2yards(2)
miles2meters(2)
miles2kms(2)
```

-----

## Using `switch()`

Create a function `convert()` that converts miles into the specified
units. Use `switch()` and the previously defined
functions—`miles2inches()`, `miles2feet()`, …, `miles2kms`—to define
`convert()`. Use two arguments: `x` and `to`, like this:

``` r
convert(40, to = "in")
```

By default, `to = "km"`, but it can take values such as `"in"`, `"ft"`,
`"yd"`, or `"m"`.

Test `convert()` with:

``` r
convert(3, "in")
convert(3, "ft")
convert(3, "yd")
convert(3, "m")
convert(3, "km")
```

-----

# Intro to Loops

The majority of functions that work with vectors are vectorized.
Remember that vectorized operations are calculations that are applied to
all the elements in a vector (element-wise operations).

In order to learn about loops and iterations, it’s good to forget about
vectorized operations in R. This means that you will be asked to write
code, using some sort of loop structure, to perform tasks for which
there is already a vectorized implementation. For example, in this lab
you will have to write code with various types of loops to calculate the
mean of a numeric vector. This can easily be done using the function
`mean()`. But we don’t want you to use `mean()`. We want you to think
about control-flow structures, which are essential in any programming
activity.

## For loops

Let’s start with a super simple example. Consider a vector `vec <-
c(3, 1, 4)`. And suppose you want to add 1 to every element of `vec`.
You know that this can easily be achieved using vectorized code:

``` r
vec <- c(3, 1, 4) 

vec + 1
```

    ## [1] 4 2 5

In order to learn about loops, I’m going to ask you to forget about the
notion of vectorized code in R. That is, pretend that R does not have
vectorized functions.

Think about what you would manually need to do in order to add 1 to the
elements in `vec`. This addition would involve taking the first element
in `vec` and add 1, then taking the second element in `vec` and add 1,
and finally the third element in `vec` and add 1, something like this:

``` r
vec[1] + 1
vec[2] + 1
vec[3] + 1
```

The code above does the job. From a purely arithmetic standpoint, the
three lines of code reflect the operation that you would need to carry
out to add 1 to all the elements in `vec`.

From a programming point of view, you are performing the same type of
operation three times: selecting an element in `vec` and adding 1 to it.
But there’s a lot of (unnecessary) repetition.

This is where loops come very handy. Here’s how to use a `for ()` loop
to add 1 to each element in `vec`:

``` r
vec <- c(3, 1, 4)

for (j in 1:3) {
  print(vec[j] + 1)
}
```

    ## [1] 4
    ## [1] 2
    ## [1] 5

In the code above we are taking each `vec` element `vec[j]`, adding 1 to
it, and printing the outcome with `print()` so you can visualize the
additions at each iteration of the loop.

**Your turn**: rewrite the `for` loop in order to triple every element
in `vec`, and printing the output at each step of the loop:

``` r
vec <- c(3, 1, 4) # Change this value!

for (j in c()) { # Replace c() with an appropriate sequence.
  # Fill in.
  
}
```

What if you want to create a vector `vec2`, in which you store the
values produced at each iteration of the loop? Here’s one possibility:

``` r
vec <- c(3, 1, 4)  # Change this value!
vec2 <- rep(0, length(vec))  # "empty" of zeros vector to be filled in the loop

for (i in c()) {# Replace c() with an appropriate sequence.
  # Fill in.
}
```

-----

### Your Turn: Summation Series

Write a for loop to compute the following two series. Your loop should
start at step \(k=0\) and stop at step \(n\). Test your code with
different values for \(n\). And store each k-th term at each iteration.
Does the series converge as \(n\) increase?

![series1](lab07-images/sum_series1.png)

\[
\sum_{k=0}^{n} \frac{1}{2^k} = 1 + \frac{1}{2} + \frac{1}{4} + \frac{1}{8} + \dots + \frac{1}{2^n}
\]

![series2](lab07-images/sum_series2.png)

\[
\sum_{k=0}^{n} \frac{1}{9^k} =1 + \frac{1}{9} + \frac{1}{81} + \dots + \frac{1}{9^n}
\]

### Your Turn: Arithmetic Series

Write a for loop to compute the following arithmetic series
\(a_n = a_1 + (n-1)d\) when \(a_1 = 3\), and \(d = 3\). For instance:
\(3 + 6 + 9 + 12 + 15 + \dots\).

![arithmetic series](lab07-images/arith_series.png)

\[
a_n = a_1 + (n-1)d
\]

Test your code with different values for \(n\). And store each n-th term
at each iteration. Does the series converge as \(n\) increase?

### Your Turn: Geometric Sequence

A sequence such as \(3, 6, 12, 24, 48\) is an example of a geometric
sequence. In this type of sequence, the \(n\)-th term is obtained as:

![geometric sequence](lab07-images/geo_seq.png)

\[
a_n = a_1 \times r^{n-1}
\]

where: \(a_1\) is the first term, \(r\) is the common ratio, and \(n\)
is the number of terms.

Write a for loop to compute the sum of the first \(n\) terms of:
\(3 + 6 + 12 + 24 + \dots\). Test your code with different values for
\(n\). Does the series converge as \(n\) increase?

-----

### Your Turn: Sine Approximation

Consider the following series that is used to approximate the function
\(sin(x)\):

![sine approximation](lab07-images/sine_series.png)

\[
sin(x) \approx x - \frac{x^3}{3!} + \frac{x^5}{5!} - \frac{x^7}{7!} + \dots
\]

Write a `for` loop to approximate \(sin(x)\). Try different number of
terms, \(n = 5, 10, 50, 100\). Compare your loop with the `sin()`
function.
