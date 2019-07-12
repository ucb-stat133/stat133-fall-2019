# Stat 133: Concepts in Computing with Data

- [Policies](syllabus/policies.md)
- [Staff](syllabus/staff.md)
- [Piazza](syllabus/piazza.md)
- [FAQ](syllabus/faqs.md)

-----


## Calendar

+ __Instructor:__ Gaston Sanchez
+ __Lecture:__ MWF 9:00-10:00am, 245 Li Ka Shing
+ Tentative calendar (weekly topics), subject to change depending on 
the pace of the course.
+ Notes (:file_folder:) involves material discussed in class.
+ Reading (:book:) involves material that expands lecture topics, as well as coding examples that you should practice on your own.
+ Misc (:newspaper:) is supporting material that is worth taking a look at.


-----


## 0. Course Introduction

- :card_index: __Dates__: Aug 28-30
- :paperclip: __Topics__: Welcome to Stat 133. We begin with the usual review of the course policies/logistics, expectations, topics in a nutshell, etc. Then, we move on with an unconventional introduction to _computing with data_ using my favorite analogy "Data Analysis is a lot like Cooking".
- :file_folder: __Notes__:
    + [Welcome to Stat 133](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-00-welcome.pdf)
    + [Data Analysis is a lot like cooking](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-01-dac-cooking.pdf)
    + [Data Analysis Cycle: Example](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-02-dac-example.pdf)
- :book: __Reading__:
    + [Course policies](syllabus/policies.md)
    + [Piazza etiquette](syllabus/piazza.md)
    + [FAQs](syllabus/faqs.md)
