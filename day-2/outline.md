# Day 2

## Motivation (why to broaden your horizons beyond Excel)
* Flexibility
* Reproducibility
* Scalability
* Relational data vs. dimensional data

## Rectangles
* The toughest part of data visualization is data munging. 
* Data frames are the only appropriate input for `library(ggplot2)`. 

## Jump right in
* [Graphics guide](https://ui-research.github.io/r-at-urban/graphics-guide.html)

#### Example 1 ()
```
library(ggplot2) # loaded in library(tidyverse)

ggplot(data = storms, mapping = aes(x = pressure, y = wind)) + 
  geom_point()
```

#### Example 2 (3rd-dimension)
```
ggplot(data = storms, mapping = aes(x = pressure, y = wind, color = category)) + 
  geom_point(alpha = 0.2)
```

#### Example 3 (munging)
```
storms %>%  
  filter(category > 0) %>%
  distinct(name, year) %>%
  count(year) %>%
  ggplot(mapping = aes(x = year, y = n)) + 
  geom_line() +
  geom_point()
```

#### Example 4 (layers)
```
ggplot(data = storms, mapping = aes(x = pressure, y = wind)) + 
  geom_point() +
  geom_smooth()
```

#### Example 5 (bar)
```
ggplot(data = storms, aes(category)) + 
  geom_bar()
```


* Make a bar plot by copying-and-pasting code

## Functions

* `ggplot()`
* `aes()`
* `geom_*()`
    * `geom_point()`
    * `geom_line()`
    * `geom_col()`    
* `scale_*()`
    * `scale_y_continuous()`
* `labs()`

## Theory

1. *Data* are the values represented in the visualization.
2. *Aesthetic mappings* are directions for how data are mapped in a plot in a way that we can perceive. Aesthetic mappings include linking variables to the x-position, y-position, color, fill, shape, transparency, and size.
    * Aesthetic mappings like color and size vary with the values of variables. Color, fill, shape, transparency, and size can be added in ways that don't vary with the day by including them outside of `aes()`.
3. *Geometric objects* are representations of the data, including points, lines, and polygons.
4. *Scales* turn data values, which are quantitative or categorical, into aesthetic values.
5. *Coordinate systems* map scaled geometric objects to the position of objects on the plane of a plot. The two most popular coordinate systems are the Cartesian coordinate system and the polar coordinate system.
6. *Facets* (optional) break data into meaningful subsets.
    * `facet_wrap()`, `facet_grid()`, and `facet_geo()`
7. *Statistical transformations* (optional) transform the data, typically through summary statistics and functions, before aesthetic mapping.
8. *Theme* controls the visual style of plot with font types, font sizes, background colors, margins, and positioning.

## Styling

`source('https://raw.githubusercontent.com/UrbanInstitute/urban_R_theme/master/urban_theme.R')`

```
library(urbnthemes)
set_urban_defaults(style = "print")
```

## Mapping

* [library(urbnmapr)](https://github.com/UrbanInstitute/urbnmapr)
* [Urban Institute R Users Group website: mapping](https://ui-research.github.io/r-at-urban/mapping.html)

## Resources

* [Urban Institute R Users Group website](https://ui-research.github.io/r-at-urban/graphics-guide.html)
* [Why the Urban Institute visualizes data with ggplot2](https://medium.com/@urban_institute/why-the-urban-institute-visualizes-data-with-ggplot2-46d8cfc7ee67)
* [R for Data Science: data visualization](http://r4ds.had.co.nz/data-visualisation.html)
* [awunderground themes](https://awunderground.github.io/ggplot2-themes/)
* [R Graph Gallery](https://www.r-graph-gallery.com/)