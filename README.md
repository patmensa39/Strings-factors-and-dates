# Handling Strings-Factors-and-Dates
This project deals with ways of handling string (combining and splitting them), handling factors(arranging them alphabetically and by levels), Times and dates and working with forcats.

---
title: "Strings, Factors and dates"
output:
  pdf_document: default
  html_document: default
  word_document: default
date: "October 2020"
theme: cerulean
---

---


## Name: Project 3 

### This project deals with ways of handling string (combining and splitting them), handling factors(arranging them alphabetically and by levels), Times and dates and working with forcats.

### Splittig my name with dots.
```{r}
strsplit("Patrick.Senyo.Mensah", split = "[.]")

### This can also be separated by any letter in the name. Eg. Splitting my name with the 'y'
strsplit("Patrick.Senyo.Mensah", split = "y")
 
### with 'e'
strsplit("Patrick.Senyo.Mensah", split = "e")
```

### Combining my name with with the #paste function.
```{r}
paste("Patrick",  "Senyo", "Mensah")

### By separating them with sep.
paste("Patrick",  "Senyo", "Mensah", sep = "_")
```

### The string package is contained in tidyverse

```{r}
library(tidyverse)
### Combining names using str_c in tidyverse. str_c is vectorized.
str_c("Philant", c("Sammy", "Clement", "Wisdom", "Ephraim"), "Osman", sep = "_")
str_c("Philant", c("Sammy", "Clement", "Wisdom", "Ephraim"), c("Nash", "Osaman","Vicent"), "Osman", sep="_")

### Collapsing the above to a single string.
str_c("Philant", c("Sammy", "Clement", "Wisdom", "Ephraim"), "Osman", collapse = "")
```

### Finding the length of a string using the str_lenth function.
```{r}
### Finding the first seven characters from Philantropist.
str_sub("Philantropist", 1,7)
### Counting from backwards by finding the last seven characters from Philantropist.
str_sub("Philantropist", -7,-1)
```

### Changing my name to lowercase, uppercase, and capitalizing the first letters.
```{r}
str_to_lower("Patrick Senyo mensah")
str_to_upper("Patrick Senyo mensah")
str_to_title("Patrick Senyo mensah")
```

### Splitting functions with str_split. This does the same thing as strsplit, execept that str_split gives you the lists. 
```{r}
str_split("www.patrickmensah.com", pattern = "[.]")
str_split(c("My full name is Patrick Senyo Mensah", "My nickname is Philant"), pattern = " ")
### Adding options.
str_split(c("My full name is Patrick Senyo Mensah", "My nickname is Philant"), pattern = " ", simplify = TRUE)
```

### Splitting strings with the boundry function. Here, each charater is separated by each 'word'
```{r}
str_split("My full name is Patrick Senyo Mensah. My nickname is Philant", boundary("word"))[[1]]
```

### Sorting strings. 
```{r}
### Arranging alphabetically.
str_sort(c("Phialnt", "Osman", "Osaman", "Clement", "Wisdom"))
### Arranging by the order of the number.
str_order(c("Phialnt", "Osman", "Osaman", "Clement", "Wisdom"))
```


## Factors
```{r}
### Days of the week in factors.
days<- c("Monday", "Tuesday","Sunday", "Wednesday", "Thursday", "Friday", "Saturday","Thursday")
### Sorting the days alphabetically.
sort(days)
### Sorting by using factors.
week.levels<- c("Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday")
week<- factor(days, levels = week.levels)
sort(week)
```

```{r}
### Months of the year.
x1<- c("Mar", "Jan", "Oct", "Apr")
### Sorting the months
sort(x1)
### Arranging according to the months in the year using the levels below.
month.levels<-c("Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec")
month<-factor(x1, levels = month.levels)
sort(month)
```

## Time and dates
```{r}
### Date and times only uses lubridate.
### time only uses hms
###install.packages("lubridate")
###install.packages("hms")
```

```{r}
### loading the packages
### y means year, m means month and d means day.
library(lubridate)
library(hms)
mdy("October 4th, 2020")
dmy("4-October-2020")
ymd(20201004)
```

```{r}
### Adding time to the dates
### with hour, minute and second
ymd_hms("2020-10-04 23:14:50")
### with hour and minute
ymd_hm("2020-10-04 23:14")

### specifying the dates and time with timezones
ymd(20201004, tz= "GMT")
ymd(20201004, tz= "Asia/Singapore")
ymd(20201004, tz= "America/New_York")
