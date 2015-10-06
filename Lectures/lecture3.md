# Lecture 3
1. Recap
	- Vectors, Matrices
2. Reminder: if you haven't submit your r script from previous lectures, please do so.
There is a due date. Please submit your script before the next lecture.

2. Today's Agenda
	- Data structures: vectors, matrices
	- Factor, List, Dataframe

## Factors
1. In R a factor is a vector that hold categorical data. (for example, 'Yes'-'No' answers). For example:
```{r}
f1=factor('Yes',levels=c('Yes','No'))
f1[2]='No'
f1[3]='Maybe'
f1[3]='No'
f1[4]='No'
table(f1)
```
2. Sometimes we want to keep an ordering between the levels of the factors
```{r}
data=sample(letters[1:10],size=50,replace=T)
f2=factor(data,levels=letters[1:10],ordered=T)
```

3. 􏰀Sometimes it is useful to convert a numerical vector into factor.
􏰀
4. The function 'cut' can be useful in doing so.
```{r}
data=stack.x[,'Water.Temp']
f3=cut(data,breaks=3,labels=c(‘Low’,’Medium’,’High’))
```
We can add the ordering
```
f3=cut(data,breaks=3, labels=c(’Low’,’Medium’,’High’),ordered=T)
```

## Lists

1. Lists are collections, like vectors. But unlike vectors, the same list can hold different types of objects.
􏰀
2. Lists also have the attribute ’names’ that you can set and use to access the components.
􏰀
3. You can also access the components using the operator '[[ ]]' not '[ ]' as for vectors and matrices.

4. Why use lists:  It allows you to put together objects of different types. Vectors don’t.
```{r}
V=c('A','A','C','B','B');
X=1:5;
Y=rnorm(5);
L=list(X,Y,V)
names(L)
names(L)=c('V1','V2','V3')
L$V1 L[[3]]
```

## Dataframes

1. Roughly a data frame is a rectangular table with rows and columns. The columns represent variables and can be of different types (numeric, integer, factor, character); a major difference from matrices. The rows are records or cases.

2. Typically we create data frames by reading data from files. We can also create data frames from vectors with the function data.frame.

3. You can convert a data frame to a matrix with ’data.matrix’.
```{r}
V=factor(c('A','A','C','B','B'));
X=1:5;
Y=rnorm(5);
dt1=data.frame(X,Y,V)
names(dt1)=c('meas1','meas2','meas3')
```

4. We think of data frames both as a matrix (a rectangular table with rows and columns) and as a list (a list of statistical variables on which we have observations).
```
#Continuing with the previous example:
dt1[1,1]
dt1$meas1
dt1[[1]]
```
