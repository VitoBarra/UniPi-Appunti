---
Subject: "[[Calcolo Numerico(CN)]]"
tags:
  - CN
topic:
---

# Ordine di convergenza
--- 
gli _ordini di convergenza_ servono a confrontare i [[Metodi iterativi funzionali (calcolo degli zeri)|metodi]] del [[punto fisso]] con $g$ diverse

sia una successione $\{x_{k}\}$ _convergente_ a $\alpha$ punti fisso per $g(x)$. 
se $x_{k} \not= \alpha \ \ \forall x_{k}$ e se esiste una valore $p\geq 1$ tale che. 
$$
\begin{array}{}
\lim_{ k \to \infty } \cfrac{|x_{k+1}-\alpha|}{|x_{k}-\alpha|^{p}}  = \gamma  & \text{with}  &  \begin{cases}
0 < \gamma \leq 1  &  \text{if} &  p=1 \\
\gamma>0  & \text{if} & p>1
\end{cases}
\end{array}
$$
si dice che la successione _converge con ordine_ $p$
questo significa che per $k \to \infty$ ho che 
$$e_{k+1}=|x_{k+1}-\alpha| \approx \gamma \cdot |x_{k}-\alpha|^p$$
questo significa che 
- per $p=1$ vuol dire che l errore si riduce solo di un fattore $\gamma$ 
- per $p>1$ vuol dire che l errore si riduce più velocemente
- non ha senso di parlare di $p<1$ siccome non vedo una riduzione del errore ovvero la successione non sta convergendo

nomenclature
- con $p=1$ e $0<\gamma<1$ si dice _convergenza lineare_
- con $p=1$ e $\gamma =1$ si dice _convergenza sublineare_ 
	- converge molto lentamente
- con $p=2$ e $\gamma>0$ si dice _convergenza quadratica_
	- il metodo converge molto velocemente verso un errore vicino alla [[Precisione di macchina|precisione di macchina]]