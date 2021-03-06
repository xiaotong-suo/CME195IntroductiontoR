# Lecture 4
1. Recap:
  - Vectors, Matrices, Factors, Lists

2. Today:
  - Lists, Dataframes
  - Data input/output

## Data input/output
*  R can write matrix and data frames to file using the function ’write.table’.
And read data from file using ’read.table’.
*  If you have a tab-delimited file, use the function ’read.delim’ instead.
If the file is comma-separated file, then use ’read.csv’.
```{r}
Year,Student,Major
2009, John Doe,Statistics
2009, Bart Simpson, Mathematics I
```
The above is an example of a comma-separated file. Tab.delimited is the same
except that we have tabs as a separator.

* The data set ’airquality’ is available is R and gives weather measurement in
New York city over some period of time. Load that data set in a data frame and
save it to a file.

*  Things to keep in mind when reading or writing to file:
  - Header: whether the file has a first row giving the names of the variables.
  - Separator: What separator of fields is used: space, comma, tabular.
  - Data character string: What character strings serve as missing data.
  -  Do you want to allow R to convert characters variables to factors? use options stringsAsFactors and as.is.

*  The general syntax of read.table:
```{r}
mydata=read.table('filename.dat',header=F, sep=' ', dec='.', col.names=c('V1','V2'),
na.strings='NA')
```

## Some useful functions
*  as. functions
```{r}
as.numeric
as.character
as.matrix(data.matrix())
as.data.frame
```
Character > numeric > integer > logical

*  which functions
```{r}
which()
which.min()
which.max()
```

*  Split() function
split(x,f) divides the data in the vector x into the groups defined by f.
```{r}
spliteddiamonds = split(diamonds, color)
```

*  str function: A alternative function to ‘summary’
You can apply str to any objects in R: fpre example, a dataframe
```{r}
str(diamonds)
x <- rnorm(100,2,4)
str(x) #compared to summary(x)
str(spliteddiamonds)
```

*  apply function:
```{r}
args(apply)
function (X, MARGIN, FUN, ...)
X: the object;
’MARGIN’: a vector giving the subscripts
which the function will be applied over.
1 indicates rows, 2 indicates columns.

’FUN’: the function to be applied.
In the case of functions like +, %*%, etc.,
the function namemust be	backquoted or quoted.
’...’: additional optional arguments to FUN.
```
Some Exercises
```{r}
x <- rnorm(100, -5, 1)
x <- c(NA,rnorm(100, -5, 1))
y <- rnorm(100, 5, 1)
X <- cbind(x, y)
apply(X, MARGIN=2, FUN=mean)
apply(X, 2,mean,na.rm=T)
apply(X, MARGIN=2, FUN=var)
apply(X,2,var,na.rm=T)
for( i in 1:2) print(mean(X[,i]))
```

*  rowSums, rowMeans,colSums, colMeans

*  order and sort
1. The  function	'order'	returns	the	ascending	(default)	or	descending	order	of	elements	of	a	vector.	For	example,	order(0.5,5,-3.1)	will	return	3,	1,	2.	Its	sister	func1on	is	sort.	We	always	have	x[order(x)]=sort(x).		
2. The	matrix	stack.x is	a	readily	available	matrix	in	
R.	It	has	three	names	columns:	Air.Flow,	 Water.Temp,	Acid.Conc..	
The	meaning	of	these	numbers	are	not	very	important	here.		
Order	the	rows	of	the	matrix	by	increasing	values	of the	column	AirFlow.		

* Performance comparisons
```{r}
N=10
P=5
A=matrix(rnorm(N*P),ncol=P)
sumrow=apply(A,MARGIN=1,FUN=sum)
N=1000
A=matrix(rnorm(N*P),ncol=P)
sumrow=numeric(N),
system.time(for (i in 1:N) sumrow[i]=sum(A[i,]))
system.time(apply(A,MARGIN=1,FUN=sum))
system.time(rowSums(A))
```
