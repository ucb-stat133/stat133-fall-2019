Lab 5: More Bash and Intro to Git
================
Gaston Sanchez

> ### Learning Objectives:
>
> -   First contact with Git, and its basic workflow
> -   Use Unix output redirection with `>` and `>>`
> -   Use Unix pipes with `|`
> -   Use filters: `cut`, `paste`, `sort`, `uniq`, `grep`
> -   First contact with R script files
> -   Learn about various exporting options in R

### General Instructions

-   You DON'T need to use an `.Rmd` file for this lab
-   Part of this lab involves writing code in an `R` script file.
-   Name this file as `script-first-last.R`, where `first` and `last` are your first and last names (e.g. `script-gaston-sanchez.R`).
-   Submit your `R` file to bCourses, in the corresponding lab assignment.

While you work on this assignment, you may want to open Git's cheatsheet:

<https://github.com/ucb-stat133/stat133-fall-2019/blob/master/cheatsheets/git-cheatsheet.pdf>

------------------------------------------------------------------------

0 Introducing yourself to Git
-----------------------------

We are assuming that you have installed Git in your computer. To confirm that this is the case, on the terminal type the following command:

``` bash
git --version
```

If you have Git installed, you should be able to see a version number. Otherwise, it very likely means that you don't have Git installed.

When you use Git on a (new) computer for the first time, you need to configure a few things:

-   your name
-   your email address
-   command line coloring for Git
-   and that you want to use these settings globally (i.e. for every project)

On the terminal, type the following configuration commands, **using your own name and email**:

``` bash
# Use your own First and Last names!!!
git config --global user.name "Gaston Sanchez"

# Use your own email address!!
git config --global user.email "gasigiri@berkeley.edu"

# coloring Git output
git config --global color.ui auto
```

Please use your own name and email address. This user name and email will be associated with your subsequent Git activity, which means that any changes pushed to GitHub or any nother Git host server in a later lesson will include this information.

------------------------------------------------------------------------

1 Filestructure and Data File
-----------------------------

To help you better prepare for Workout-1, we want you to practice using a more sophisticated file structure. Follow the steps listed below to create the necessary subdirectories.

In your computer, **Outside** the directory for Stat 133, create a directory `gitdemo`:

        gitdemo/
           README.md
           data/
           code/
           output/
           images/

-   Open a shell terminal (e.g. command line or GitBash)
-   Change your working directory to a location where you will store all the materials for this demo.
-   Create a directory `gitdemo`
-   Change directory to `gitdemo`
-   Create other subdirectories: `data`, `code`, `output`, `images`
-   List the contents of `gitdemo` to confirm that you have all the subdirectories
-   Use `touch` to create an empty `README.md` text file.
-   Open the `README.md` file with a text editor (e.g. the one in RStudio) and add a brief description of what this lab is about. Save the changes.
-   Change directory to `data/`
-   Download the data file with the command `curl`, and the `-O` option (letter O)

    ``` bash
    curl -O curl -O https://raw.githubusercontent.com/ucb-stat133/stat133-fall-2019/master/data/nba2018-players.csv
    ```

-   List the contents to confirm that the csv file is in `data/`
-   Use *word count* `wc` to count the lines of the csv file
-   Take a peek at the first rows of the csv file
-   Take a peek at the last 5 rows of the csv file
-   Move outside `data/` (i.e. return to directory `demo/`)

------------------------------------------------------------------------

2 Initialize your Repository
----------------------------

Let's tell Git to make `gitdemo/` a **repository**, which is the fancy name where Git can store versions of our files:

``` bash
# assuming you are inside gitdemo/
git init
```

List all contents in `gitdemo/`, including hidden (dot) files:

``` bash
ls -la
```

Git uses this special sub-directory called `.git/` to store all the information about the project, including all files and sub-directories located within the project's directory. If you ever delete the `.git/` sub-directory, you will lose the project's history.

You can check that everything is set up correctly by asking Git to tell you the **status** of our project:

``` bash
git status
```

If you check the status of your project, Git tells you that it's noticing new files, with some output like this:

    On branch master

    No commits yet

    Untracked files:
      (use "git add <file>..." to include in what will be committed)

        README.md
        data/

    nothing added to commit but untracked files present (use "git add" to track)

The "untracked files" message means that there are files in the directory that Git isn't keeping track of.

------------------------------------------------------------------------

3 Adding changes to Git's database
----------------------------------

How do you tell Git to start tracking changes in a file? We can tell Git to track a file using `git add`:

``` bash
git add README.md
```

and then check that the right thing happened:

