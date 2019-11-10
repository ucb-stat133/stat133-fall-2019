More Regular Expressions
================
Gaston Sanchez

> ### Learning Objectives:
> 
>   - More examples with regular expressions
>   - Regex functions in package `"stringr"`
>   - Text file with log common format

-----

## Getting started with Regex in R

In this tutorial we’ll be mainly using functions from the R package
`"stringr"`:

``` r
# install.packages(stringr)
library(stringr)
```

Although R has built-in functions to perform regex operations, I’ve
found that functions from `"stringr"` are more user friendly (i.e. they
have a more consistent naming style).

## Data Log File

In this tutorial, we’ll be using the text file `may-logs.txt` located in
the `data/` folder of the course github repo:

<https://raw.githubusercontent.com/ucb-stat133/stat133-fall-2018/master/data/may-logs.txt>

This file is a **server log file** that contains the recorded events
taking place in a web server. The content of the file is in a special
format known as *common log format*. According to
[wikipedia](https://en.wikipedia.org/wiki/Common_Log_Format):

“The Common Log Format is a standardized text file format used by web
servers when generating server log files.”

Here’s an example of a log record (the text should in one line of code,
but I’ve split it into 2 lines for readibility purposes)

    pd9049dac.dip.t-dialin.net - - [01/May/2001:01:51:25 -0700] 
    "GET /accesswatch/accesswatch-1.33/ HTTP/1.0" 200 1004

  - A `"-"` in a field indicates missing data.
  - `pd9049dac.dip.t-dialin.net` is the IP address of the client (remote
    host) which made the request to the server.
  - `[01/May/2001:01:51:25 -0700]` is the date, time, and time zone that
    the request was received, by default in strftime
    format`%d/%b/%Y:%H:%M:%S %z`.
  - `"GET /accesswatch/accesswatch-1.33/ HTTP/1.0"` is the request line
    from the client.
  - The method `GET, /accesswatch/accesswatch-1.33/` is the resource
    requested, and `HTTP/1.0` is the HTTP protocol.
  - `200` is the HTTP status code returned to the client.
      - `2xx` is a successful response
      - `3xx` a redirection
      - `4xx` a client error, and
      - `5xx` a server error
  - `1004` is the size of the object returned to the client, measured in
    bytes.

If you want to download a copy of the text file to your working
directory:

``` r
# download file
github <- "https://raw.githubusercontent.com/ucb-stat133/stat133-fall-2018"
textfile <- "/master/data/may-logs.txt"
download.file(url = paste0(github, textfile), destfile = "may-logs.txt")
```

-----

## Reading the text file

The first step involves reading the data in R. How can you do this? One
option is with the `readLines()` function which reads any text file into
a character vector:

``` r
# one option is to read in the content with 'readLines()'
logs <- readLines('may-logs.txt')
```

Let’s check how the content looks like:

``` r
# take a peek at the contents in logs
head(logs)
```

    ## [1] "pd9049dac.dip.t-dialin.net - - [01/May/2001:01:51:25 -0700] \"GET /accesswatch/accesswatch-1.33/ HTTP/1.0\" 200 1004"              
    ## [2] "pd9049dac.dip.t-dialin.net - - [01/May/2001:01:51:26 -0700] \"GET /accesswatch/accesswatch-1.33/img/allifou.jpg HTTP/1.0\" 304 -"  
    ## [3] "pd9049dac.dip.t-dialin.net - - [01/May/2001:01:51:26 -0700] \"GET /sa.inside.jpg HTTP/1.0\" 304 -"                                 
    ## [4] "pd9049dac.dip.t-dialin.net - - [01/May/2001:02:20:19 -0700] \"GET /accesswatch/accesswatch-1.33/ HTTP/1.0\" 200 7791"              
    ## [5] "pd9049dac.dip.t-dialin.net - - [01/May/2001:02:20:20 -0700] \"GET /accesswatch/accesswatch-1.33/img/allifou.jpg HTTP/1.0\" 304 -"  
    ## [6] "pd9049dac.dip.t-dialin.net - - [01/May/2001:02:20:20 -0700] \"GET /accesswatch/accesswatch-1.33/img/blueblock.gif HTTP/1.0\" 304 -"

Because the file contains 26033 lines (or elements), let’s get a subset
by taking a random sample of size 50:

``` r
# subset a random sample of lines
set.seed(98765)
s <- sample(1:length(logs), size = 50)
sublogs <- logs[s]
```

### JPG File requests

To begin our regex experiments, let’s try to find out how many requests
involved a JPG file.

One way to answer the previous question is by counting how many log
lines contain the pattern `"jpg"`. We can use `str_count()` to count the
number of matches in a string:

``` r
# counting matches of "jpg"
str_count("jpg", sublogs)
```

    ##  [1] 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
    ## [36] 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0

We can also use `str_detect()` to find what elements contain the
pattern:

``` r
# showing value of matches
str_detect(sublogs, "jpg")
```

    ##  [1]  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE
    ## [12] FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE FALSE FALSE
    ## [23] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE
    ## [34] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE
    ## [45]  TRUE  TRUE FALSE FALSE FALSE  TRUE

Likewise, we can take the previous about and pass it to `which()` to
know the number of the element containing the pattern:

``` r
# showing value of matches
which(str_detect(sublogs, "jpg"))
```

    ##  [1]  1  2 10 19 20 33 42 45 46 50

We can try to be more specific by defining a pattern `".jpg"` in which
the `.` corresponds to the *literal* dot character. Recall that to match
the dot, we need to escape it with `"\\."`:

``` r
# we could try to be more precise and match ".jpg"
str_detect(sublogs, pattern = "\\.jpg ")
```

    ##  [1]  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE
    ## [12] FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE FALSE FALSE
    ## [23] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE
    ## [34] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE
    ## [45]  TRUE  TRUE FALSE FALSE FALSE  TRUE

``` r
# extracting ".png"
str_extract(string = sublogs, pattern = "\\.jpg")
```

    ##  [1] ".jpg" ".jpg" NA     NA     NA     NA     NA     NA     NA     ".jpg"
    ## [11] NA     NA     NA     NA     NA     NA     NA     NA     ".jpg" ".jpg"
    ## [21] NA     NA     NA     NA     NA     NA     NA     NA     NA     NA    
    ## [31] NA     NA     ".jpg" NA     NA     NA     NA     NA     NA     NA    
    ## [41] NA     ".jpg" NA     NA     ".jpg" ".jpg" NA     NA     NA     ".jpg"

We can do the same for PNG extensions:

``` r
# matching "png" (which lements)
str_detect(string = sublogs, pattern = "\\.png")
```

    ##  [1] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [12] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [23] FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE
    ## [34] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [45] FALSE FALSE FALSE FALSE FALSE FALSE

``` r
# extracting ".png"
str_extract(string = sublogs, pattern = "\\.png")
```

    ##  [1] NA     NA     NA     NA     NA     NA     NA     NA     NA     NA    
    ## [11] NA     NA     NA     NA     NA     NA     NA     NA     NA     NA    
    ## [21] NA     NA     NA     NA     NA     NA     NA     ".png" NA     NA    
    ## [31] NA     NA     NA     NA     NA     NA     NA     NA     NA     NA    
    ## [41] NA     NA     NA     NA     NA     NA     NA     NA     NA     NA

-----

## Image files

Now let’s try to count all types of image files (JPG, PNG, GIF, ICO) on
the entire vector of `logs`

``` r
# looking for image file extensions
jpgs <- str_count(logs, pattern = "\\.jpg ")
sum(jpgs)
```

    ## [1] 5509

``` r
pngs <- str_count(logs, pattern = "\\.png ")
sum(pngs)
```

    ## [1] 1374

``` r
gifs <- str_count(logs, pattern = "\\.gif")
sum(gifs)
```

    ## [1] 8818

``` r
icos <- str_count(logs, pattern = "\\.ico ")
sum(icos)
```

    ## [1] 100

### How to match image files with one regex pattern?

We can use character sets to define a more generic pattern. For
instance, to match `"jpg"` or `"png"`, we could join three character
sets: `"[jp][pn][g]"`. The first set `[jp]` looks for `j` or `p`, the
second set `[pn]` looks for `p` or `n`, and the third set simply looks
for `g`.

``` r
# matching "jpg" or "png"
jpg_png_lines <- str_detect(sublogs, "[jp][pn][g]")
sum(jpg_png_lines)
```

    ## [1] 11

Including the dot, we can use: `"\\.[jp][pn][g]"`

``` r
# matching "jpg" or "png"
jpg_png_lines <- str_detect(sublogs, "\\.[jp][pn][g]")
sum(jpg_png_lines)
```

    ## [1] 11

We could generalize the pattern to include the GIF and ICO extensions:

``` r
# matching "jpg" or "png" or "gif"
image_lines1 <- str_detect(sublogs, "[jpgi][pnic][gfo]")
sum(image_lines1)
```

    ## [1] 46

To confirm that we are actually matching `jpg`, `png`, `gif` and `ico`,
let’s use `str_extract()`

``` r
# are we correctly extracting image file extensions?
str_extract(sublogs, "[jpgi][pnic][gfo]")
```

    ##  [1] "ing" "ing" "ing" "gif" NA    "ing" "ing" "gif" "ing" "ing" "gif"
    ## [12] "ing" "gif" "ing" "ing" "ing" "ing" "gif" "ing" "ing" "ing" "ing"
    ## [23] "ing" "ing" "ing" "gif" "ing" "ing" "ing" "ing" NA    "ing" "ing"
    ## [34] "ing" "ing" NA    "ing" "ing" "ing" "ing" "ing" "ing" "inf" "ing"
    ## [45] "ing" "ing" NA    "ing" "gif" "ing"

The previous pattern does not really work as expected: note that we are
matching the patterns formed by `"ing"` and `"inf"` which do not
correspond to image file extensions.

An alternative way to detect JPG and PNG is by grouping patterns inside
parentheses, and separating them with the metacharacter `"|"` which
means *OR*:

``` r
# detecting .jpg OR .png
jpg_png <- str_detect(sublogs, "\\.jpg|\\.png")
sum(jpg_png)
```

    ## [1] 11

Here’s how to detect all the extension in one single pattern:

``` r
# matching "jpg" or "png" or "gif" or "ico"
image_lines <- str_detect(sublogs, "\\.jpg|\\.png|\\.gif|\\.ico")
sum(image_lines)
```

    ## [1] 29

To make sure our regex operation is successful, let’s see the output of
`str_extract()`:

``` r
images_output <- str_extract(sublogs, "\\.jpg|\\.png|\\.gif|\\.ico")
images_output
```

    ##  [1] ".jpg" ".jpg" NA     ".gif" NA     ".gif" NA     ".gif" NA     ".jpg"
    ## [11] ".gif" ".gif" ".gif" ".gif" NA     NA     ".gif" ".gif" ".jpg" ".jpg"
    ## [21] ".gif" ".gif" NA     NA     NA     ".gif" NA     ".png" NA     NA    
    ## [31] NA     ".ico" ".jpg" NA     ".gif" NA     NA     ".gif" NA     NA    
    ## [41] NA     ".jpg" NA     ".gif" ".jpg" ".jpg" NA     ".gif" ".gif" ".jpg"

There’s some repetition with the dot character; we can modify our
previous pattern by placing the dot `"\\."` at the beginning:

``` r
images_output <- str_extract(sublogs, "\\.jpg|png|gif|ico")
images_output
```

    ##  [1] ".jpg" ".jpg" NA     "gif"  NA     "gif"  NA     "gif"  NA     ".jpg"
    ## [11] "gif"  "gif"  "gif"  "gif"  NA     NA     "gif"  "gif"  ".jpg" ".jpg"
    ## [21] "gif"  "gif"  NA     NA     NA     "gif"  NA     "png"  NA     NA    
    ## [31] NA     "ico"  ".jpg" NA     "gif"  NA     NA     "gif"  NA     NA    
    ## [41] NA     ".jpg" NA     "gif"  ".jpg" ".jpg" NA     "gif"  "gif"  ".jpg"

Notice that the dot only appears next to `".jpg"` but not with the other
type of extensions. What we need to do is group the file extensions by
surrounding them with parentheses:

``` r
images_output <- str_extract(sublogs, "\\.(jpg|png|gif|ico)")
images_output
```

    ##  [1] ".jpg" ".jpg" NA     ".gif" NA     ".gif" NA     ".gif" NA     ".jpg"
    ## [11] ".gif" ".gif" ".gif" ".gif" NA     NA     ".gif" ".gif" ".jpg" ".jpg"
    ## [21] ".gif" ".gif" NA     NA     NA     ".gif" NA     ".png" NA     NA    
    ## [31] NA     ".ico" ".jpg" NA     ".gif" NA     NA     ".gif" NA     NA    
    ## [41] NA     ".jpg" NA     ".gif" ".jpg" ".jpg" NA     ".gif" ".gif" ".jpg"

Now let’s apply the pattern on the entire log file, to count the number
of files of each type:

``` r
# frequencies
img_extensions <- str_extract(logs, "\\.(jpg|png|gif|ico)")
table(img_extensions)
```

    ## img_extensions
    ## .gif .ico .jpg .png 
    ## 8818  100 5509 1374

-----

## More Questions

  - How to get the entire name of the image file (`image.ext`)?

  - How to get just the name of the image file without, the extension
    (`image`)?

  - How to get the date?

<!-- end list -->

``` r
str_extract(sublogs, "\\d\\d/.*/\\d{4}")
```

    ##  [1] "29/May/2001" "22/May/2001" "23/May/2001" "26/May/2001" "24/May/2001"
    ##  [6] "31/May/2001" "22/May/2001" "23/May/2001" "31/May/2001" "27/May/2001"
    ## [11] "25/May/2001" "30/May/2001" "02/May/2001" "27/May/2001" "23/May/2001"
    ## [16] "30/May/2001" "08/May/2001" "16/May/2001" "22/May/2001" "24/May/2001"
    ## [21] "22/May/2001" "30/May/2001" "24/May/2001" "29/May/2001" "23/May/2001"
    ## [26] "10/May/2001" "26/May/2001" "22/May/2001" "31/May/2001" "31/May/2001"
    ## [31] "23/May/2001" "23/May/2001" "24/May/2001" "29/May/2001" "28/May/2001"
    ## [36] "25/May/2001" "25/May/2001" "30/May/2001" "22/May/2001" "25/May/2001"
    ## [41] "22/May/2001" "31/May/2001" "27/May/2001" "23/May/2001" "28/May/2001"
    ## [46] "29/May/2001" "28/May/2001" "22/May/2001" "18/May/2001" "24/May/2001"

  - How to get the time?

<!-- end list -->

``` r
str_extract(sublogs, "\\d\\d:\\d\\d:\\d\\d ")
```

    ##  [1] "20:42:45 " "21:18:01 " "00:53:37 " "15:14:17 " "23:20:17 "
    ##  [6] "06:54:44 " "13:30:28 " "03:46:07 " "06:10:12 " "20:13:09 "
    ## [11] "07:14:02 " "11:08:08 " "11:43:48 " "20:40:42 " "13:29:18 "
    ## [16] "11:54:07 " "20:23:09 " "06:54:33 " "07:37:02 " "04:27:34 "
    ## [21] "10:46:54 " "08:33:25 " "13:23:29 " "06:21:36 " "06:14:06 "
    ## [26] "07:48:18 " "02:38:47 " "22:23:14 " "11:34:51 " "11:02:03 "
    ## [31] "09:55:46 " "09:50:13 " "08:56:04 " "10:57:03 " "07:13:49 "
    ## [36] "12:21:43 " "04:59:18 " "12:21:24 " "03:14:30 " "19:19:12 "
    ## [41] "02:28:29 " "05:41:29 " "02:34:41 " "14:04:08 " "00:50:12 "
    ## [46] "14:01:13 " "06:33:48 " "09:15:47 " "11:50:12 " "15:48:10 "

``` r
str_replace(str_extract(sublogs, "\\d\\d:\\d\\d:\\d\\d "), " ", "")
```

    ##  [1] "20:42:45" "21:18:01" "00:53:37" "15:14:17" "23:20:17" "06:54:44"
    ##  [7] "13:30:28" "03:46:07" "06:10:12" "20:13:09" "07:14:02" "11:08:08"
    ## [13] "11:43:48" "20:40:42" "13:29:18" "11:54:07" "20:23:09" "06:54:33"
    ## [19] "07:37:02" "04:27:34" "10:46:54" "08:33:25" "13:23:29" "06:21:36"
    ## [25] "06:14:06" "07:48:18" "02:38:47" "22:23:14" "11:34:51" "11:02:03"
    ## [31] "09:55:46" "09:50:13" "08:56:04" "10:57:03" "07:13:49" "12:21:43"
    ## [37] "04:59:18" "12:21:24" "03:14:30" "19:19:12" "02:28:29" "05:41:29"
    ## [43] "02:34:41" "14:04:08" "00:50:12" "14:01:13" "06:33:48" "09:15:47"
    ## [49] "11:50:12" "15:48:10"

  - How to get the request type: e.g. `"GET`?

  - How to get the status codes: e.g. `200`?

  - How to get the size of the resource (number at the end):
    e.g. `34301"`?

  - How to get the IP address of the client?
