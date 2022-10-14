---
type: nota
course: Fondamenti Di Informatica
topic: 
tags: FDI
---

Prev: [[Fondamenti Del Informatica (FDI)]]

# Serie di Fibonacci
---

## Formula ricorsiva
$$fib(x)=
\begin{cases}
	fib(0)   & =0 \\
	fib(1)   & =1 \\
	fib(x+2) & = fib(x+1)+fib(x)
\end{cases}$$

## Formula chiusa

$$fib(x)=\frac{\sqrt5}{5}(\frac{1+\sqrt5}{2})^x-\frac{\sqrt5}{5}(\frac{1-\sqrt5}{2})^x$$