# Homework 1
Due date: Oct 14th, 2015

You have to get 70 % right on each homework in order to pass this homework.

## Problem 1 (30%)
Vector & Matrix Exercise:
- Create a vector, where each element has a normal distribution with mean 2 and standard deviation 2. How to check how many of these elements are greater than 2?

- Create a matrix and do the following
$$A = \begin{pmatrix}4 & 1 & 2 & 3 \\
1 & 3 & 1 & 2\\
2 & 1 & 2 & 1\\
3 & 2 & 1 & 1 \end{pmatrix}$$
    1. add row3 to row 1, change A to this new matrix
    2. Interchange column 1 and column 4
    3. Calculate AA'. Is A matrix symmetric?
    
## Problem 2 (30%)
Dataframe exercise:
- x is a 10 * 10 dataframe. What does this following do?
```{r}
x[abs(x[,7]< 1, ]
x[which((x[,10]>0)&(x[,10] <9)),]
```
- Load stack.x in R. Do a summary of this data. Find the subset of this data frame, the 'Water.Temp' column of this subset only has Water.Temp less than 25. Note that this subset also have the 'Air.Flow' and 'Acid.Conc' columns.


## Problem 3 (40%)
Function Exercise:
- Write a simple function which takes a vector and sum all its element together. The function 'sum' in R is not allowed to use in this case. 'for loop in R', the function 'length' may be useful. And then write another function to return the sum of elements with odd index in the vector.