``` bash
git status
```

    On branch master

    No commits yet

    Changes to be committed:
      (use "git rm --cached <file>..." to unstage)

        new file:   README.md

    Untracked files:
      (use "git add <file>..." to include in what will be committed)

        data/

Git now knows that it's supposed to keep track of `README.md`, but it hasn't recorded these changes as a **commit** yet. To get it to do that, you need to run one more command:

``` bash
git commit -m "readme: add README"
```

    [master (root-commit) 000b3a9] add README
     1 file changed, 1 insertion(+)
     create mode 100644 README.md

When you run git commit, Git takes everything you have told it to save by using `git add` and stores a copy permanently inside the special `.git/` directory. This permanent copy is called a **commit** (or revision) and its short identifier is 000b3a9. Your commit may have another identifier.

We use the `-m` flag (for "message") to record a short, descriptive, and specific comment that will help us remember later on what we did and why. If you just run git commit without the `-m` option, Git will launch *nano* (or whatever other editor we configured as core.editor) so that we can write a longer message.

Good commit messages start with a brief (&lt;50 characters) statement about the changes made in the commit.

If you run `git status` now:

``` bash
git status
```

    On branch master`
    Untracked files:
      (use "git add <file>..." to include in what will be committed)

        data/

    nothing added to commit but untracked files present (use "git add" to track)

If you want to know what you've done recently, you can ask Git to show you the project's history using `git log`

``` bash
git log
```

    commit 000b3a90e6eb798d3cce75fbcfb26df566176ee2 (HEAD -> master)
    Author: Gaston Sanchez <gasigiri@berkelely.edu>
    Date:   Mon Sep 23 09:30:20 2019 -0700

        add README

The command `git log` lists all commits made to a repository in reverse chronological order. The listing for each commit includes the commit's full identifier (which starts with the same characters as the short identifier printed by the git commit command earlier), the commit's author, when it was created, and the log message Git was given when the commit was created.

### Your Turn

-   Tell git to add changes in file `nba2018-players.csv` (try using a relative path)
-   Check the status
-   Commit the added modifications (include a commit message)
-   Check the status of your project again
-   Examine what has been made with `git log`

------------------------------------------------------------------------

4 Piping
--------

Use the `nba2018-players.csv` data to perform the following tasks. All the commands have to be bash-shell commands (not R commands).

-   `cut` allows you to *select* columns
-   `grep` allows you to *filter* rows
-   `sort` can be used to *arrange* lines
-   `sort` could be used to *group by* lines
-   `sort` and `uniq` can be used to *count* occurrences

#### Example 1)

Here's a pipeline to obtain the unique team names. First we `cut` the second column (team names), then we skip the first row with `tail +2`, and finally we `sort` unique occurrences:

``` bash
# cd to data/
cd data

