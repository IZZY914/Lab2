Untitled
================

``` r
load("~/Documents/izzy work/BRFSS2022_rev.RData")
```

``` r
library(ggplot2)
library(tidyverse)
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.4     ✔ readr     2.1.5
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.1
    ## ✔ lubridate 1.9.3     ✔ tibble    3.2.1
    ## ✔ purrr     1.0.2     ✔ tidyr     1.3.1
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
how_many_rolls <- 100
sim_rolls <- sample(1:6, how_many_rolls, replace = TRUE)
```

``` r
# for first time
lots_of_sim_rolls <- sample(1:6,how_many_rolls, replace = TRUE)

# do 49 more simulations
for (indx in 1:49) {
  sim_rolls <- sample(1:6,how_many_rolls, replace = TRUE)
  lots_of_sim_rolls <- data.frame(lots_of_sim_rolls,sim_rolls)
  }
```

``` r
how_many_sims <- 50
sim_rolls_vec <- sample(1:6,(how_many_rolls*how_many_sims), replace = TRUE) # vectorized version
```

``` r
if_come_up_6 <- as.numeric(lots_of_sim_rolls == 6)
mean(if_come_up_6)
```

    ## [1] 0.1704

``` r
if_come_up_6_vec <- as.numeric(sim_rolls_vec == 6)
mean(if_come_up_6_vec)
```

    ## [1] 0.1652

``` r
if_come_up_6 <- (lots_of_sim_rolls == 6)
```
