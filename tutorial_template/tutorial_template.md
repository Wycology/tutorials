Tutorial Title
================
Author
2022-01-28

This is a template for tutorials, which are instructive documents that
guide a learner through a skill using examples.

Replace this text with a description of you tutorial. Include clear
learning objectives. For example:

Have you ever learned a skill in R and wanted to share it with others?
In this tutorial, we’ll walk through how to create tutorials so that you
can easily share your skills!

#### Learning objectives

-   Become familiar with the tutorial template
-   Adapt the tutorial template to your needs
-   Create beautiful and clear tutorials for learneRs

## Editing this template

#### Accessing the template

If you do not use Github, go to the [tutorials repository home
page](https://github.com/R-Ladies-Gainesville/tutorials), click `Code`,
and click `Download ZIP`. Open the `tutorial_template.Rmd` file in
RStudio.

If you use Github,
[clone](https://docs.github.com/en/get-started/using-git/getting-changes-from-a-remote-repository)
the [tutorials
repository](https://github.com/R-Ladies-Gainesville/tutorials) and edit
the `tutorial_template.Rmd` file in RStudio.

#### R Markdown

This template is written in an R Markdown document. This type of
document is best opened and edited in RStudio. R Markdown documents
allow you to include text (like this), code (see below), and output of
code, like figures, in a single document. You can learn more about R
Markdown [here](https://rmarkdown.rstudio.com/lesson-1.html) (check out
the Cheatsheet!).

#### Metadata

If you haven’t already, replace the `Tutorial Title` and `Author`
information in the metadata block at the top of this document with your
information.

#### Section titles

This section is titled **Editing this template** and the sub-section is
titled **Section titles**, but your tutorial won’t necessarily need
these sections. Consider the sections that you want in your tutorial and
revise the headers throughout (the text that starts with ##) or create
your own section headers.

## Examples

Examples are key to meeting your learning objectives. Consider your
audience, learning objectives, and narrative when writing examples (see
[The Carpentries Curriculum
Development](https://carpentries.github.io/curriculum-development/) for
tips). The learner needs to be able to reproduce examples from your
tutorial on their computer. To do this, we look to advice on how to
create a [minimal, reproducible
example](https://stackoverflow.com/a/5963610). Examples may include:

-   Problem or goal
-   Dataset
-   Solution code
-   Information for reproducibility

## Dataset

Almost all examples require an input. That is what is meant by
“dataset”. You can create your own dataset or use one that is built into
R.

**Create-your-own:**

Known values

``` r
x <- c(1, 5, 9, 10)
```

Random values (set seed to make it reproducible)

``` r
set.seed(20)
y <- rnorm(4)
```

See guidance on [minimal, reproducible
example](https://stackoverflow.com/a/5963610) for more examples.

**Built-in:**

Available datasets in R (run in RStudio to see list)

``` r
data() 
```

A popular example dataset is ‘iris’

``` r
head(iris)
#>   Sepal.Length Sepal.Width Petal.Length Petal.Width Species
#> 1          5.1         3.5          1.4         0.2  setosa
#> 2          4.9         3.0          1.4         0.2  setosa
#> 3          4.7         3.2          1.3         0.2  setosa
#> 4          4.6         3.1          1.5         0.2  setosa
#> 5          5.0         3.6          1.4         0.2  setosa
#> 6          5.4         3.9          1.7         0.4  setosa
```

Another great example dataset is ‘penguins’

``` r
# install the package if it's not already installed
if(!("palmerpenguins" %in% installed.packages()[,"Package"]))
  install.packages("palmerpenguins")

# load package
library(palmerpenguins)

# show data
head(penguins)
#> # A tibble: 6 x 8
#>   species island bill_length_mm bill_depth_mm flipper_length_~ body_mass_g sex  
#>   <fct>   <fct>           <dbl>         <dbl>            <int>       <int> <fct>
#> 1 Adelie  Torge~           39.1          18.7              181        3750 male 
#> 2 Adelie  Torge~           39.5          17.4              186        3800 fema~
#> 3 Adelie  Torge~           40.3          18                195        3250 fema~
#> 4 Adelie  Torge~           NA            NA                 NA          NA <NA> 
#> 5 Adelie  Torge~           36.7          19.3              193        3450 fema~
#> 6 Adelie  Torge~           39.3          20.6              190        3650 male 
#> # ... with 1 more variable: year <int>
```

## Solution code

We will use an example from the [palmerpenguins
vignette](https://allisonhorst.github.io/palmerpenguins/articles/intro.html)
to demonstrate solution code. For this example, the goal is to create a
scatterplot for data with different categories.

**Install packages if they’re not already installed**

This handy code is from
[Stackoverflow](https://stackoverflow.com/a/4090208). List the packages
a learner would need for your tutorial in the first line.

``` r
list.of.packages <- c("palmerpenguins", "dplyr", "ggplot2")
new.packages <- list.of.packages[!(list.of.packages %in% installed.packages()[,"Package"])]
if(length(new.packages)) install.packages(new.packages)
```

**Load packages**

We use the code chunk option “message = F” to suppress messages
generated when packages load.

``` r
library(palmerpenguins)
library(dplyr)
library(ggplot2)
```

**Settings**

Include figure settings, saved variables, and create-your-own datasets.

``` r
theme_set(theme_minimal())
```

**Solution**

Code to create scatterplot. We use the option out.width to make the
figure clearer and smaller.

``` r
ggplot(data = penguins, aes(x = flipper_length_mm, y = body_mass_g)) +
  geom_point(aes(color = species,
                 shape = species),
             size = 2) +
  scale_color_manual(values = c("darkorange","darkorchid","cyan4"))
#> Warning: Removed 2 rows containing missing values (geom_point).
```

<img src="tutorial_template_files/figure-gfm/unnamed-chunk-9-1.png" width="50%" />

If there are variations on your solution, provide more examples!

## Information for reproducibility

R and R packages are continuously updated and examples that work under a
certain set of conditions may not work under another set. Ideally, you
would update your tutorial when key software is updated to maintain
working examples. However, that may not be feasible, and the next best
option is to provide learners with all the necessary information about
your computing environment. This can help them identify differences with
their computing environment that may be preventing the example from
running as expected.

**My computing environment:**

Session information

``` r
sessionInfo()
#> R version 4.1.2 (2021-11-01)
#> Platform: x86_64-w64-mingw32/x64 (64-bit)
#> Running under: Windows 10 x64 (build 19042)
#> 
#> Matrix products: default
#> 
#> locale:
#> [1] LC_COLLATE=English_United States.1252 
#> [2] LC_CTYPE=English_United States.1252   
#> [3] LC_MONETARY=English_United States.1252
#> [4] LC_NUMERIC=C                          
#> [5] LC_TIME=English_United States.1252    
#> system code page: 65001
#> 
#> attached base packages:
#> [1] stats     graphics  grDevices utils     datasets  methods   base     
#> 
#> other attached packages:
#> [1] ggplot2_3.3.5        dplyr_1.0.7          palmerpenguins_0.1.0
#> 
#> loaded via a namespace (and not attached):
#>  [1] highr_0.9        pillar_1.6.5     compiler_4.1.2   tools_4.1.2     
#>  [5] digest_0.6.29    evaluate_0.14    lifecycle_1.0.1  tibble_3.1.6    
#>  [9] gtable_0.3.0     pkgconfig_2.0.3  rlang_0.4.12     cli_3.1.1       
#> [13] DBI_1.1.2        rstudioapi_0.13  yaml_2.2.2       xfun_0.29       
#> [17] fastmap_1.1.0    withr_2.4.3      stringr_1.4.0    knitr_1.37      
#> [21] generics_0.1.1   vctrs_0.3.8      grid_4.1.2       tidyselect_1.1.1
#> [25] glue_1.6.1       R6_2.5.1         fansi_1.0.2      rmarkdown_2.11  
#> [29] farver_2.1.0     purrr_0.3.4      magrittr_2.0.1   scales_1.1.1    
#> [33] ellipsis_0.3.2   htmltools_0.5.2  assertthat_0.2.1 colorspace_2.0-2
#> [37] labeling_0.4.2   utf8_1.2.2       stringi_1.7.6    munsell_0.5.0   
#> [41] crayon_1.4.2
```

RStudio version

``` r
rstudioapi::versionInfo()$version
#> [1] '2021.9.1.372'
```

## Sharing your tutorial

### Slides

If you’re sharing your tutorial at an R-Ladies meeting, consider making
slides to go along with it.

See the [R-Ladies Gainesville presentations
repository](https://github.com/R-Ladies-Gainesville/presentations) to
download the the R Markdown file `tutorial_template.Rmd`. The
tutorial_template presentation is created with the
[xaringan](https://slides.yihui.org/xaringan/#1) package and the RLadies
theme by [Alison
Hill](https://www.apreshill.com/project/rladies-xaringan/).

### Github

Now it’s time to add your tutorial to the R-Ladies Gainesville
[tutorials
repository](https://github.com/R-Ladies-Gainesville/tutorials). This
will make it easier for others to provide feedback and for people to use
your tutorial!

If you do not use Github, email your `.Rmd` file to R-Ladies Gainesville
at <gainesville@rladies.org>.
