---
title: R function
author: minsu
date: 2023-03-15 14:15:00 +0900
categories: [R, Basic]
tags: ["DataCamp"]
---

# R function

# lapply()

`lapply(X, FUN, arg1, arg2, ... )`

- `lapply` takes avector or list `X` , and applies the function `FUN` to each of its members.
- The output of `lapply()` is a list, the same length as `X` , where each element is the result of applying `FUN` on the corresponding element of `X`

# sapply()

`sapply(X, FUN, arg1, arg2, ... )`

- `sapply()` similar to how you used `lapply()` .
- The output of `sapply()` is a vector, the same length as `X's columns`
- `sapply()` did a great job at simplifying the rather uninformative ‘list of vectors’ that `laapy()` returns.

> If given that the length of the output of ********function******** changes for different input vectors, `sapply()` is not able to nicely convert the output of `lapply()` to a nicely formmatted matrix.

Instead, the output values of `sapply()` and `lapply()` ar exactly the same
> 

# vapply()

`vapply(X, FUN, FUN.VALUE, ... , USE.NAMES = TRUE)`

- The `FUN.VALUE` argument expects a template or the return argument of this function `FUN`

# runif()

- generate random values from a uniform distribution

# math function

## mean()

`mean(vectors, trim = (0 to 0.5))`

- `trim` : if you also specify a second argument, R will match the arguments by position and expect a specification of the `trim` argument
merging the two vectors is a must
    - Values of trim outside that rane are taken as the nearest endpoint

## abs()

Calculate the absolute value

## sum()

Calculate the sum of all values in a data structure

## round()

Round the values to 0 decimal places by default

`round(X, numbers)`

chage the number of digits to round to.

# Data Utilities

## seq()

Generate sequences, by specifying the `from`,`to`, and `by` argument

## rep()

Replication elements of vectors and lists

## sort()

Sort a vector in ascending order.

- arg
    - decreaing = TRUE : sorting from high to low

## rev()

Reverse the elements in a data structures for which reversal is defined.

## str()

Display the structure of any R object

## append()

Merge vectors or lists

## is.*()

Check for the class of an R object

## as.*()

Convert an R object from one class to another

## unlist()

Fallten (possibly embeded) lists to produce a vector.

## class()

show data type

# 문자열

[Regular Expression](https://www.notion.so/Regular-Expression-b138109908434aa9bc93fce9422beb3e)

## grepl()

which return `TRUE` when a pattern is found in the corresponding character string.

`grepl(pattern , x = )`

## grep()

which returns a vector of indices of the chracter strings that contains the pattern

`grep(pattern, x = )`

## sub()

`sub(pattern, replace , data)`

```r
awards <- c("Won 1 Oscar.",
  "Won 1 Oscar. Another 9 wins & 24 nominations.",
  "1 win and 2 nominations.",
  "2 wins & 3 nominations.",
  "Nominated for 2 Golden Globes. 1 more win & 2 nominations.",
  "4 wins & 1 nomination.")

sub(".*\\s([0-9]+)\\snomination.*$", "\\1", awards)

>>> [1] "Won 1 Oscar." "24"           "2"            "3"            "2"           
		[6] "1"
```

# Times & Dates

## Sys.Date()

show today’s date

## Sys.time()

show currnet time

## Date argument

- `%Y`: 4-digit year (1982)
- `%y`: 2-digit year (82)
- `%m`: 2-digit month (01)
- `%d`: 2-digit day of the month (13)
- `%A`: weekday (Wednesday)
- `%a`: abbreviated weekday (Wed)
- `%B`: month (January)
- `%b`: abbreviated month (Jan)

## as.Date()

To create a `Date` object from a simple character string in R

## format()

convert dates to character strings

```r
today <- Sys.Date()
format(Sys.Date(), format = "%d %B, %Y")
format(Sys.Date(), format = "Today is a %A!")
```

## as.POSIXct()

convert from a character string to a `POSIXct` object

- `%H`: hours as a decimal number (00-23)
- `%I`: hours as a decimal number (01-12)
- `%M`: minutes as a decimal number
- `%S`: seconds as a decimal number
- `%T`: shorthand notation for the typical format `%H:%M:%S`
- `%p`: AM/PM indicator

Again,**`[as.POSIXct()](https://www.rdocumentation.org/packages/base/functions/as.POSIXlt)`**
uses a default format to match character strings. In this case, it's `%Y-%m-%d %H:%M:%S`
In this exercise, abstraction is made of different time zones.

## diff()

calcuate the differences between consecutive days