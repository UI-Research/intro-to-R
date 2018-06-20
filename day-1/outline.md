# Day 1

## The Owl
Statistical programming, data visualization, and social and economic policy research are difficult. Four hours isn't enough to master R. The goal of this training is to offer hands-on experience and enough comfort that a beginner can ask the right question when hitting his or her first wall. 

## Why program?
* To create a script of all steps in an analysis. 
    * Easy communication with others and your future self.
    * Easy to start over. 
    * "I live in fear of clicking the wrong thing". ~ Hadley Wickham
    * "Code as the primary data artifact of a data analysis." ~ Hadley Wickham
* Efficient and scalable.
* Aren't limited to the tools created by a developer. More flexibility.
* Stack overflow as a tool for debugging. Others have experienced your issue first!

## Why R?
* Free!
* Open source
* Powerful and extensible
    * Domain specific languages

## How do I turn this thing on?
* Difference between R and R Studio
* R is a calculator
    * Submit code to the console
    * Submit code from scripts

## Basic syntax
* `<-` is the assignment operator
* `#` begins a comment
* `?` searches for functions and data sets. Drop the parentheses!
* `%>%` is the pipe operator
* `c()` is concatenate

## Functions
* R is based on functions of the form `mean()`, `median()`, `min()`, and `max()`. R has powerful tools for creating custom functions. 

## R packages
* `install.packages("tidyverse")`
* `library(tidyverse)`
* R has powerful tools for creating custom packages. 

## Rectangles
* `tidyverse`
* The idea is to only use one data structure, and a host of functions that are specialized to that data structure.
* View()
* glimpse()

## `library(dplyr)`
* Seven-point-five functions:
  1. `select()` (use `-` to drop variables)
  2. `rename()` (new name = old name)
  3. `filter()` with (`==`, `>`, `<`, `>=`, `<=`, `!`, `is.na()`, `&`, `|`, and `%in%`).
  4. `arrange()` and `desc()`
  5. `mutate()`
  6. `summarize()`
  7. `group_by()`

## More resources
* [R for Data Science](http://r4ds.had.co.nz/)
* [Urban Institute intro to R page](https://ui-research.github.io/r-at-urban/intro-to-r.html)
* [Tidy Data-Hadley Wickham](http://vita.had.co.nz/papers/tidy-data.html)
* [You can't do data science with a GUI](https://www.youtube.com/watch?v=cpbtcsGE0OA)
