
### Feladat leirasa: Kimenet es bemenet eloallitasa a specifikaciaonak megfeleloen
Mi a feladata?
Mik a lehetseges bemenetek?
Mik a lehetseges kimenetek?

#### Description of the search for the smallest element in a list

$$
a \in U \space |\space \exists i: 0 \le i < u, A[i] = a, A[j] \ge a, 0 < j < u
$$
Output
$$
i
$$
#### Efficiency of the algorithm

```
i<-0
for j<-1..n-1 do # incrementation, change the val of the cyclic
	if A[j] < A[i] then # comparsion, this will describe our algo
		i<-j # assignment
	endif
endfor	
```

##### Time complexity
- Worst time
- Avg
- Best time
There is not an alg which is the fastest in every case

$$
t(n) \in \Theta (n) \newline 
$$
$$
Def: f, g: \mathbb{N} \rightarrow \mathbb{N} \space | \space f \in \Theta(g) \space \exists c > 0 \space | \space n_o \ge 0  
$$
$$
f(n) \le c*g(n) \space | \space n \ge n_o
$$
#### Time Complexity Types
- Linear -> `TIME(n)`
- `TIME(f(n)) =>` $$t(n) \in \Theta(f(n))$$
- Polinomial
$$\exists b: t(n) \in \Theta(n^k)$$
$$\cup_{k=0}^{\infty} \space TIME(n^k)$$
- NP: Can be checked polinomially (Konjunctive normal form evaluation of every true evaluations)
- NP Hard: If a task from this class could be solved in polynomial everyone could be solved from this class. 