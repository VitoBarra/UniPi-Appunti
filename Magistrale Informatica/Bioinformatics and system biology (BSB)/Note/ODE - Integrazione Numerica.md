---
Course: "[[Analisi|Analisi]]"
tags:
  - Analisi
Area: 
topic: 
SubTopic:
---
# ODE - Integrazione Numerica
---
L’**integrazione numerica** di una **ODE** consiste nell’approssimare la soluzione del **[[ODE - Problema di Cauchy|problema di Cauchy]]** $$\frac{dy}{dx}=f(x,y),\; y(x_0)=y_0$$ quando non è disponibile una soluzione analitica esplicita o non è computazionalmente accessibile. L’obiettivo è costruire una successione discreta che approssimi la soluzione continua $y(x)$.

Metodi diversi sono necessari perché le [[Ordinary Differential Equation (ODE)]] possono presentare caratteristiche molto differenti: **non linearità**, **sistemi di grande dimensione**, **dinamiche con scale temporali molto diverse** (sistemi stiff), **vincoli di stabilità numerica** e **requisiti diversi in termini di accuratezza e costo computazionale**. In base al contesto si scelgono famiglie di metodi con proprietà differenti.

Si introduce una discretizzazione della variabile indipendente $$x_n=x_0+n h,\; y_n\approx y(x_n)$$ con passo $h>0$ e $n$ è il numero di passi fatti, e si utilizza uno schema numerico per propagare l’approssimazione. 
Nei metodi a **passo singolo** il valore successivo dipende solo da $(x_n,y_n)$; nella forma generale $$y_{n+1}=y_n+h\,\Phi(x_n,y_n,h)$$ dove $\Phi$ approssima il contributo medio del campo su $[x_n,x_{n+1}]$. Nei metodi **multistep** il nuovo valore dipende anche da più passi precedenti $y_n,y_{n-1},\dots$, risultando più efficienti a parità di ordine ma richiedendo una storia iniziale.

Un’altra distinzione riguarda la struttura della ricorrenza. 
Nei metodi **espliciti** $$y_{n+1}=y_n+h\,\Phi(x_n,y_n,h)$$il nuovo valore è calcolato direttamente da quantità note. 
Nei metodi **impliciti** $$y_{n+1}=y_n+h\,\Phi(x_{n+1},y_{n+1},h)$$il termine incognito compare anche a destra e a ogni passo va risolta un’equazione (in generale non lineare); questi metodi sono più costosi ma più stabili e adatti a [[ODE - Sistemi|sistemi stiff]]. 

Un’ulteriore distinzione riguarda il passo: nei metodi a **passo fisso** $h$ è costante, nei metodi **adattativi** viene aggiornato tramite una stima dell’errore locale per bilanciare accuratezza e costo.


tutti i metodi sono caratterizzati da un certo errore in funzione dello step $h$ e si dicono che sino di **ordine $p$** se l’errore globale è $O(h^p)$ e quello locale $O(h^{p+1})$. 
La **stabilità numerica** si studia spesso tramite l’equazione test $$y'=\lambda y$$ che produce una ricorrenza $y_{n+1}=R(h\lambda)\,y_n$; la regione di stabilità è l’insieme dei valori di $h\lambda$ per cui $|R(h\lambda)|\le 1$ e l’errore non cresce lungo l’integrazione.

Metodi principali:
- [[ODE - integrazione numerica - Metodo di Eulero|Metodo di Eulero]] (ordine 1)
- [[ODE - integrazione numerica - Metodo di Runge-Kutta|Metodi di Runge–Kutta]] (ordine 2 o meglio)
- [[ODE - integrazione numerica - Metodi di Adams|Metodi di Adams]] (metodo multi step con ordine simile al numero di step usati)
- [[ODE - integrazione numerica - Metodo di Backward Differentiation Formula (BDF)|Metodi BDF]] ()