# ana515a2
---
title "ANA 515 Assignment2"
author: "Mijeong Jo"
date: '2023.09.24'
output:
html_document:
df_print: paged
pdf_document: default
word_document: default
---

#install.packages("knitr")
#install.packages("bslib")
#install.packages("dplyr")
library(knitr)
library(bslib)
library(dplyr)

#The data measures liters of alcohol consumptions by countries. It contains country,beer_servings,spirit_servings,wine_servings,total_litres_of_pure_alcohol.

```{r alcon, cache = FALSE, echo=TRUE}
knitr::opts_chunk$set(echo = TRUE)
url <- "https://github.com/fivethirtyeight/data/blob/master/alcohol-consumption/drinks.csv"
alcon <- read.csv(url)
alcon2 <- alcon[, c(1, 2, 3, 4, 5, 6)]
glimpse(alcon)
```
```{r clean, include = TRUE}
alcon3 = rename(alcon, "beerpercountris"="beer_servings")
alcon3 = rename(alcon, "winepercountris"="wine_servings")
newalcon <- subset(alcon3, select = -c(6))
```
myalcon <-newalcon[,c(1,2)]
columns_summary <- data.frame(Columns = c(colnames(myalcon))
                              Description = c("The total_litres_of_pure_alcoholvariable is used to measure total alcohol consumption")
kable(columns_summary, caption = "alcohol consumption")     
```
```{r summarystat=TRUE, echo=TRUE}
subset = alcon3[,c('beerpercountris','winepercountris','total_litres_of_pure_alcohol')]
subset

sum(is.na((subset$`beerpercountris``)))
sum(is.na((subset$`winepercountris`)))
sum(is.na((subset$`total_litres_of_pure_alcohol`)))
result <- summary(subset)
result

