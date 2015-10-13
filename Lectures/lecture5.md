# Lecture 5
## Agenda
1. Useful Commands
2. Control Structures
3. Next time: graphics(basic plot functions, and ggplot2 package)

## Control structures
1. An important component of a programming language is control structures to implement repetitive tasks.

􏱻2. R programming language has control structures similar to C

3. Loops are used to carry out a sequence of related operations without having to write the code for each step explicitly.

### for Loops
1. For instance, suppose we want to calculate:
$\sum_{i = 1}^{10} i$
```{r}
x=0
for(i in 1:10){
  x=x+i
}
```
- In the above program, x is an accumulator variable, meaning that its value is repeatedly updated while the program runs. 
- Always remember to initiazlize accumulator varialbes (to zero in this example). 
- To clarify, we can add a print statement inside the loop body.
```{r}
x=0
for (i in 1:10){
	x=x+i
	print(c(i,x))
}
```

2. The general structure of 'for' loops:
```{r}
for(var in seq) expr
```
Or
```{r}
for(var in seq){
  expr
}
```
3. Exercise: Given a matrix A, write a for loop that calculates the sum of each row of A. 

This is an example of a `trivial` for loop. 
There is never the need to do such loops in R because it provides a simple class of functions to do just that: the 'apply' functions. 
􏰀Often times the apply functions even lead to faster code (but not always). 

### while loops
while loop is used when it is not known ahead of time how many loop iterations are needed.

Example: suppose we wish to calculate the partial sums of the harmonic series until the partial sum exceeds 5. It is a fact that the harmonic series diverges, so eventually the partial sum must exceed any given constant

The harmonic series is $\sum_{i=1}^{\infty}\frac{1}{i}$

### if loops
1. An ‘if’ block can be used to make on-the-fly decisions about what statements of a program get executed. For example, 
```{r}
y=7	
if (y < 10) { 
	x=2 
}else{
  x=1 
} 
```

2. General syntax: 
```{r}
if (cond) expr1 else expr2 
    Or 
  if (cond) { 
		expr1 
	} else { 
		expr2 
	}   
```

3. Another example: the following program places the sum of the odd integers up to 100 in A and the sum of the even integers up to 100 in B. 

### next and break
A break statement is used to exit a loop when a certain condition is met. A next statement results in the current iteration being aborted, but the loop continues with the next iteration. 

```{r}
x=0
for (k in seq(100)){  
  if (k %% 2 == 0){ 
    next 
  } ## Skip even numbers, but keep looping.
	if (x >= 50) { 
    break 
  }	## Quit looping when the sum exceeds 50. 
  x=x+k
} 
```