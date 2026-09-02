# Evaluating New Jersey's ERPO Law

This repository contains the R code used to evaluate the association between New Jersey's Extreme Risk Protection Order (ERPO) law and firearm homicide rates using the Augmented Synthetic Control Method (ASCM).

The analysis uses New Jersey as the treated state and states without an ERPO law by 2019 as the donor pool. The study period is 1999-2023, with 2019 treated as the intervention year.

## Current Analysis

The current version of `nj_erpo.Rmd` is configured for the **female firearm homicide analysis**.

The outcome variables are defined near the beginning of the file:

```r
death_col <- "female_firearm_homicides"
pop_col <- "female_population"
outcome_label <- "Female firearm homicide rate"
output_prefix <- "female"
```

These settings can be changed to run the same analysis for other outcomes or demographic groups.

## Study Setup

* Treated state: New Jersey
* Study period: 1999-2023
* Pretreatment period: 1999-2018
* Treatment year: 2019
* Posttreatment period: 2019-2023
* Outcome: Firearm homicide rate per 100,000 population
* Method: Augmented Synthetic Control Method
* Outcome model: Ridge regression

## Donor States

The analysis uses the following 31 donor states:

Alabama, Alaska, Arizona, Arkansas, Georgia, Idaho, Iowa, Kansas, Kentucky, Louisiana, Maine, Michigan, Minnesota, Mississippi, Missouri, Montana, Nebraska, New Hampshire, North Carolina, North Dakota, Ohio, Oklahoma, Pennsylvania, South Carolina, South Dakota, Tennessee, Texas, Utah, West Virginia, Wisconsin, and Wyoming.

Only states with complete data for the full study period are retained in the analysis.

## Analysis

The R Markdown file includes:

1. Data preparation and calculation of firearm homicide rates
2. Augmented Synthetic Control Method estimation
3. Observed vs synthetic New Jersey comparison
4. Average treatment effect calculation
5. Relative reduction calculation
6. ASCM inference
7. Permutation inference
8. Jackknife+ inference
9. In-space placebo analysis
10. Leave-one-out donor sensitivity analysis

## R Packages

The main packages used are:

```r
library(augsynth)
library(dplyr)
library(ggplot2)
library(readr)
library(tidyr)
```

## Data

The analysis uses **restricted-use National Center for Health Statistics (NCHS) mortality data**.

Because the data are restricted-use, they are not included in this repository.

## Running the Code

Open `nj_erpo.Rmd` in RStudio and update the analysis settings near the beginning of the file as needed.

For example:

```r
death_col
pop_col
outcome_label
output_prefix
```

Then run the R Markdown file chunk by chunk or knit the complete document.

The file can also be rendered from R using:

```r
rmarkdown::render("nj_erpo.Rmd")
```

## Author

Aayush Chitransh

Contact: connect.aayushchitransh@gmail.com
