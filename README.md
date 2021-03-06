
<!-- badges: start -->
[![Travis build status](https://travis-ci.org/moodymudskipper/flow.svg?branch=master)](https://travis-ci.org/moodymudskipper/flow) [![Codecov test coverage](https://codecov.io/gh/moodymudskipper/flow/branch/master/graph/badge.svg)](https://codecov.io/gh/moodymudskipper/flow?branch=master) <!-- badges: end -->

flow <img src='man/figures/logo.png' align="right" height="139" />
==================================================================

Visualize as flow diagrams the logic of functions, expressions or scripts and ease debugging.

-   Call `flow_view()` on a function, a quoted expression, or the path of an R script to visualize it.

-   Call `flow_run()` on a call to a function to visualize which logical path in the code was taken. Set `browse = TRUE` to debug your function block by block (similar to `base::browser()`) as the diagram updates.

-   Export to *html*, *png*, *jpeg*, or *pdf*.

-   Use the Rstudio addins to run `flow_view()` or `flow_run()` on your selection.

Installation
------------

Install with:

``` r
devtools::install_github("moodymudskipper/flow")
```

Example
-------

``` r
library(flow)
flow_view(median.default)
```

<img src="man/figures/README-unnamed-chunk-3-1.png" width="100%" />

There are way too many features to show them all on a README, check `?flow_view` for more,copy the following code to have a taste of the possibilities.

``` r
# exports (supports png, jpeg, pdf, html)
# shortcuts are available to export to temp file and open 
flow_view(median.default, out = "png")

# visualize which path was taken (relevant S3 method is presented)
vec <- c(1:3, NA)
flow_run(median(vec, na.rm = TRUE))

# works when code fails too (handy to debug!)
flow_run(median(iris))

# step by step exploration
vec <- c(1:3, NA)
flow_run(median(vec, na.rm = TRUE), browse = TRUE)

# trim the head of the chart as you go
flow_run(median(vec, na.rm = TRUE), browse = TRUE, trim = TRUE)
```
