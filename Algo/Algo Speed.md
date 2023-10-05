
$$
t(n) \in O(n^3)
$$
$$
t(n) = c * n^{3} * O(n^2)
$$

`C` constant:

In: `A[0, ... , n-1]`
Out: `min(A)`
`t(n) = n-1`

In: `A[0, ..., n-1]`
Out: `max(A)`
`t(n) = n-1` -> there is not a better time since all the elements must be measured, and must be compared


In: `A[0, ..., n-1]`
Out: `min(A), max(A)` 
`t(n) = 2(n-1)`
Can be done with 2 variables or with two cycles.

#### Different method
We create pairs in the list. In each pair the lesser cannot be the biggest one and the bigger one cannot be the smallest one
```
min <- T[0]
max <- T[0]

i<-1

while i + 1 < n do
	if T[i] < T[i+1] then
		a<-T[i], b<-T[i+1]
	else 
		a<-T[i+1], b<-T[i]
	endif

	if min > a then
		min <- a
	endif
	if max < b then
		max <- b
	endif
	i = i + 2
endfor
return max
```

$$
t(n) = \frac{3n}{2}
$$

75% speed gain

