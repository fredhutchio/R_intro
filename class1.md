Introduction to R, Class 1: Functions and objects
================

<!--class1.md is generated from class1.Rmd. Please edit that file -->

## Objectives

Welcome to Introduction to R from fredhutch.io\! This course introduces
you R by working through common tasks in data science: importing,
manipulating, and visualizing data.

R is a statistical and programming computer language widely used for a
variety of applications. For more information about R and ways to use it
at Fred Hutch, please see the [R and
RStudio](https://sciwiki.fredhutch.org/scicomputing/software_R/) entry
for the Fred Hutch Biomedical Data Science Wiki.

Before proceeding with these training materials, please ensure you have
installed both R and RStudio as described
[here](http://www.fredhutch.io/software/#r-and-rstudio).

By the end of this session, you should be able to:

  - work within the RStudio interface to run and save R code in a
    project
  - understand basic R syntax to use functions and assign objects
  - create and manipulate vectors and understand how R deals with
    missing data

## A brief orientation to RStudio

[R](https://cran.r-project.org) is a statistical programming language,
while [RStudio](https://rstudio.com) is an integrated development
environment (IDE) that allows you to code in R more easily. RStudio
possesses many features that you may find useful in your work. We’ll
highlight a few of the most common and useful parts for our introductory
course.

The first time you open RStudio, you’ll see three panels, or windows.

1.  The panel on the left is the console, where you can run R code. The
    text printed in this panel is basic information about R and the
    version you’re running. You can test how the console can be used to
    run code by entering `3 + 4` and then pressing enter. This instructs
    your computer to read, interpret, and execute the command, then
    print the result (`7`) to the Console, and show a right facing arrow
    (`>`), indicating it is ready to accept additional code.
2.  The panel on the top right is the environment. It’s empty right now,
    but we’ll learn more about this later in this lesson.
3.  The panel on the lower right shows the files present in your working
    directory. Currently, that’s probably your `Home` directory, which
    includes folders like `Documents` and `Downloads`.

You may notice that some of the panels possess additional tabs. We’ll
explore some of these features in this class, but for more information:

`Help -> Cheetsheets -> RStudio IDE cheat sheet`

This PDF includes an overview of each of the things you see in RStudio,
as well as explanations of how you can use them. It may be intimidating
right now, but will come in handy as you gain experience with R.

One of the ways that RStudio makes working in R easier is by allowing
you to create R projects. You can think of a project as a discrete unit
of work, such as a chapter of a thesis/dissertation, analysis for a
manuscript, or a monthly report. We recommend organizing your code,
data, and other associated files as projects, which allows you to keep
all parts of an analysis together for easier access.

We’ll be creating a project to use for the duration of this course.
Create a new project in RStudio:

  - `File -> New Project`
  - Choose `New Directory`, then `New Project`
  - name your project `intro_r` and save it somewhere on your computer
    you’ll be able to find easily later (we recommend your Desktop or
    Documents)
  - Click `Create project`

After your RStudio screen reloads, note two things:

  - The file browser in the lower right panel will now show the contents
    of a new folder, `intro_r`, that was created as a part of your
    RStudio project.
  - The console window will show the path, or location in your computer,
    for your project directory. This is important later in class, when
    this path will be required to locate data for analysis.

Now we’re ready to create a new R script:

  - `File -> New File -> R Script`
  - Save the new file as `class1.R`. By default, RStudio will save this
    in your project directory.

This R script is a text file that we’ll use to save code we learn in
this class. We’ll refer to this window as the script or source window.
Remember to save this file periodically to retain the record of the work
you’re doing, so you can re-execute the code later if necessary.

By convention, a script should include a title at the top, so type the
following on the first line:

`# Introduction to R: Class 1`

## Using functions

Now that we have a project and new script set up, we’re ready to begin
adding code. Skipping a line after the title, type the following on the
next two lines:

``` r
# basic math
4 + 5 
```

    ## [1] 9

The first of the two boxes above represents the code you execute. The
second box (prefaced with `##`) shows the output you should expect. The
`[1]` in the second box means there is one item (in this case, `9`)
present in the output.

The first line in that example is a code comment. It is not interpreted
by R, but is a human-readable explanation of the code that follows. This
is also how we included a title in our script. In R, anything to the
right of one or more `#` symbols represents a comment.

The code above is the same mathematical operation we executed earlier.
If we wanted to re-run this command, we have two options:

1.  Copy and paste the code into the Console
2.  Use the `Run` button at the top of the script window
3.  Use the keyboard shortcut: `Ctrl + Enter`

The third option is the most efficient, especially as your coding skills
progress. With your cursor on the line with `4 + 5`, hold down the
`Control` key and press `Enter`. You’ll see the code and answer both
appear in the Console. A few things to note about this keyboard
shortcut:

  - It doesn’t matter where your cursor is on the line of code; the
    entire line will be executed with the keyboard shortcut.
  - If there isn’t code on the line where your cursor is located,
    RStudio will attempt to execute following lines.

In practice, a script should represent code you are developing in R, and
you should only save the code that you know functions. For this class,
we’ll be including notes about things we learn as comments.

> `Ctrl + Enter` is the only keyboard shortcut we emphasize in this
> course, but there are many others available. You can view them on the
> second page of the cheat sheet linked above, or by going to `Help ->
> Keyboard Shortcuts Help`.

If you were looking carefully, you may have noticed that the `+` in the
previous code example had spaces on either side, separating it from the
numbers. You may wonder whether spaces matter in how the code is
interpreted. As with many questions in coding, the easiest way to assess
whether removing the spaces matters is to simply try it:

``` r
# same code as above, without spaces
4+5
```

    ## [1] 9

Given the output, we can conclude that spaces do not matter in how the
code functions. In this case, however, spaces represent a common
convention in formatting R code, as it makes it easier for human eyes to
read. In general, you should attempt to replicate the code presented
here as closely as possible, and we’ll do our best to note when
something is required as opposed to convention.

> Code convention and style doesn’t make or break the ability of your
> code to run, but it does affect whether other people can easily
> understand your code. A brief overview of common code style is
> available [here](http://adv-r.had.co.nz/Style.html), and more
> information is available in the [tidyverse style
> guide](https://style.tidyverse.org).

So far, we’ve used R with mathematical symbols representing operations.
R possesses the ability to perform much more complex tasks using
functions, which is a pre-defined set of code that allows you to repeat
particular actions.

R includes functions for other types of math:

``` r
# using a function: rounding numbers
round(3.14)
```

    ## [1] 3

In this case, `round` is the function, and `3.14` is the number (data)
being manipulated by the funcion. A word followed by parentheses is a
common format for functions in R.

> Syntax refers to the rules that dictate how combinations of words and
> symbols are interpreted in a language (either programming or human).

Additional options for modifying functions are called arguments, and are
included with the data between parentheses. For the `round` function, a
common modification would be the number of decimal points output. You
can change this detail by adding a comma and then additional argument:

``` r
# using a function with more arguments
round(3.14, digits = 1)
```

    ## [1] 3.1

If you would like to learn more about how this function works, you can
go to the bottom righthand panel and click on the `Help` tab. Enter the
name of a function into the search box and hit `Enter`. Alternatively,
execute the following in your console:

`?round`

This is a shortcut for performing the same task in the panel described
above.

R help documentation tends to be formatted very consistently. At the
very top, you’ll see the name of the function. Below that, a short title
indicates the purpose of the function, along with a more verbose
“Description”. “Usage” tells you how to use the function in code, and
“Arguments” details each of the optiond in “Usage”. The rest of the
subheadings should be self-explanatory.

In the example above, there is no label associated with `3.14`. In
reality, `3.14` represents `x`, so the command can actually be written
as `round(x = 3.14, digits = 1)`. Even if not explicitly stated, the
computer assumes that `3.14` represents `x` if the number is the first
thing that appears after the opening parenthesis.

If you define both arguments explicitly, you can switch the order in
which they appear:

``` r
# can switch order of arguments
round(digits = 1, x = 3.14)
```

    ## [1] 3.1

If you remove the labels (`round(1, 3.14)`), the answer is different,
because R is assuming you mean `round(x = 1, digits = 3.14)`.

> You may notice that boxes pop up as you type. These represent
> RStudio’s attempts to guess what you’re typing and share additional
> options.

> #### Challenge-hist
> 
> What does the function `hist` do? What are its main arguments? How did
> you determine this?

## Assigning objects

So far, we’ve been performing tasks with R that require us to input the
data manually. One of the strengths of using a programming language is
the ability to assign data to objects, or variables.

> Objects in R are referred to as variables in other programming
> languages. We’ll use these terms synonymously for this course, though
> in other contexts there may be differences between them. Please see
> the [R documentation on
> objects](https://cran.r-project.org/doc/manuals/r-release/R-lang.html#Objects)
> for more information.

Like in math, a variable is a word used to represent a value (in this
case, a number):

``` r
# assigning value to an object
weight_kg <- 55
```

In the code above, `<-` is the assignment operator: it instructs R to
recognize `weight_kg` as representing the value 55. You can think of
this code as referencing “55 goes into weight\_kg.”

After executing the code above, you’ll see the object appear in the
Environment panel on the upper right hand side of the RStudio screen.
The name of the object will appear on the left, with the value assigned
to it on the right.

The name you assign to objects can be arbitrary, but we recommend using
names that are relatively short and meaningful in the context of the
values they represent. It’s useful to also know other general
limitations on object names:

  - case sensitive
  - cannot start with numbers
  - avoid other common words in R (e.g., function names, like `mean`)
  - avoid dots (underscores are a good alternative, such as the example
    above)

Extra information on object names is available in the [tidyverse style
guide](https://style.tidyverse.org/syntax.html#object-names).

Now that the object has been assigned, we can reference that object by
executing its name:

``` r
# recall object
weight_kg
```

    ## [1] 55

Thus, the value `weight_kg` represents is printed to the Console.

We can also perform operations on an object:

``` r
# multiple an object (convert kg to lb)
2.2 * weight_kg
```

    ## [1] 121

In that case, the answer is printed to the Console. You can also assign
the output to a new object:

``` r
# assign weight conversion to object
weight_lb <- 2.2 * weight_kg
```

After executing that line of code, you’ll see `weight_lb` appear in the
Environment panel, too.

Now let’s explore what happens if we assign a value to an existing
object name:

``` r
# reassign new value to an object
weight_kg <- 100
```

Note that the value assigned to `weight_kg` as it appears in the
Environment panel changes after executing the code above.

Has the value assigned to `weight_lb` also changed? You might expect
this would be the case, since this value is derived from `weight_kg`.
However, `weight_kg` remains the same as previously assigned. If you
want the value for `weight_kg` to reflect the new value for `weight_kg`,
you will need to again execute `weight_lb <- 2.2 * weight_kg`. This
should help you understand an important concept in writing code: the
order in which you execute lines of code matters\! In the context of the
material we cover in this class, we’ll continue saving code in scripts
so we have a record of both the relevant commands and the appropriate
order for execution.

> You can think of the names of objects like sticky notes. You have the
> option to place the sticky note (name) on any value you choose. You
> can pick up the sticky note and place it on another value, but you
> need to explicitly tell R when you want values assigned to certain
> objects.

At this point in the lesson, it’s common to have accidentally created an
object with a typo in the name. If this has happened to you, it’s useful
to know how to remove the object to keep your environment up to date.
Here, we’ll practice removing an object with something everyone has
available:

``` r
# remove object
remove(weight_lb) 
```

This removes the specified object from the environment, which you can
confirm by its absence in the Environment panel. You can also abbreviate
this command to `rm(weight_lb)`.

> You can clear the entire environment using the button at the top of
> the Environment panel with a picture of a broom. This may seem
> extreme, but don’t worry\! We can re-create all the work we’ve already
> done by executing each line of code again.

> #### Challenge-values
> 
> For the code chunk below, what is the value of each item at each step?

``` r
mass <- 47.5            # mass?
width  <- 122             # width?
mass <- mass * 2.0      # mass?
width  <- width - 20        # width?
mass_index <- mass/width  # mass_index?
```

## Vectors

So far, we’ve worked with objects containing a single value. For most
research purposes, however, it’s more realistic to work with a
collection of values. We can do that in R by creating a vector with
multiple values:

``` r
# assign vector
ages <- c(50, 55, 60, 65) 
# recall vector
ages
```

    ## [1] 50 55 60 65

The `c` function used above stands for “combine,” meaning all of the
values in parentheses after it are included in the object. This is
reflected in the Console, where recalling the value shows all four
values, and the Environment window, where multiple values are shown on
the right side.

We can use functions to ask basic questions about our vector, including:

``` r
# how many things are in object?
length(ages)
```

    ## [1] 4

``` r
# what type of object?
class(ages)
```

    ## [1] "numeric"

``` r
# get overview of object
str(ages)
```

    ##  num [1:4] 50 55 60 65

In the code above, we learn that there are four items (values) in our
vector, and that the vector is composed of numeric data. `str` stands
for “structure”, and shows us a general overview of the data, including
a preview of the first few values (or all the values, as is the case in
our small vector).

Even more useful is the ability to use functions to perform more complex
tasks for us, such as statistical summaries:

``` r
# performing functions with vectors
mean(ages)
```

    ## [1] 57.5

``` r
range(ages)
```

    ## [1] 50 65

Although we’ve focused on numbers as data so far, it’s also possible for
data to be words instead:

``` r
# vector of body parts
organs <- c("lung", "prostate", "breast")
```

In this case, each word is encased in quotation marks, indicating these
are character data, rather than object names.

> #### Challenge-organs
> 
> Please answer the following questions about `organs`: - How many
> values are in `organs`? - What type of data is `organs`? - How can you
> see an overview of `organs`?

We’ve seen data as numbers and letters so far. In fact, R has all of the
following basic data types:

  - **character**: sometimes referred to as string data, tend to be
    surrounded by quotes
  - **numeric**: real or decimal numbers, sometimes referred to as
    “double”
  - integer: a subset of numeric in which numbers are stored as integers
  - **logical**: Boolean data (TRUE and FALSE)
  - complex: complex numbers with real and imaginary parts (e.g., 1 +
    4i)
  - raw: bytes of data (machine readable, but not human readable)

The three data types listed in **bold** above are the focus of this
class. R automatically interprets the type as you enter data. Most data
analysis activities will not require you to understand specific details
of the other data types.

> #### Challenge-dtypes
> 
> R tends to handle interpreting data types in the background of most
> operations. The following code is designed to cause some unexpected
> results in R. What is unusual about each of the following objects?

``` r
num_char <- c(1, 2, 3, "a")
num_logical <- c(1, 2, 3, TRUE)
char_logical <- c("a", "b", "c", TRUE)
tricky <- c(1, 2, 3, "4")
```

## Manipulating vectors

In the section above, we learned to create and assess vectors, and use
functions to calculate statistics across the values. We can also modify
a vector after it’s been created:

``` r
# add a value to end of vector
ages <- c(ages, 90) 
```

The example above uses the same combine (`c`) function as when we
initially created the vector. We can also use it to add values to the
beginning of the vector:

``` r
# add value at the beginning
ages <- c(30, ages)
```

If we wanted to extract, or subset, a portion of a vector:

``` r
# extracting second value
organs[2] 
```

    ## [1] "prostate"

In general, square brackets (`[ ]`) in R refer to a part of an object.
The number 2 indicates the second value in the vector.

> The index position of a value is the number associated with its
> location in a collection. In the example above, note that R indexes
> (or counts) starting with 1. This is different from many other
> programming languages, like Python, which use 0-based indexing.

In R, a minus sign (`-`) can be used to negate a value’s position, which
excludes that value from the output:

``` r
# excluding second value
organs[-2] 
```

    ## [1] "lung"   "breast"

You may be tempted to try extracting multiple values at a time by
separating the numbers with commas (e.g., `organs[2,3]`). This will
result in a rather cryptic error, which we’ll talk more about next time.
For now, remember that you can use the combine function to indicate
multiple values for subsetting:

``` r
# extracting first and third values
organs[c(1, 3)] 
```

    ## [1] "lung"   "breast"

We’ll switch back to our numerical `ages` object to explore another
common need when subsetting: extracting values based on a condition (or
criteria). For numerical data, we’re often interested in extracting data
that are in a certain range of values. It is tempting to try something
like:

``` r
ages > 60 
```

    ## [1] FALSE FALSE FALSE FALSE  TRUE  TRUE

The result, however, is less than satisfying: you receive either TRUE or
FALSE for each data point, depending on whether it meets the condition
or not.

While that information isn’t quite what we expected, we can combine it
with the subsetting syntax we learned earlier:

``` r
# extracts values which meet condition
ages[ages > 60] 
```

    ## [1] 65 90

If we read the code above from the inside out (a common strategy for R),
the code above identifies which values meet the criteria, and the square
brackets are used to extract this from the original vector.

If you want to extract items exactly equal to a specific value, you need
to use two equal signs:

``` r
# extracts values numerically equivalent values
ages[ages == 60]
```

    ## [1] 60

You can think of this as a way to differentiate mathematical equivalency
from specification of parameters for arguments (such as `digits = 1` for
`round()`, as we learned earlier). R also allows you to use \<= and \>=.

Finally, it’s common to need to combine conditions while subsetting. For
example, you may be interested in only values between 50 and 60:

``` r
# ages less than 50 OR greater than 60
ages[ages < 50 | ages > 60]
```

    ## [1] 30 65 90

In the code above, the vertical pipe `|` is interpreted to mean “or,” so
each data point can belong to either the category on the left of the
pipe, the category on the right, or both. In other words, the vertical
pipe means any single value being evaluated must meet one or both
conditions.

You can also combine conditions with `&`, but this means any single
value must meet **both** conditions:

``` r
# ages greater than 50 OR less than 60
ages[ages > 50 & ages < 60]
```

    ## [1] 55

> Be careful when thinking about human language as opposed to
> programming languges. When speaking, we is reasonable to say “extract
> all values below 50 and above 60.” While this makes sense in context,
> it is mathematically impossible for a value to be both less than 50
> AND greater than 60.

> #### Challenge-compare
> 
> Why does the following code return the answer it

``` r
"four" > "five"
```

    ## [1] TRUE

## Missing data

Most of the data we encounter has missing data. Programming languages
interpret and handle missing data in different ways, so it’s worth
taking time to dig into how R approaches this issue.

First, we’ll create a new vector some values indicated as missing data:

``` r
# create a vector with missing data
heights <- c(2, 4, 4, NA, 6)
```

In the vector above, `NA` represents a value where data are missing. You
may notice `NA` is not encased in quotation marks. This is because R
interprets that set of characters specifically as missing data.

Next, let’s investigate how this vector responds to use in functions:

``` r
# calculate mean and max on vector with missing data
mean(heights)
```

    ## [1] NA

``` r
max(heights)
```

    ## [1] NA

The answer isn’t very satisfying; we’re told the answer is missing data
because of the presence of a single missing value in the vector. This is
a slightly frustrating default behavior for some common statistical
functions in R, but we can add an argument to ignore missing data and
calculate across the remaining values:

``` r
# add argument to remove NA
mean(heights, na.rm = TRUE)
```

    ## [1] 4

``` r
max(heights, na.rm = TRUE)
```

    ## [1] 6

In the code above, the `na.rm` parameter controls whether missing data
are removed. The default (which you can also reference in the help
documentation) is for missing values to be included (`na.rm = FALSE`).
By switching to `na.rm = TRUE`, we’re instructing R to remove missing
data.

The example above retains missing values in the dataset while performing
calculations. There are certainly cases in which you may want to
specifically filter out the missing data from your dataset.

The function `is.na` allows you to ask whether elements in a dataset are
missing:

``` r
# identify elements which are missing data
is.na(heights)
```

    ## [1] FALSE FALSE FALSE  TRUE FALSE

If a resulting value is `TRUE`, the value is missing. If `FALSE`, the
data point is present. We can invert the resulting logical data using an
exclamation point:

``` r
# reverse the TRUE/FALSE
!is.na(heights)
```

    ## [1]  TRUE  TRUE  TRUE FALSE  TRUE

This means missing data are now listed as `FALSE`, with data present as
`TRUE`.

As with the conditional statements we learned earlier, we can combine
these results with our square bracket subsetting syntax to extract only
values that are present in the dataset:

``` r
# extract elements which are not missing values
heights[!is.na(heights)]
```

    ## [1] 2 4 4 6

Alternatively, you can use a function specifically designed for
excluding (omitting) missing data:

``` r
# remove incomplete cases
na.omit(heights) 
```

    ## [1] 2 4 4 6
    ## attr(,"na.action")
    ## [1] 4
    ## attr(,"class")
    ## [1] "omit"

You may notice that this output looks slightly different than the
previous example. This is because `na.omit` includes output about
attributes, or information about the data. The output vectors are the
same for the last two code examples, even though the way they appear in
the Console seems different.

> If you aren’t sure how to interpret the output in your console,
> sometimes it helps to assign the output to an object. You can then
> inspect the data type, structure, etc to ensure you’re getting the
> answer you expected.

> #### Challenge-analyze
> 
> Complete the following tasks after executing the code chunk below.
> (Note: there are multiple solutions): - Remove NAs - Calculate the
> median - Identify how many elements in the vector are greater than 67
> inches - Visualize the data as a histogram (hint: function `hist`)

``` r
# create vector
more_heights <- c(63, 69, 60, 65, NA, 68, 61, 70, 61, 59, 64, 69, 63, 63, NA, 72, 65, 64, 70, 63, 65)
```

## Wrapping up

In this session, we spent some time getting to know the RStudio
interface for writing and running R code, explored the basic principles
of R syntax for functions and object assignment, and worked with vectors
to understand how R handles missing data.

In the next session, we’ll learn to import spreadsheet-style data that
are more similar to what you’d like handle for a research project, and
practice accessing different portions of the data.

**When you are done working in RStudio,** you should save any changes to
your R script. When you close RStudio, you will see a pop-up box asking
if you want to save your workspace image. We do not recommend saving
your project in this way, as it creates extra (hidden) files on your
computer that can be unwieldy in size and inadvertently retain sensitive
data (if you’re working with PHI or other private data). If you’ve saved
your R script, you can recreate all the work you’ve accomplished. For
more information on this topic, please review [this
explanation](https://www.stat.ubc.ca/~jenny/STAT545A/block01_basicsWorkspaceWorkingDirProject.html#workspace-.rdata).
If you would like to prevent this box from popping up in the future, we
recommend:

  - Go to `Tools -> Global Options` (Global means for all projects; you
    can also change this for each project using `Project Options`)
  - In the drop-down menu next to `Save workspace to ~/.Rdata on exit`
    select `Never`.

**If you need to reopen your project after closing RStudio,** you should
use the `File -> Open Project` and navigate to the location of your
project directory. Alternatively, using your operating system’s file
browser, double click on the `r_intro.Rrpoj` file.

**This document is written in [R
markdown](http://rmarkdown.rstudio.com),** which is a method of
formatting text, code, and output to create documents that are sharable
with other people. While this document is intended to serve as a
reference for you to read while typing code into your own script, you
may also be interested in modifying and running code in the original R
markdown file ([`class1.Rmd`](class1.Rmd) in the GitHub repository).

The course materials webpage is available [here](README.md). Materials
for all lessons in this course include:

  - [Class 1](class1.md): R syntax, assigning objects, using functions
  - [Class 2](class2.md): Data types and structures; slicing and
    subsetting data
  - [Class 3](class3.md): Data manipulation with `dplyr`
  - [Class 4](class4.md): Data visualization in `ggplot2`

## Extra exercises

Answers to all challenge exercises are available [here](solutions/).

#### Challenge-objects

  - Create an object called agge that contains your age in years
  - Reassign the object to a new object called age (e.g., correct the
    typo)
  - Remove the previous object from your environment
  - Calculate your age in days

#### Challenge-num

  - create a object representing a vector that contains the names of
    buildings on Fred Hutch’s campus:
    <https://www.fredhutch.org/en/contact-us/visit-us.html>
  - add Seattle, Washington to the beginning of the vector, and Steam
    Plant to the end of the vector
  - subset the vector to show only the building in which you work

#### Challenge-char

The following vector represents the number of vacation days possessed by
various employees:

``` r
vacation_days <- c(5, 7, 20, 1, 0, 0, 12, 4, 2, 2, 2, 4, 5, 6, 7, 10, 4)
```

  - How many employees are represented in the vector?
  - How many employees have at least one work week’s worth of vacation
    available to them?
