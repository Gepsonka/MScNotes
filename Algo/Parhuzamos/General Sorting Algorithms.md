
# Grouping

- ### Min max selecting
	- basic
	- bubble
	- heap
 - ### Minimum selecting
	 - Merge sort
 - ### Inserting - Not suitable for small numbers
	 - Basic inserting
	 - Shell
	 - Ford-Jhonson
 - ### Selection
	 - Quick-sort
	 - Batcher-like odd-even
 - ### Rank Based

## Minimum Selecting Sort

```
for i<-0 ... size-2 do
	min <- i
	for j <- i+1 ... size-1 do
		if .[min] > .[j] then 
			min <- j
		endif
	endfor
	.[min] <-> .[i] # switch up variables
endfor
```

$$
(n-1) + (n-2) + ... + 1 = \frac{n(n-1)}{2} = \frac{1}{2}n^{2}- \frac{1}{2}n
$$

## Bubble Sort

```
for i<-0 ... size-2 do
	for j<-.size-1 ... i+1 (down) do
		if .[j-1] > .[j] then
			.[j] <-> .[j-1]
		endif
	endfor
endfor
```

$$
t(n) \in O(n^2)
$$


### Fine Tuned Bubble Sort

```
for i<-0 ... size-1 do
	k <- .size-1
	for j<-.size-1 ... i+1 (down) do
		if .[j-1] > .[j] then
			.[j] <-> .[j-1]
			k<-j
		endif
	endfor
	i<-k
endfor
```

$$
t(n) \in O(n^2)
$$
### Rank Based Sort

```
R[0 ... size-1] <- 0
for i<-0 ... size-2 do
	for j <- i+1 ... size-1 do
		if [i] > [j] then
			R[i]++
		else
			R[j]++
		endif
	endfor
	for i <- 0 ... size-1 do
		B[R[i]] <- [i]
	endfor
	[...] <- B
endfor	
```
$$
t(n) \in O(n^2)
$$
Rang calculation: How many element are smaller or equal but comes earlier.

-> good for cases when an element can be in the list in multiple times.

### Merge Sort

 ```
{x} {y} {z} {a} {b} {c}
{x, y}  {z, a} {b, c} -> number of comparsions: n. |
{x,y,z,a} {b,c} -> n                               |. log n
{x,y,z,a,b,c}   -> n                               |                  
```
$$
t(n) \in O(n * log\space n)
$$

### Quick Sort

$$
t(n) \in O(n^2)
$$

A common sorting algorithm cannot be faster than:
$$
t(n) \in \Omega(n * log\space n)
$$

