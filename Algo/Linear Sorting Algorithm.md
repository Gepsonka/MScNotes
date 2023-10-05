### Counting Sort

$$
U=\{0, ..., n-1\}
$$
$$
A(0, ..., n-1)
$$


```
[3, 7, 0, 1, 3, 7, 2, 5, 7]
```

```
Counting elements
0: |
1: | 
2: |
3: ||
4:
5: |
6:
7: |||
8:
9:
```

Output:
`[0, 1, 2, 3, 3, 5, 7, 7, 7]`

Time complexity:
$$
m+n+3n+m = 4n+2m
$$
$$
t(n,m) \in O(n+m)
$$
Linear in the size of the array and the universe.
It is efficient if the `m` is similar sized to `n` 


# Bin Sort

Divide items by characteristics into bins, then sort the bins.



## Radix Sort



## Ford-Jhonson

