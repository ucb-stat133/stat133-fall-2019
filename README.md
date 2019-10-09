# Stat 133: Concepts in Computing with Data

- [Policies](syllabus/policies.md)
- [Staff](syllabus/staff.md)
- [FAQs](syllabus/faqs.md)


-----


## Calendar

+ __Instructor:__ Gaston Sanchez
+ __Lecture:__ MWF 9:00-10:00am, 245 Li Ka Shing
+ __OH:__ MWF 10:30am - 11:30am, 309 Evans
+ Tentative topics and dates, subject to change depending on the pace of the course.
+ Notes (:pencil:) involves material discussed in lecture.
+ Reading (:book:) involves material that expands lecture topics, as well as coding examples that you should review/practice outside of class.


-----


## 0. Course Introduction

- :card_index: __Dates__: Aug-28
- :speech_balloon: __Topics__: Welcome to Stat 133. We begin with the usual review of the course policies, logistics, overall expectations, topics in a nutshell, etc.
- :pencil: __Notes__:
    + Welcome to Stat 133 (talk and chalk)
- :book: __Reading__:
    + [Course policies](syllabus/policies.md)
    + [FAQs](syllabus/faqs.md)
- :microscope: __Lab__: No lab
- :speaker: __To Do__: 
    + Install [__R__](https://cran.cnr.berkeley.edu/) 
    + Install [RStudio](https://www.rstudio.com/products/rstudio/download/#download) Desktop (open source version, free)


-----


## 1. The Big Picture

- :card_index: __Dates__: Aug-30, Sep-04
- :speech_balloon: __Topics__: Let's start with an unconventional introduction to _computing with data_ using my favorite analogy "Data Analysis is a lot like Cooking". At the conceptual level we'll identify the main stages of the data analysis cycle. Also, we should keep in mind that data analysis projects usually start with a Research Question. In addition, we'll describe how Data can actually be seen from a triangular perspective (i.e. my "3 Views of Data"). 
- :pencil: __Notes__:
    + [Data Analysis is a lot like cooking](slides/stat133-01-dac-cooking.pdf)
    + [Data Analysis Cycle: Example](slides/stat133-02-dac-example.pdf)
    + [The Starting Point: Research Questions](slides/stat133-03-research-question.pdf)
    + [The Three Views of Data](slides/stat133-04-data-perspectives.pdf)
- :book: __Reading__:
    + [What is Data Science?](https://github.com/ucb-stat133/stat133-misc/blob/master/what-is-data-science.pdf)


-----


## 2. R Survival Skills

- :card_index: __Dates__: Sep 04-05, :warning: _mostly in lab_
- :speech_balloon: __Topics__: In addition to the "Big Picture" concepts, you'll begin learning basic survival skills for R. The main idea is to get a first contact with the RStudio workspace, and the Markdown syntax.
- :book: __Reading__:
    + [First contact with R](tutorials/01-intro-to-R.md) (tutorial)
    + [Intro to Rmd files](tutorials/02-intro-to-Rmd-files.md) (tutorial)
    + [Introduction to R Markdown](http://rmarkdown.rstudio.com/lesson-1.html) (by RStudio)
- :bulb: __Cheatsheet__: 
    + [RStudio cheat sheet](cheatsheets/rstudio-IDE-cheatsheet.pdf)
    + [R markdown cheat sheet](cheatsheets/rmarkdown-cheatsheet-2.0.pdf)
    + [Base R](cheatsheets/base-r-cheatsheet.pdf)


-----


## 3. Intro to Data Technologies: Data Types, and Data Objects.

- :card_index: __Dates__: Sep 06-11
- :speech_balloon: __Topics__: How do programming languages and computing environments handle data? To answer this question we'll discuss a couple of fundamental topics such as _data types_ and their implementation in R around _vectors_ and _arrays_. More specifically, we'll focus on concepts like atomicity, vectorization, recycling, and subsetting. Likewise, we will also describe more generic data objects such as lists.
- :pencil: __Notes__:
    + [Data Types](slides/stat133-06-data-types.pdf)
    + [Vectors](slides/stat133-07-vectors.pdf)
    + [Arrays and Factors](slides/stat133-08-arrays-factors.pdf)
    + [Lists](slides/stat133-09-lists.pdf)
- :book: __Reading__:
    + [Intro to vectors](tutorials/03-intro-to-vectors.md) (tutorial)
    + [chapter 20: Vectors](http://r4ds.had.co.nz/vectors.html) (_R for Data Science_ by Grolemund and Wickham)
- :bulb: __Cheatsheet__: 
    + [Base R](cheatsheets/base-r-cheatsheet.pdf)


-----


## 4. Intro to Data Technologies (cont'd): Data Frames

- :card_index: __Dates__: Sep 11-12, :warning: _mostly in lab_
- :speech_balloon: __Topics__: Besides atomic data objects, we also need to talk about R data frames which provide a nice structure to handle tabular data. You will learn how to manipulate data frames from two approaches: 1) using classic bracket notation, and 2) using a more modern and syntactic way following the _data plying_ framework provided by the package `"dplyr"`.
- :pencil: __Notes__:
    + Data Frames [part 1](slides/stat133-10-data-frames1.pdf) 
    + Data Frames [part 2](slides/stat133-11-data-frames2.pdf)
    + ["dplyr" tutorial slides](slides/dplyr-wickham.pdf) (by Hadley Wickham)
- :book: __Reading__:
    + [Introduction to dplyr](https://cran.r-project.org/web/packages/dplyr/vignettes/dplyr.html) (by Hadley Wickham)
    + [tibbles vignette](https://cran.r-project.org/web/packages/tibble/vignettes/tibble.html)
- :bulb: __Cheatsheet__: 
    + [Data transformation cheat sheet](cheatsheets/data-transformation-cheatsheet.pdf)


-----


## 5. Housekeeping: Filesystem and Bash Commands

- :card_index: __Dates__: Sep 13-16
- :speech_balloon: __Topics__: At the lowest level, Data Analysis Projects (DAPs) are essentially made of files and directories. Therefore, we need to review some fundamental concepts such as the file-system, the command line interface, and some basic shell commands.
- :pencil: __Notes__:
    + [Filesystem Basics](slides/stat133-12-filesystem-basics.pdf)
    + [File Paths](slides/stat133-13-file-paths.pdf)
    + [Shell Basics](slides/stat133-14-shell-basics.pdf)
    + [Command Line](slides/stat133-15-command-line.pdf)
    + [Working with files](slides/stat133-16-working-with-files.pdf)
- :book: __Reading__:
    + [Linux Tutorial](https://ryanstutorials.net/linuxtutorial/) lessons 1-5 (by Ryan Chadwick)
    + [The Unix Shell](http://swcarpentry.github.io/shell-novice/) lessons 1-3 (by Software Carpentry)
    + [Linux Command Line tutorial](https://www.guru99.com/terminal-file-manager.html) (by Guru99)
- :bulb: __Cheat sheet__:
    + [command line cheat sheet](cheatsheets/command-line-cheatsheet.pdf)


-----


## 6. Data Tables: Storage, Organization, Importing, and Unix filters

- :card_index: __Dates__: Sep 18-25
- :speech_balloon: __Topics__: We continue with a fundamental topic of data technologies: _Data Tables_, the most common form in which data is stored, handled, and manipulated. Because datasets in tabular format are so ubiquitous, we need to talk about how tables are typically stored, learn good principles of data organization, and the so-called notion of "tidy data". You will also learn how to perform basic manipulation of data-table files with some unix filters. Also, we'll examine the relationship between tables and R data frames, as well as some considerations when importing (and exporting) tables in R.
- :pencil: __Notes__:
    + [Data Tables](slides/stat133-23-data-tables.pdf) (introduction)
    + [Spreadsheets](slides/stat133-24-data-spreadsheets.pdf)
    + Unix command line: Redirection and Pipes
    + Unix filters: `cut`, `sort`, `uniq`
    + Importing tables [part 1](slides/stat133-24-importing-tables1.pdf) and [part 2](slides/stat133-25-importing-tables2.pdf)
- :book: __Reading__:
    + [Organizing data in spreadsheets](http://kbroman.org/dataorg/) (by Karl Broman)
    + [Intro to Data Technologies](https://www.stat.auckland.ac.nz/~paul/ItDT/itdt-2010-11-01.pdf) (preface, chapter 1, and chapter 5) (by Paul Murrell)
    + [Tidy Data](https://github.com/ucb-stat133/stat133-misc/blob/master/tidy-data-wickham.pdf) (by Hadley Wickham)
- :bulb: __Cheat sheet__:
    + [command line cheat sheet](cheatsheets/command-line-cheatsheet.pdf)


-----


## 7. Housekeeping: Version Control with Git and GitHub

- :card_index: __Dates__: Oct -02-03, :warning: _mostly in lab_
- :speech_balloon: __Topics__: We continue talking about filestructure topics, and we introduce basic notions of version control systems (VCS) using Git, and the companion hosting platform GitHub.
- :pencil: __Notes__:
    + [Git Basics](slides/stat133-19-git-intro.pdf)
    + [Git Workflow](slides/stat133-20-git-workflow.pdf)
- :book: __Reading__:
    + Read sections 4 to 9 in Part I [Installation](https://happygitwithr.com/install-git.html) (_Happy Git and GitHub for the useR_ by Jenny Bryan et al.)
- :bulb: __Cheat sheet__:
    + [Data import cheat sheet](cheatsheets/data-import-cheatsheet.pdf)
    + [git cheat sheet](cheatsheets/git-cheatsheet.pdf)


-----


## 8. Data Visualization

- :card_index: __Dates__: Sep 30, Oct-09
- :speech_balloon: __Topics__: Paraphrasing the old saying "a graphic is word a thousand numbers". No other means of data representation allows us to understand data than visual displays. But in order to make good graphics we need to learn the fundamental concepts for data visualization.  
- :pencil: __Notes__:
    + [Datavis: Classic Examples](slides/stat133-26-datavis-classic-examples.pdf) and [Introduction](slides/stat133-27-datavis-intro.pdf)
    + [Datavis: Encoding Data in Graphs](slides/stat133-28-encoding-data-in-graphs.pdf)
    + [Datavis: The Visual System](slides/stat133-30-visual-system.pdf)
    + [Datavis: Using Color](slides/stat133-32-using-color.pdf)
    + [Datavis: Effective Charts](slides/stat133-33-effective-charts.pdf)
    + [Stephen Few's Data Visualization](slides/show-me-the-numbers-Few.pdf)
- :book: __Reading__:
    + ["ggplot2" lecture](slides/ggplot-karthik.pdf) (by Karthik Ram)
- :bulb: __Cheat sheet__:
    + [Data visualization with ggplot2](cheatsheets/ggplot2-cheatsheet-2.1.pdf)
- :mortar_board: __MIDTERM 1__: Friday Oct-11


-----


## 9. Transition to Programming Basics for Data Analysis (part 1)

- :card_index: __Dates__: Oct 14-18
- :speech_balloon: __Topics__: You don’t need to be an expert programmer to be a data scientist, but learning more about programming allows you to automate common tasks, and solve new problems with greater ease. We'll discuss how to write basic functions, the notion of R expressions, and an introduction to conditionals. 
- :pencil: __Notes__:
    + [Creating functions](tutorials/06-creating-functions.md) (tutorial)
    + [Introduction to functions](tutorials/07-intro-to-functions.md) (tutorial)
    + [Introduction to R expressions and conditionals](tutorials/08-intro-to-expressions-conditionals.md) (tutorial)
- :book: __Reading__:
    + [chapter 19: Functions](http://r4ds.had.co.nz/functions.html) (_R for Data Science_ by Grolemund and Wickham)


-----


## 10. Programming Basics for Data Analysis (part 2)

- :card_index: __Dates__: Oct 21-25
- :speech_balloon: __Topics__: In addition to writing functions to reduce duplication in your code, you also need to learn about iteration, which helps you when you need to do the same operation several times. Namely, we review control flow structures such as `for` loops, `while` loops, `repeat` loops, and the `apply` family functions.
- :pencil: __Notes__:
    + [Introduction to loops](tutorials/09-intro-to-loops.md) (tutorial)
    + [More about functions](tutorials/10-more-functions.md) (tutorial)
    + [Functions](http://adv-r.had.co.nz/Functions.html) (_Advanced R_ by H. Wickham)
- :book: __Reading__:
    + [Environments](http://adv-r.had.co.nz/Environments.html) (_Advanced R_ by H. Wickham)


-----


## 11. Testing Functions

- :card_index: __Dates__: Oct 28-Nov 01
- :speech_balloon: __Topics__: We begin with an introduction to the package `"testthat"` which provides a nice framework for testing functions. Jointly, we will discuss Shiny apps which provide an interesting companion to R, making it quick and simple to deliver interactive analysis and graphics on any web browser. In lab, you'll learn how to perform basic manipulation of strings. 
- :pencil: __Notes__:
    + [Intro to testing functions](tutorials/11-testing-functions.md) (tutorial)
    + [shiny tutorial](slides/shiny-tutorial.pdf) (by Grolemund)    
- :book: __Reading__:
    + [testthat: Get started with testing](papers/testthat-wickham.pdf) (by Wickham)
    + [Character strings in R](http://www.gastonsanchez.com/r4strings/chars.html) (_r4strings_ by Sanchez)
    + [Basic string manipulations](http://www.gastonsanchez.com/r4strings/manip.html) (_r4strings_ by Sanchez)
    + [chapter 14: Strings](http://r4ds.had.co.nz/strings.html) (_R for Data Science_ by Grolemund and Wickham)
- :bulb: __Cheat sheet__:
    + [Stringr cheat sheet](cheatsheets/stringr-cheatsheet.pdf)


-----


## 12. Shiny Apps

- :card_index: __Dates__: Oct 28-Nov 01
- :speech_balloon: __Topics__: We will discuss Shiny apps which provide an interesting companion to R, making it quick and simple to deliver interactive analysis and graphics on any web browser.
- :pencil: __Notes__:
    + [shiny tutorial](slides/shiny-tutorial.pdf) (by Grolemund)    
- :book: __Reading__:
    + [testthat: Get started with testing](papers/testthat-wickham.pdf) (by Wickham)
    + [Character strings in R](http://www.gastonsanchez.com/r4strings/chars.html) (_r4strings_ by Sanchez)
    + [Basic string manipulations](http://www.gastonsanchez.com/r4strings/manip.html) (_r4strings_ by Sanchez)
    + [chapter 14: Strings](http://r4ds.had.co.nz/strings.html) (_R for Data Science_ by Grolemund and Wickham)
- :bulb: __Cheat sheet__:
    + [Stringr cheat sheet](cheatsheets/stringr-cheatsheet.pdf)


-----


## 13. More Shiny Apps and Introduction to Regular Expressions

- :card_index: __Dates__: Nov 04-08
- :speech_balloon:  __Topics__: Random numbers have many applications in science and computer programming, especially when there are significant uncertainties in a phenomenon of interest. In this part of the course we'll look at some basic problems involving working with random numbers and creating simulations. Additionally, we continue the discussion about character strings with a first contact to Regular Expressions. 
- :pencil: __Notes__:
    + [Introduction to random numbers](tutorials/12-intro-to-random-numbers.md)
    + [Coin toss shiny app](https://github.com/ucb-stat133/stat133-fall-2018/tree/master/apps/coin-toss)
    + [Regexpal](http://regexpal.com.s3-website-us-east-1.amazonaws.com/) tester tool.
- :book: __Reading__:
    + [Part 1 - How to build a Shiny app](https://vimeo.com/rstudioinc/review/131218530/212d8a5a7a/#t=0m0s) (video)
    + [Part 2 - How to customize reactions](https://vimeo.com/rstudioinc/review/131218530/212d8a5a7a/#t=42m2s) (video)
    + [Part 3 - How to customize appearance](https://vimeo.com/rstudioinc/review/131218530/212d8a5a7a/#t=1h32m41s) (video)
- :bulb: __Cheat sheet__:
    + [shiny cheat sheet](cheatsheets/shiny-cheatsheet.pdf)


-----


## 14. More Regular Expressions

- :card_index: __Dates__: Nov 11-15
- :speech_balloon:  __Topics__: At its heart, computing involves working with numbers. However, a considerable amount of information and data is in the form of text. To unleash the power of strings manipulation, we need to take things to the next level and learn about Regular Expressions. Namely, Regular expressions are a tool that allows us to describe a certain amount of text called "patterns". We'll describe the basic concepts of regex and the common operations to match text patterns.
- :pencil: __Notes__:
    + [Long Jump World Record example](https://www.gastonsanchez.com/r4strings/cleaning.html)
    + [Log file example](https://www.gastonsanchez.com/r4strings/logs.html)
- :book: __Reading__:
    + [Handling Strings in R](https://www.gastonsanchez.com/r4strings) (by Sanchez)
- :bulb: __Cheat sheet__:
    + [Regular Expressions cheat sheet](cheatsheets/regular-expressions-cheatsheet.pdf)


-----


## 15. R packaging (part 1)

- :card_index: __Dates__: Nov 18-22
- :speech_balloon: __Topics__: Packages are the fundamental units of reproducible R code. They include reusable functions, the documentation that describes how to use them, and sample data. In this part we'll start describing how to turn your code into an R package.
- :pencil: __Notes__:
    + [Programming S3 Classes](https://www.gastonsanchez.com/packyourcode/coin.html)
    + [Methods](https://www.gastonsanchez.com/packyourcode/methods1.html) (by Sanchez)
- :book: __Reading__:
    + [Package Structure](http://r-pkgs.had.co.nz/package.html) (R packages by Wickham)
    + See package components: [http://r-pkgs.had.co.nz/](http://r-pkgs.had.co.nz/) (R packages by Wickham)
- :bulb: __Cheat sheet__:
    + [Package Development cheat sheet](cheatsheets/packages-cheatsheet.pdf)


-----


## 16. R Packaging (part 2)

- :card_index: __Dates__: Dec 02-06
- :speech_balloon: __Topics__: Creating an R package can seem overwhelming at first. So we'll keep working on the creation of a relatively basic package. This will give you the opportunity to apply most of the concepts seen in the course.
- :pencil: __Notes__:
    + [Pack YouR Code](https://www.gastonsanchez.com/packyourcode) (by Sanchez)
- :book: __Reading__:
    + See package components: [http://r-pkgs.had.co.nz](http://r-pkgs.had.co.nz/) (R packages by Wickham)
- :bulb: __Cheat sheet__:
    + [Package Development cheat sheet](cheatsheets/packages-cheatsheet.pdf)


-----


## 17. RRR Week and Final Exam

- :card_index: __Dates__: Dec 09-13
- :speech_balloon: __Topics__: Prepare for final examination
- :pencil: __Notes__:
    + No lecture. Instructor will hold OH (in 309 Evans)
- :mortar_board: __FINAL__: Dec-19th, 7-10 pm, room TBD
    + More details about the final will be posted on bCourses


-----
