---
output: html_document
---
# Lecture 2
1. Today's Agenda
- Functions
- Data structures: vectors, matrices

2. The feedback from you:
- Pace: most of you followed the first lecture well and I will increase the speed of the lectures in the future. However, if you have trouble following me, feel free to ask questions in class or make an appointment with me. 

- Lecture materials: Maybe a little less organized! 

3. The r script you turn in: it will not be graded, instead, will be checked. However, if you are enrolled in this class and would like me to give you some feedback, I would be happy to do so. 


## Data structures
In order to work with a language we need to know the objects that language offers. R offers 5 basic objects: vectors, matrix, factor, dataframe and list.

## Vectors
- A vector is a collection of objects which all have the same data type (also called mode). R supports many different mode: integer, double, logical, character and complex.
- To create a vector use the function 'vector':
```{r}
x1 <- vector(’double’,2);
x2 <- 1 #The variable x is a vector of size 1
```

- Another common way of creating a vector is using the concatenation function 'c' or ':'.
```{r}
x3 <-  c(1,2,10)
x4 <- 1:10
```

- There are also many other common ways to create a vector:
```{r}
x5 = rep(1, 10)
x6 = seq(from = -2.5, to = 2.5, by = 0.1)
```

- We use `[]` to access the elements of a vector. Thus x[1] is the first element of x, etc...
```{r}
x3[1]+2
x3[3:10]
X3[1]
```
Note: the index in R is 1 based!

- Some Exercises
```{r}
x1 <- vector(’double’,length=20) # a vector of real numbers
x2=c(1:10) # a vector of integers
x3=c(T,F,FALSE,TRUE) # a vector of logical values
x4=c(’MY’,’NAME’, ’IS’) # a vector of characters
x5 = c(2+2i,complex(real=cos(pi/3),imaginary=sin(pi/3))) # a vector of complex numbers
typeof(x4) #or class(x4) or mode(x4)
typeof(x5)
```
- Again: in a vector all elements are of the same data type.
If need be R will coerce your input in order to enforce that rule
```{r}
x1 <- c(1.2, `a`)
x2 <- c(5,-3,FALSE)
```

- You can name the elements of a vector.
```{r}
x=1:5
names(x)=c(‘a’,’b’,’c’,’d’,’e’)
#we can do it more quickly:
names(x)=letters[1:5]
```

- Calculus is vectorized in R.
```{r}
x=c(1,3)
exp(x)
x/2
```

- The recycling rule: consider the following example:
```{r}
x<-c(1,2,3,5);
y = 1:5
z=seq(from=1,to=2,by=0.5)
length(z)  #will give you the number of elements of z
v=c(x,y,z) # 'c' is the concatenation function
v+1
x+1
```
  
In formal calculus, the last two expressions are not valid because the vectors are not of the same size. That is where the recycling rule kicks in: R repeats the shortest vector until the two vector have the same length.

- Accessing elements of collections of objects is an important operation(subletting). R provides a very powerful and flexible facility for this. We can select subsets of a vector by inclusion, exclusion, by name and by logical indexing. The result is another vector.
```{r}
x=rbinom(10,21,0.5)
#by inclusion
x[1]
#by exclusion
x[-c(1,2,9,10)]
#by logical indexing  
x[x>5]
```

- Can you guess what is going on?
```{r}
x=1:10;
names(x)=letters[1:10]
x['b']
x[-(1:2)]=10:3
x[x==100]=NA
x[c(TRUE,FALSE)]
x[]=10
x=10
```

### Logical vectors
- Most of you are familiar with vectors of numerics. It is important to understand vectors of logical.
􏰁Logical can be either TRUE, FALSE or NA (for missing).
􏰁These variables obey the rules of Boolean algebra with operators AND, OR and NOT.
􏰁In R,AND is &,OR is |and NOT is !.
```{r}
A=c(TRUE,TRUE);
B=c(TRUE,FALSE)
!A
A&B
A|B
```

- R allows to do usual calculations on logical vectors. In this case, the value TRUE is taken as 1 and FALSE as 0. This can be very useful in practice. Consider the following:
```{r}
x=rnorm(100)
mean(x>0)
```
## A quick recap: 
 - How to define a vector, name a vector
 - Access elements in a vector
 - Recycling rule

## Matrices

- R supports matrices and has a good numerical linear algebra library.
􏰁- You can create matrix in R using the function ’matrix’.
- By default the matrix is filled by column. Use the argument  ’byrow’ to fill the matrix by row
```{r}
M1=matrix(data=1:8,ncol=4, nrow=2)
M2=matrix(data=1:8,ncol=4,nrow=2,byrow=T)
```

- You can name to rows and columns of a matrix:
```{r}
rownames(M1)=letters[1:2]
colnames(M1)=letters[1:4] 􏰁
```

- We can find out the size of a matrix:
```{r}
dim(M1)
ncol(M1)
nrow(M1)
```

- To index a matrix, use the same techniques as for vectors but with the first index for rows and the second index for column.

- Can you guess what is is going on?
```{r}
M1= matrix(data=1:8,ncol=4, nrow=2)
rownames(M1)=letters[1:2]
colnames(M1)=letters[1:4]
M1[-1,2]
M1[’a’,]
M1[,c(TRUE,TRUE,FALSE)]
```

- When we take a one-dimensional subset of a matrix, the result by default is coerced into a vector, unless we use the argument drop.
```{r}
M1[,1]
# compare with
M1[,1,drop=F]
```

- R supports matrix calculus, but beware: A+B, A-B, A/B, A*B are all element by element operations. As with vectors, any operation on numerics will also work on matrix of numerics.
```{r}
A=matrix(1:4,2,2)
B=matrix(5:8,2,2)
A+B
A/B
A*B
log(exp(A))
```
- Note that `A% ∗ %B` is the usual matrix multiplication. The inverse is obtained with the function ’solve’.
􏰁Other useful function: ’eigen’, ’det’. The transpose is ’t’.