# display unique team names
cut -f 2 -d "," nba2018-players.csv | tail +2 | sort -u
```

We can use the previous pipeline, and redirect the output to a text file `team-names.txt` using the output redirection operator `>`.

``` bash
# file with list of unique team names
cut -f 2 -d "," nba2018-players.csv | tail +2 | sort -u > team-names.txt
```

To confirm that `team-names.txt` has the unique names, we can use `head` to display the first five lines of the created file:

``` bash
head -n 5 team-names.txt
```

Now that we have new files, we can tell Git to track them:

``` bash
git status
git add team-names.txt
git status
git commit -m "data: adding team-names"
git status
```

#### Example 2)

Here's another pipeline to find the number of players in `CLE` (Cleveland) team; the output should be just the number of players.

``` bash
# how many players in CLE
grep "CLE" nba2018-players.csv | wc -l
```

If you want to create a file with the data for Cleveland players, you can redirect the output to a text file `cleveland.csv`:

``` bash
grep "CLE" nba2018-players.csv > cleveland.csv
```

Notice that the created file `cleveland.csv` does NOT contain names of columns in the first row. We can tell Git to track the new changes:

``` bash
git status
git add cleveland.csv
git status
git commit -m "data: adding file of cleveland players"
git status
```

### Your Turn

**4.1)** Write a pipeline to obtain the unique player positions (column 3), and redirect the output to a text file `position-names.txt`. Add and commit the new modifications in your `gitdemo` project. *HINT:* these filters are your friends: `cut`, `tail`, `sort`; and redirection `>` operator.

**4.2)** Write a pipeline to obtain the counts (i.e. frequencies) of the different `experience` values (column 7), displayed from largest to smallest (i.e. descending order). The first column corresponds to count, the second column corresponds to experience. Redirect the output to a text file `experience-counts.txt`. Add and commit the new modifications in your `gitdemo` project. *HINT:* these filters are your friends: `cut`, `tail`, `sort`, `uniq`; and redirection `>` operator.

**4.3)** Use output redirection commands to create a CSV file `LAC.csv` containing data for the `LAC` team (Los Angeles Clippers). Your CSV file should include column names in the first row. Add and commit the new modifications in your `gitdemo` project. *HINT:* redirection operators `>` and `>>`, as well as `head` and `grep` are your friends.

**4.4)** Write pipelines to create a CSV file `gsw-height-weight.csv` that contains the `player`, `height` and `weight` of `GSW` players. Your CSV file should include column names. Add and commit the new modifications in your `gitdemo` project. *HINT:* redirection operators `>` and `>>`, as well as `cut`, `head`, and `grep` are your friends.

**4.5)** *Difficult*. This is optional. Write pipelines to create a file `top10-salaries.csv` containing the top10 player salaries, arranged by `salary` from largest to smallest. Your CSV file should include column names (`player`, `salary`). Add and commit the new modifications in your `gitdemo` project. *HINT:* redirection operators `>` and `>>`, as well as `cut`, `tail`, and `sort`, and `head` are your friends.

------------------------------------------------------------------------

5 R script file
---------------

The second part of this lab involves working with an `R` script file (NOT to confuse with an `Rmd` file).

-   Once you have the filestructure for this lab, go to RStudio and open a new `R` script file
-   Save the `R` script file as `demo-script.R` in the `code/` folder of `gitdemo/`

R script files are used to write R code only, using R syntax. In other words, you should NOT use Markdown or LaTeX syntax inside an R script file. Why? Because if you run the entire script, R will try to execute all the commands, and won't be able to recognize Markdown, LaTeX, yaml, or other syntaxes.

### File Header

Let's start with some good coding practices by adding a header to the `R` script file in the form of R comments. In general, the header section should contain a title, a description of what the script is about, what are the inputs, and what are the main outputs produced when executing the code in the script. Optionally, you can also include the name of the author, the date, and other details. Something like this:

    # Title: Short title (one sentence)
    # Description: what the script is about (one paragraph or two)
    # Input(s): what are the main inputs (list of inputs)
    # Output(s): what are the main outputs (list of outputs)
    # Author(s): First Last
    # Date: mm-dd-yyyy

Think of the header of a script file as the yaml header used in `Rmd` files. The header should be the very first thing that appears at the top of the script file. Personally, I like to surround the header in my R script files with some delimiting characters that help the reader to visually identify main parts of the script. Here's a hypothetical example of a header:

``` r
# ===================================================================
# Title: Descriptive Analysis
# Description:
#   This script computes descriptive statistics, as well as 
#   various exploratory data visualizations.
# Input(s): data file 'nba2018-players.csv'
# Output(s): summary data files, and plots
# Author: Gaston Sanchez
# Date: 9-23-2019
# ===================================================================
```

Another good coding practice is to avoid writing very long lines of code. Most coding style guides stick to a maximum line width of 80 characters, and this is the [magic number](https://softwareengineering.stackexchange.com/questions/148677/why-is-80-characters-the-standard-limit-for-code-width) that I also use for my scripts.

**Your turn**: Include a header in your R script file, respecting the width limit of 80 characters. Save this file in the `code/` folder.

### Required Packages

The next thing that you need to include in your script file are the required packages. Not all script files need packages, but many do. When this is the case, loading the packages should be the first lines of code to be executed.

Include the commands to load the following packages in your script:

``` r
# packages
library(dplyr)    # data wrangling
library(ggplot2)  # graphics
```

In addition to loading the packages, sometimes you will also need to load code from other script files. We won't do that today, but you should know that this is very common as the complexity and size of your projects grow.

**Tell Git to add and commit the R script file.**

------------------------------------------------------------------------

6 Exporting some data tables
----------------------------

After the header, and the loading-packages sections, the next part in your `.R` script involves importing the data. In addition to importing a data table, you are also going to practice exporting tables. That is, writing data tables to external files.

We want you to work with relative paths. To execute the commands that read input(s) and write output(s), you will need to set the working directory. On the menu bar go to **Session**, then select the option **Set Working Directory**, and choose **To Source File Location**.

### Your Turn

-   Use `read.csv()` to import the data `nba2018-players.csv` in R. Do this by specifying a relative path.

-   Use the imported table to create a data frame `warriors` by selecting rows---e.g. `filter()`---of Golden State Warriors, arranging rows by salary in increasing order.

-   Use the function `write.csv()` to export (or save) the data frame `warriors` to a data file `warriors.csv` in the `data/` directory. You will need to use a relative path to specify the `file` argument. Also, see how to use the argument `row.names` to avoid including a first column of numbers.

-   Inspect the contents of the `data/` folder and confirm that the csv files are there.

-   Tell Git to add and commit the new modifications in your project.

------------------------------------------------------------------------

7 Exporting some R output
-------------------------

Yyou will produce some summary statistics, and then save the generated output to external text files. To do this, you will have to learn about the `sink()` function, which sends R output to a specified file.

Say you are interested in exporting the summary statistics of `height` and `weight`, exactly in the same way they are displayed by R:

``` r
summary(dat[ ,c('height', 'weight')])
```

    ##      height          weight     
    ##  Min.   :69.00   Min.   :150.0  
    ##  1st Qu.:77.00   1st Qu.:200.0  
    ##  Median :79.00   Median :220.0  
    ##  Mean   :79.15   Mean   :220.2  
    ##  3rd Qu.:82.00   3rd Qu.:240.0  
    ##  Max.   :87.00   Max.   :290.0

One naive option to "export" this output would be to manually copy the text displayed on the console, and then paste it to a text file. While this may work, it is labor intensive, error prone, and highly irreproducible. A better way to achieve this task is with the `sink()` function. Here's how:

``` r
# divert output to the specified file
sink(file = '../output/summary-height-weight.txt')
summary(dat[ ,c('height', 'weight')])
sink()
```

The fist call to `sink()` opens a connection to the specified file, and then all outputs are diverted to that location. The second call to `sink()`, i.e. the one without any arguments, closes the connection.

While you are `sink()`ing output to a specified file, all the results will be sent to such file. In other words, nothing will be printed on the console. Only after the sinking process has finished and the connection is closed, you will be able to execute commands and see results displayed on R's console.

#### Why sinking?

Why would you ever want to `sink()` R outputs to a file? Why not simply display them as part of your `Rmd` file? One good reason for diverting output to an external file is for convenience. In practice, the reports and documents (e.g. papers, executive summaries, slides) of a data analysis project won't contain everything that you tried, explored, analyzed, and graphed. There will be many intermediate results that, while relevant for a specific stage of the analysis cycle, are innecessary for the final report. So a good way to keep these intermediate outputs is by exporting them with `sink()`.

### Your Turn

-   Export the output of `str()` on the data frame with all the players. `sink()` the output, using a relative path, to a text file `data-structure.txt`, in the `output/` folder. Tell git to add and commit the changes.

-   Export the `summary()` of the entire data frame `warriors` to a text file `summary-warriors.txt`, in the `output/` folder (also use a relative path). Tell git to add and commit the changes.

-   Export another `summary()` of the entire data frame `lakers` to a text file `summary-lakers.txt`, in the `output/` folder (using a relative path). Tell git to add and commit the changes.

------------------------------------------------------------------------

8 Exporting graphs
------------------

In the same way that R output, as it appears on the console, can be exported to some files, you can do the same with graphics and plots. Actually, saving plot images is much more common than `sink()`ing output.

Base R provides a wide array of functions to save images in most common formats:

-   `png()`
-   `jpeg()`
-   `tiff()`
-   `bmp()`
-   `svg()`
-   `pdf()`

Similar to the writing table functions such as `write.table()` or `write.csv()`, and the `sink()` function, the graphics device functions require a file name to be provided. Here's how to save a simple scatterpot of `height` and `weight` in png format to the folder `images/`:

``` r
# saving a scatterplot in png format
png(filename = "../images/scatterplot-height-weight.png")
plot(dat$height, dat$weight, pch = 20, 
     xlab = 'Height', ylab = 'Height')
dev.off()
```

-   The function `png()` tells R to save the image in PNG format, using the provided filename.
-   Invoking `png()` will open a graphics device; not the graphics device of RStudio, so you won't be able to see the graphic.
-   The `plot()` function produces the scatterplot.
-   The function `dev.off()` closes the graphics device.

### Your turn

-   Open the help documentation of `png()` and related graphic devices.

-   Use `jpeg()` to save a histogram of `age` with `hist()` is a file called `histogram-age.jpeg`. Give width and height of 600 and 400 pixels, respectively. Save the graph in the `images/` folder. Tell Git to add and commit all the modifications.

-   Save another version of the scatterplot between `height` and `weight` in a file called `scatterplot2-height-weight.png`, but now try to get an image with higher resolution (Hint: argument `pointsize` is your friend). Save the plot in `images/`. Tell Git to add and commit all the modifications.

-   Use `ggplot2` functions to make and save (with `ggsave()`) another scatterplot of `height` and `weight`, facetting by `position`. Save the graph in the `images/` folder, and name the file `height_weight_by_position.pdf`. Tell Git to add and commit all the modifications.

------------------------------------------------------------------------
