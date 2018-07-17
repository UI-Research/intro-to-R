# Day 4

## The Goal

1) Create a directory for an analysis
2) Create a .Rproj
3) Create a .Rmd document
4) Load data (.csv or .xlsx)
5) Munge the data into a useful format
6) Create a summary statistic
7) Create a data visualization
8) "Knit" the R Markdown document into a .html document

## R Markdown

### Motivation
1) Copying-and-Pasting is boring and dangerous
2) It's easy for analyses and narratives to get out-of-sequence
3) Parallel documents: R Markdown can be a lab notebook where ideas and computations are combined instead of kept in two places
4) Is code written for machines or humans?

**The answer:** Literate (Statistical) Programming

![](images/rmarkdown.png)


[Gallery](https://rmarkdown.rstudio.com/gallery.html)

[Cheat sheet](https://github.com/rstudio/cheatsheets/raw/master/rmarkdown-2.0.pdf)

### 1. YAML header
* Control the options and parameters of the document. Options include title, author, output format, and styles. 

### 2. Markdown text
* Simplified markup language for styling plain text. 

`#` creates header 1

`##` creates header 2

`###` creates header 3

`*` creates a bullet point

`1.` creates an ordered list

### 3. R Code

#### Code chunks (optional)

*Unnamed*

    ```{r}
    mean(apples)
    ````

*Named*

    ```{r code-chunk-name}
    mean(apples)
    ````
    
#### In-line code

    `r mean(apples)`

### "Knit" the document

## The Owl
Statistical programming, data visualization, and social and economic policy research are difficult. Four hours isn't enough to master R. The goal of this training is to offer hands-on experience and enough comfort that a beginner can ask the right question when hitting his or her first wall. 

## More resources

* [R Markdown brown bag resources and video](https://urbanorg.box.com/s/da80g5cpszv7yh4byne4jjascxqs27ih)
* [RStudio R Markdown page](https://rmarkdown.rstudio.com/)
* [R Markdown fact sheets](https://github.com/UrbanInstitute/rmarkdown-factsheets)
* [R Markdown html resources](https://github.com/UrbanInstitute/rmarkdown-resources)
