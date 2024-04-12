---
Subject: Programmazione e Algoritmica
topic: nota
tags: PEA
---

Prev: [[Programmazione e Algoritmica (PEA)]]

# Ricerca Binaria
---
é una [[Algoritmi|algoritmo]] di ricerca con [[Complessita|complessita]] $\theta(\log n)$

![[binarysearch.png]]

```c++
#include <iostream>
using namespace std;
#define x 15
#define N 5
int main(){
int a[N] = {1,5,8,10,15};
int i = 0, j = N-1, m, pos = -1;
do { 
m = (i + j)/2; 
if(a[m] == x)
	pos = m; 
else if (a[m] < x) 
	i = m + 1; 
else 
	j = m - 1; 
}
while(i <= j && pos == -1); 
if(pos != -1) return 0; }
```