- :microscope: __Lab__: No lab
- :newspaper: __Misc__:
    + [What is Data Science?](https://github.com/ucb-stat133/stat133-misc/blob/master/what-is-data-science.pdf)
- :speaker: __To Do__: 
    + Install [__R__](https://cran.cnr.berkeley.edu/) 
    + Install [RStudio](https://www.rstudio.com/products/rstudio/download/#download) Desktop (open source version, free)


-----


## 1. The Big Picture and R Survival Skills

- :card_index: __Dates__: Sep 02-06
- :paperclip: __Topics__: First things first. At the conceptual level we'll discuss how data analysis projects usually start with a Research Question. Also, we'll describe how Data can actually be seen from a triangular perspective (i.e. my "3 Views of Data"). At the practical level, you'll begin learning basic survival skills for R, followed by an overall review of the RStudio workspace. Then we move on to discuss basic data types and their implementation in R around vectors and other data structures. 
- :file_folder: __Notes__:
    + [The Starting Point: Research Questions](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-03-research-question.pdf)
    + [The Three Views of Data](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-04-data-perspectives.pdf)
    + Be the Boss of your Data (talk and chalk)
    + [Data Types](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-06-data-types.pdf) and [Vectors](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-07-vectors.pdf)
- :book: __Reading__:
    + [First contact with R](https://github.com/ucb-stat133/stat133-tutorials/blob/master/01-intro-to-R.md) (tutorial)
    + [Intro to Rmd files](https://github.com/ucb-stat133/stat133-tutorials/blob/master/02-intro-to-Rmd-files.md) (tutorial)
- :microscope: __Lab__:
    + [Getting started with R and RStudio](labs/lab01-R-basics.md) (due Sep-06)
- :newspaper: __Misc__:
    + [Introduction to R Markdown](http://rmarkdown.rstudio.com/lesson-1.html) (by RStudio)
- :bulb: __Cheat sheet__: 
    + [RStudio cheat sheet](cheatsheets/rstudio-IDE-cheatsheet.pdf)
    + [R markdown cheat sheet](cheatsheets/rmarkdown-cheatsheet-2.0.pdf)
- :dart: __WARM-UP 1__:
    + [Markdown practice](hws/warmup01.pdf) (due Sep-10)


-----


## 2. More Data Structures: Arrays, Lists, and Dataframes

- :card_index: __Dates__: Sep 11-13 _(Holiday Sep-09)_
- :paperclip: __Topics__: In this week you'll keep learning more about R data structures like arrays and lists. More specifically, we'll focus on fundamental concepts like atomicity, vectorization, recycling, and subsetting.
- :file_folder: __Notes__:
    + [Arrays and Factors](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-08-arrays-factors.pdf) and [Lists](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-09-lists.pdf)
    + Data Frames [part 1](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-10-data-frames1.pdf) and [part 2](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-11-data-frames2.pdf)
- :book: __Reading__:
    + [Intro to vectors](https://github.com/ucb-stat133/stat133-tutorials/blob/master/03-intro-to-vectors.md) (tutorial)
    + ["dplyr" tutorial slides](https://github.com/ucb-stat133/stat133-slides/blob/master/dplyr-wickham.pdf) (by Hadley Wickham)
- :microscope: __Lab__:
    + [Getting started with vectors and factors](labs/lab02-vector-basics.md) (due Sep-13)
- :newspaper: __Misc__:
    + [chapter 20: Vectors](http://r4ds.had.co.nz/vectors.html) (_R for Data Science_ by Grolemund and Wickham)
- :bulb: __Cheat sheet__: 
    + [Base R](cheatsheets/base-r-cheatsheet.pdf)
- :dart: __WARM-UP 2__:
    + TBA (due Sep-17)


-----


## 3. Housekeeping: Filesystem and Bash Commands

- :card_index: __Dates__: Sep 16-20
- :paperclip: __Topics__: Data Analysis Projects (DAPs) are made of files and directories. Therefore, we need to review some fundamental concepts such as the file-system, the command line interface, and some basic shell commands.
- :file_folder: __Notes__:
    + [Filesystem Basics](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-12-filesystem-basics.pdf)
    + [File Paths](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-13-file-paths.pdf)
    + [Shell Basics](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-14-shell-basics.pdf)
    + [Command Line](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-15-command-line.pdf)
    + [Working with files](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-16-working-with-files.pdf)
- :book: __Reading__:
    + [Linux Tutorial](https://ryanstutorials.net/linuxtutorial/) lessons 1-5 (by Ryan Chadwick)
    + [The Unix Shell](http://swcarpentry.github.io/shell-novice/) lessons 1-3 (by Software Carpentry)
- :microscope: __Lab__:
    + [Command Line Basics](labs/lab03-command-line-basics.md) (due Sep-20)
- :newspaper: __Misc__:
    + [Linux Command Line tutorial](https://www.guru99.com/terminal-file-manager.html) (by Guru99)
- :bulb: __Cheat sheet__:
    + [command line cheat sheet](cheatsheets/command-line-cheatsheet.pdf)
- :dart: __WARM-UP 3__:
    + TBA (due Sep-24)


-----


## 4. Data Tables: Transforming and Visualizing Tabular Data

- :card_index: __Dates__: Sep 23-27
- :paperclip: __Topics__: Because data tables are so ubiquitous, you will have the chance to practice some data manipulation operations on data frames. At the practical level, it's important that you learn how to manipulate them via R data frames in a more modern and syntactic way. How? By following the _data plying_ framework provided by the package `"dplyr"`. Also, we'll discuss some considerations when importing tables (in R).
- :file_folder: __Notes__:
    + [Data Tables](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-23-data-tables.pdf) (introduction) and [Spreadsheets](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-24-data-spreadsheets.pdf)
    + Importing tables [part 1](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-24-importing-tables1.pdf) and [part 2](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-25-importing-tables2.pdf)
- :book: __Reading__:
    + [Organizing data in spreadsheets](http://kbroman.org/dataorg/) (by Karl Broman)
    + [Intro to Data Technologies](https://www.stat.auckland.ac.nz/~paul/ItDT/itdt-2010-11-01.pdf) (preface, chapter 1, and chapter 5) (by Paul Murrell)
- :microscope: __Lab__:
    + [Data Frame Basics](labs/lab04-data-tables.md) (due Sep-27)
- :newspaper: __Misc__:
    + [tibbles vignette](https://cran.r-project.org/web/packages/tibble/vignettes/tibble.html)
    + [Introduction to dplyr](https://cran.r-project.org/web/packages/dplyr/vignettes/dplyr.html) (by Hadley Wickham)
- :bulb: __Cheat sheet__:
    + [Data transformation cheat sheet](cheatsheets/data-transformation-cheatsheet.pdf)
    + [Data visualization with ggplot2](cheatsheets/ggplot2-cheatsheet-2.1.pdf)
- :dart: __WARM-UP 4__:
    + TBA (due Oct-01)


-----


## 5. Data Visualization

- :card_index: __Dates__: Sep 30-Oct 04 
- :paperclip: __Topics__: We begin a comprehensive discussion on concepts for data visualization.  
- :file_folder: __Notes__:
    + [Datavis: Classic Examples](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-26-datavis-classic-examples.pdf) and [Introduction](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-27-datavis-intro.pdf)
    + [Datavis: Encoding Data in Graphs](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-28-encoding-data-in-graphs.pdf)
    + [Datavis: The Visual System](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-30-visual-system.pdf)
    + [Datavis: Using Color](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-32-using-color.pdf)
    + [Datavis: Effective Charts](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-33-effective-charts.pdf)
- :book: __Reading__:
    + ["ggplot2" lecture](https://github.com/ucb-stat133/stat133-slides/blob/master/ggplot-karthik.pdf) (by Karthik Ram)
- :microscope: __Lab__:
    + [Data Wrangling and Graphics](labs/lab04-dplyr-ggplot-basics.md) (due Sep-27)
- :newspaper: __Misc__:
    + [Tidy Data](https://github.com/ucb-stat133/stat133-misc/blob/master/tidy-data-wickham.pdf) (by Hadley Wickham)
- :bulb: __Cheat sheet__:
    + [Data transformation cheat sheet](cheatsheets/data-transformation-cheatsheet.pdf)
- :dart: __WORK-OUT 1__:
    + TBA (due Oct-15?)


-----


## 6. Housekeeping: Version Control with Git and GitHub

- :card_index: __Dates__: Oct 07-11
- :paperclip: __Topics__: We continue talking about filestructure topics, and we introduce basic notions of version control systems (VCS) using Git, and the companion hosting platform GitHub.
On the Data side, we begin our discussion about Tables: the most common form in which data is stored, handled, and manipulated. Consequently, we need to talk about the typical storage formats of tabular data, and the relationship between tables and R data frames.
- :file_folder: __Notes__:
    + [Git Basics](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-19-git-intro.pdf)
    + [Git Workflow](https://github.com/ucb-stat133/stat133-slides/blob/master/stat133-20-git-workflow.pdf)
- :book: __Reading__:
    + Read sections 4 to 9 in Part I [Installation](http://happygitwithr.com/installation-pain.html) (_Happy Git and GitHub for the useR_ by Jenny Bryan et al.)
- :microscope: __Lab__:
    + [Git Basics](labs/lab06-git-basics.md) (due Oct-11)
- :newspaper: __Misc__:
    + [Data Import](http://r4ds.had.co.nz/data-import.html) (_R for Data Science_ by Grolemund and Wickham)
- :bulb: __Cheat sheet__:
    + [Data import cheat sheet](cheatsheets/data-import-cheatsheet.pdf)
    + [git cheat sheet](cheatsheets/git-cheatsheet.pdf)
- :mortar_board: __MIDTERM 1__: Friday Oct-11



-----


## 7. Transition to Programming Basics for Data Analysis (part 1)

- :card_index: __Dates__: Oct 14-18
- :paperclip: __Topics__: You don’t need to be an expert programmer to be a data scientist, but learning more about programming allows you to automate common tasks, and solve new problems with greater ease. We'll discuss how to write basic functions, the notion of R expressions, and an introduction to conditionals. 
- :file_folder: __Notes__:
    + [Creating functions](https://github.com/ucb-stat133/stat133-tutorials/blob/master/06-creating-functions.md) (tutorial)
    + [Introduction to functions](https://github.com/ucb-stat133/stat133-tutorials/blob/master/07-intro-to-functions.md) (tutorial)
    + [Introduction to R expressions and conditionals](https://github.com/ucb-stat133/stat133-tutorials/blob/master/08-intro-to-expressions-conditionals.md) (tutorial)
- :microscope: __Lab__:
    + [Getting started with functions and conditionals](labs/lab07-simple-functions.md) (due Mar-15)
- :newspaper: __Misc__: 
    + [chapter 19: Functions](http://r4ds.had.co.nz/functions.html) (_R for Data Science_ by Grolemund and Wickham)
- :dart: __WARM-UP 5__:
    + [Functions](hws/warmup05.pdf) (due Mar-20)


-----


## 8. Programming Basics for Data Analysis (part 2)

- :card_index: __Dates__: Oct 21-25
- :paperclip: __Topics__: In addition to writing functions to reduce duplication in your code, you also need to learn about iteration, which helps you when you need to do the same operation several times. Namely, we review control flow structures such as `for` loops, `while` loops, `repeat` loops, and the `apply` family functions.
- :file_folder: __Notes__:
    + [Introduction to loops](https://github.com/ucb-stat133/stat133-tutorials/blob/master/09-intro-to-loops.md) (tutorial)
    + [More about functions](https://github.com/ucb-stat133/stat133-tutorials/blob/master/10-more-functions.md) (tutorial)
    + [Functions](http://adv-r.had.co.nz/Functions.html) (_Advanced R_ by H. Wickham)
    + [Environments](http://adv-r.had.co.nz/Environments.html) (_Advanced R_ by H. Wickham)
- :microscope: __Lab__: 
    + [Getting started with loops](labs/lab08-simple-loops.md) (due Mar-22)
- :newspaper: __Misc__:
    + [chapter 21: Iteration](http://r4ds.had.co.nz/iteration.html) (_R for Data Science_ by Grolemund and Wickham)
- :dart: __WARM-UP 6__:
    + [Loops and simulations](hws/warmup06.pdf) (due Apr-03)


-----


## 9. Testing Functions and Introduction to Shiny Apps

- :card_index: __Dates__: Oct 28-Nov 01
- :paperclip: __Topics__: We begin with an introduction to the package `"testthat"` which provides a nice framework for testing functions. Jointly, we will discuss Shiny apps which provide an interesting companion to R, making it quick and simple to deliver interactive analysis and graphics on any web browser. In lab, you'll learn how to perform basic manipulation of strings. 
- :file_folder: __Notes__:
    + [Intro to testing functions](https://github.com/ucb-stat133/stat133-tutorials/blob/master/11-testing-functions.md) (tutorial)
    + [shiny tutorial](https://github.com/ucb-stat133/stat133-slides/blob/master/shiny-tutorial.pdf) (by Grolemund)    
- :book: __Reading__:
    + [testthat: Get started with testing](https://github.com/ucb-stat133/stat133-misc/blob/master/testthat-wickham.pdf) (by Wickham)
    + [Character strings in R](http://www.gastonsanchez.com/r4strings/chars.html) (_r4strings_ by Sanchez)
    + [Basic string manipulations](http://www.gastonsanchez.com/r4strings/manip.html) (_r4strings_ by Sanchez)
- :microscope: __Lab__: 
    + [Getting started with strings](labs/lab09-tests-strings-basics.md) (due Apr-05)
- :newspaper: __Misc__:
    + [chapter 14: Strings](http://r4ds.had.co.nz/strings.html) (_R for Data Science_ by Grolemund and Wickham)
- :bulb: __Cheat sheet__:
    + [Stringr cheat sheet](https://github.com/ucb-stat133/stat133-cheatsheets/blob/master/stringr-cheatsheet.pdf)
- :dart: __WORK-OUT 2__:
    + [Shiny App](hws/workout02.pdf) (due Apr-17)


-----


## 10. More Shiny Apps and Introduction to Regular Expressions

- :card_index: __Dates__: Nov 04-08
- :paperclip:  __Topics__: Random numbers have many applications in science and computer programming, especially when there are significant uncertainties in a phenomenon of interest. In this part of the course we'll look at some basic problems involving working with random numbers and creating simulations. Additionally, we continue the discussion about character strings with a first contact to Regular Expressions. 
- :file_folder: __Notes__:
    + [Introduction to random numbers](https://github.com/ucb-stat133/stat133-tutorials/blob/master/12-intro-to-random-numbers.md)
    + [Coin toss shiny app](https://github.com/ucb-stat133/stat133-fall-2018/tree/master/apps/coin-toss)
    + [Regexpal](http://regexpal.com.s3-website-us-east-1.amazonaws.com/) tester tool.
- :book: __Reading__:
    + [Part 1 - How to build a Shiny app](https://vimeo.com/rstudioinc/review/131218530/212d8a5a7a/#t=0m0s) (video)
- :microscope: __Lab__:
    + [Random numbers and simulations](labs/lab10-random-simulations.md) (due Apr-12)
- :newspaper: __Misc__:
    + [Part 2 - How to customize reactions](https://vimeo.com/rstudioinc/review/131218530/212d8a5a7a/#t=42m2s) (video)
    + [Part 3 - How to customize appearance](https://vimeo.com/rstudioinc/review/131218530/212d8a5a7a/#t=1h32m41s) (video)
- :bulb: __Cheat sheet__:
    + [shiny cheat sheet](cheatsheets/shiny-cheatsheet.pdf)
- :dart: __WORK-OUT 2__:
    + _Keep working on your workout02 assignment._


-----


## 11. More Regular Expressions

- :card_index: __Dates__: Nov 11-15
- :paperclip:  __Topics__: At its heart, computing involves working with numbers. However, a considerable amount of information and data is in the form of text. To unleash the power of strings manipulation, we need to take things to the next level and learn about Regular Expressions. Namely, Regular expressions are a tool that allows us to describe a certain amount of text called "patterns". We'll describe the basic concepts of regex and the common operations to match text patterns.
- :file_folder: __Notes__:
    + [Long Jump World Record example](https://www.gastonsanchez.com/r4strings/cleaning.html)
    + [Log file example](https://www.gastonsanchez.com/r4strings/logs.html)
- :book: __Reading__:
    + [Handling Strings in R](https://www.gastonsanchez.com/r4strings) (by Sanchez)
- :microscope: __Lab__:
    + [Regular Expressions](labs/lab11-regex-basics.md) (due Apr-19)
- :bulb: __Cheat sheet__:
    + [Regular Expressions cheat sheet](cheatsheets/regular-expressions-cheatsheet.pdf)
- :dart: __WORK-OUT 3__:
    + [R Package](hws/workout03.pdf) (due May-03)


-----


## 12. R packaging (part 1)

- :card_index: __Dates__: Nov 18-22
- :paperclip: __Topics__: Packages are the fundamental units of reproducible R code. They include reusable functions, the documentation that describes how to use them, and sample data. In this part we'll start describing how to turn your code into an R package.
- :file_folder: __Notes__:
    + [Programming S3 Classes](https://www.gastonsanchez.com/packyourcode/coin.html)
    + [Methods](https://www.gastonsanchez.com/packyourcode/methods1.html) (by Sanchez)
- :book: __Reading__:
    + [Package Structure](http://r-pkgs.had.co.nz/package.html) (R packages by Wickham)
    + See package components: [http://r-pkgs.had.co.nz/](http://r-pkgs.had.co.nz/) (R packages by Wickham)
- :microscope: __Lab__:
    + [HTML and Web scraping](labs/lab12-web-scraping.md) (due Apr-26)
- :bulb: __Cheat sheet__:
    + [Package Development cheat sheet](cheatsheets/packages-cheatsheet.pdf)
- :dart: __WORK-OUT 3__: 
    + [R Package](hws/workout03.pdf)


-----


## 13. R Packaging (part 2)

- :card_index: __Dates__: Dec 02-06
- :paperclip: __Topics__: Creating an R package can seem overwhelming at first. So we'll keep working on the creation of a relatively basic package. This will give you the opportunity to apply most of the concepts seen in the course.
- :file_folder: __Notes__:
    + [Pack YouR Code](https://www.gastonsanchez.com/packyourcode) (by Sanchez)
- :book: __Reading__:
    + See package components: [http://r-pkgs.had.co.nz](http://r-pkgs.had.co.nz/) (R packages by Wickham)
- :microscope: __Lab__:
    + Take advantage of lab discussion to work on the workout03 assignment
- :bulb: __Cheat sheet__:
    + [Package Development cheat sheet](cheatsheets/packages-cheatsheet.pdf)
- :dart: __WORK-OUT 3__:
    + _Keep working on your workout03 assignment._ (due May-03)



-----


## 14. RRR Week and Final Exam

- :card_index: __Dates__: May 06-10
- :paperclip: __Topics__: Prepare for final examination
- :file_folder: __Notes__:
    + No lecture. Instructor will hold OH (in 309 Evans)
- :mortar_board: __FINAL__: May-15th, 7-10 pm, in Wheeler 150
    + More details about the final will be posted on bCourses


-----
