---
output: html_document
---
# Lecture 1
- Welcome to CME 195!
- My email is xiaotong@stanford.edu

# Course Logistics 1
1. Requirements:
  - Programming skills
  - Statistics background
2. Course structures:
  - Around 40 mins lecture
  - Exercises
- What is this course about?

## What is R?
- R is a software for statistical computing and data analysis. An implementation of the S language.

- R is freely distributed software (www.r-project.org) with contributions from developers from around the world. It is one of the main software for statistical computing.

## Why R?
- R is free.
- Companies use R. 
- R is popular in academia.
- R is one of the best tools for data science. 
- 
## Install packages
There are many nice packages in R and some of them are not in default. You may want to install them for your research.
```{r}
install.packages(“packagename”)
```
Then you need to type:
```{r}
library(packagename)
```
in order to use the package.

## Getting Started
There are two ways to work in R:

- A conventional approach: you open a file and write program describing what you intend to do and run that program.
- An interactive approach: you interact with R and do whatever you want to do, one step at a time.

We type in expressions and R evaluate them and return a value if needed.
We combine both approaches most of the times.


## Variables
A variable in computer science is a name given to some storage location. In more practical terms, it is a binding between a symbol and a value.

```{r}
x = 20
y = x + 1
x + 2 = z
assign(‘u’, x+2)
```
1.  Both <- and = assign values to a variable, there are some differences between two assignment.
For example, if we type:
```{r}
median(x = 1:10)
```
v.s.
```{r}
  median(x <- 1:10)
```
In general, you might run into problems using `=` for assignment operator and `<-` is preferred!

2.   It is important to understand R’s organization.
As you create new variables in R, there are kept in the computer memory. It is useful sometimes to know what variables are currently in memory and be able to save or delete them.
```{r}
ls()
ls.str()
```
Both commands list existing variables.

3.   Useful Commands related to variables:
```{r}
x<-rnorm(1)
u<-x+1
```
  * Save x and u in file 'x1.RData'
  ```{r}
  save(list=c('x','u') , file='x1.RData')
  ```
  * Delete x and u
  ```{r}
  rm(list=c('x',’u’))
  ```
  * Delete all variables
  ```{r}
  rm(list=ls())
  ```
  * Load the data in x1.Rdata
  ```{r}
  load(file = ’x1.RData’)
  ```

## Working Directory
- At the beginning of each R section, a directory is attached to the section called the ’working directory’.

To see the current working directory
```{r}
getwd()
```
To set the working directory.
```{r}
setwd()
```
- Whenever you try to read or save a file without the full path, the working directory (wd) will be used. Typically the wd is the directory from which you start R.
At the end of an R session, you can choose to save all the objects in memory. A file “.RData” is then created for this purpose. Next time, starting R from the same directory, this file “.RData” will be automatically loaded.

- You can load the .RData from another directory with `load()`.

- Note that only the file ’.RData’ is automatically loaded whereas other file ‘filename.RData’ are not. You need to load them with the function `load`.

- Another important concept to know is the search directories. That is the sequence of Environments in which R searches for whatever variable or function you request.
- You can see that hierarchy with `search()`. This hierarchy changes as you add or remove packages to your R session.

- Another important concept to know is the search directories. That is the sequence of Environments in which R searches for whatever variable or function you request.
You can see that hierarchy with ’search()’. This hierarchy changes as you add or remove packages to your R session.
Type ?environment in R to find how to get, set and create environments.


## Functions

- Beside variables, functions are the other most important concept in computer programming. A function is a piece of code that takes some input called arguments, performs a specific task and possibly returns a value. In order to properly use a function we must properly set up its arguments.

- In R we specify arguments either by name or by position.
- The function rnorm we used earlier:
  ```{r}
  u <- rnorm(100,0,2) # by position
  x <- rnorm(n = 100, mean = 0, sd = 2) # by name
  ```
We can find the arguments of a given function by using the function `args`. For example, `args(rnorm)`.
- There are a lot of build-in functions in R. Before writing your own function, I would check whether there are existing functions available first.
Sometimes it is hard to google ’summation in R’. Instead, you can google ‘summation in R cran’
If you know the build-in function name, but you are not sure how to use it,
?rnorm
- Define a function

  ```{r}
  f <- function(x, i){
    x[i] = 4
  }
  w = c(10, 11, 12, 13)
  f(w, 1)
  w
  ```
- Pass by reference or pass by value:
w is not changed when we call the function f on it. Therefore, w is passed by value, which means that R makes a copy of w and changes the first element of the copied w. We will talk more about this in later classes.

## Special values in R

- `NA` is used to represent missing values and stands for not available.
  ```{r}
  v -> c(1,2,3)
  length(v) = 4
  ```
R automatically fills a NA into the end of ‘v’ since no value is provided.
- Inf and –Inf: If a computation results in a number that is too big, R will return ‘Inf’ for a positive number and ‘-Inf’ for a  negative number.
  ```{r}
  2^1024
  -2^1024
  1/0
 ```
- NaN: a computation will produce a result that makes little sense. In these cases, R often returns ‘NaN’, which stands for not a number.
```
  Inf – Inf
  0/0
  ```
- ‘NULL’:  A null object in R, represented by the symbol NULL. NULL is often used as an argument in functions to mean that no value was assigned to the argument.
```
  f1 = function(arg1, arg2 = NULL)
 ```
# Course Logistics 2
In order to pass this course:

- We have two long homework. You need to complete both homework and get more than 70% right.

- You need to turn in your r script at the end of every class. You are allowed to miss only one this quarter for no reason.No exceptions. Please do not ask one. I will not grade the scripts you turn in, I just want to make sure that everyone is on the same page.
