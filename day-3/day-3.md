Day 3 - Loading Data
====================

(Almost) All You Need
---------------------

``` r
library(readr)
df <- read_csv(file = 'path/to/file')
```

A quick demo:

``` r
df <- readr::read_csv('data/example.csv')
```

    ## Parsed with column specification:
    ## cols(
    ##   x = col_integer(),
    ##   y = col_character()
    ## )

``` r
head(df)
```

    ## # A tibble: 6 x 2
    ##       x y            
    ##   <int> <chr>        
    ## 1    72 Kansas       
    ## 2    60 Missouri     
    ## 3   142 Mississippi  
    ## 4   251 New Hampshire
    ## 5   355 Hawaii       
    ## 6   242 West Virginia

The `readr` Package
-------------------

Load the `readr` package. We'll also load `dplyr` for some data cleaning.

``` r
library(readr)
library(dplyr)
```

To import your data, `readr` does three things:

1.  Read your file and parse it into a matrix of strings
2.  Determine the type of each column
3.  Parse each column into its specific type

``` r
read_delim('x,y,z\n1,2.5,apple', delim = ',')
```

    ## # A tibble: 1 x 3
    ##       x     y z    
    ##   <int> <dbl> <chr>
    ## 1     1   2.5 apple

``` r
read_delim('x|y|z\n1|2.5|3', delim = '|')
```

    ## # A tibble: 1 x 3
    ##       x     y     z
    ##   <int> <dbl> <int>
    ## 1     1   2.5     3

The `read_csv` and `read_tsv` are convenience wrappers around `read_delim`, with the `delim` argument pre-set for you.

``` r
read_csv('x,y,z\n1,2,3')
```

    ## # A tibble: 1 x 3
    ##       x     y     z
    ##   <int> <int> <int>
    ## 1     1     2     3

``` r
read_tsv('x\ty\tz\n1\t2\t3')
```

    ## # A tibble: 1 x 3
    ##       x     y     z
    ##   <int> <int> <int>
    ## 1     1     2     3

Parsing Issues
--------------

Sometimes there will be an issue in your data file and `readr` will return a parsing failure.

``` r
df <- read_csv('data/parsing_failure.csv')
```

    ## Parsed with column specification:
    ## cols(
    ##   x = col_integer(),
    ##   y = col_character()
    ## )

    ## Warning in rbind(names(probs), probs_f): number of columns of result is not
    ## a multiple of vector length (arg 2)

    ## Warning: 1 parsing failure.
    ## row # A tibble: 1 x 5 col     row col   expected               actual file                       expected   <int> <chr> <chr>                  <chr>  <chr>                      actual 1  1001 x     no trailing characters .16    'data/parsing_failure.csv' file # A tibble: 1 x 5

``` r
tail(df)
```

    ## # A tibble: 6 x 2
    ##       x y           
    ##   <int> <chr>       
    ## 1    67 Wisconsin   
    ## 2   294 Pennsylvania
    ## 3    75 Mississippi 
    ## 4   250 Illinois    
    ## 5   330 Nebraska    
    ## 6    NA Virginia

You can use the `problems` function to convert the output into a `tibble` as you work through the issues:

``` r
failures <- problems(df)
failures
```

    ## # A tibble: 1 x 5
    ##     row col   expected               actual file                      
    ##   <int> <chr> <chr>                  <chr>  <chr>                     
    ## 1  1001 x     no trailing characters .16    'data/parsing_failure.csv'

The issue is that the `read_*` functions will read in the first 1000 lines of a file and use that to guess the column type. The `guess_max` argument can be set higher if needed.

``` r
df <- read_csv('data/example.csv', guess_max = 1001)
```

    ## Parsed with column specification:
    ## cols(
    ##   x = col_integer(),
    ##   y = col_character()
    ## )

``` r
tail(df)
```

    ## # A tibble: 6 x 2
    ##       x y           
    ##   <int> <chr>       
    ## 1   361 Kansas      
    ## 2    67 Wisconsin   
    ## 3   294 Pennsylvania
    ## 4    75 Mississippi 
    ## 5   250 Illinois    
    ## 6   330 Nebraska

``` r
df <- read_csv(
    'data/example.csv',
    col_types = cols(
      x = col_double(), 
      y = col_character()
    )
  )

tail(df)
```

    ## # A tibble: 6 x 2
    ##       x y           
    ##   <dbl> <chr>       
    ## 1   361 Kansas      
    ## 2    67 Wisconsin   
    ## 3   294 Pennsylvania
    ## 4    75 Mississippi 
    ## 5   250 Illinois    
    ## 6   330 Nebraska

``` r
microbenchmark::microbenchmark(
  guess = read_csv(
    'data/example.csv'),
  specified = read_csv(
    'data/example.csv',
    col_types = cols(
      x = col_double(), 
      y = col_character()
    )
  ),
  control = list(warmup = 10)
)
```

    ## Unit: milliseconds
    ##       expr      min       lq     mean   median       uq      max neval
    ##      guess 1.936416 2.028499 2.192527 2.108549 2.185490 5.093569   100
    ##  specified 1.161001 1.200773 1.290738 1.228266 1.264745 3.879373   100

Vector Types
------------

### logical

### integer

### double

### character

Object Size
-----------

``` r
df_char <- read_csv(
    'data/example.csv',
    col_types = cols(
      x = col_double(), 
      y = col_character()
    )
  )

pryr::object_size(df_char)
```

    ## 21.6 kB

``` r
df_factor <- df_char %>%
  mutate(y = as.factor(y))

pryr::object_size(df_factor)
```

    ## 16.8 kB

The `jsonlite` Package
----------------------

``` r
library(jsonlite)
data_json <- fromJSON('data/sample.json')
```

Resources
---------

-   [r4ds.had.co.nz/data-import.html](r4ds.had.co.nz/data-import.html)
