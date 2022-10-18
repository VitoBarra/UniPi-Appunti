---
type: nota
course: Elementi di calcolabilita e complessita
topic: 
tags: ECC
---

Prev: [[Elementi di Complessità e Calcolabilità (ECC)]]

# Funzioni Ricorsive Generali
---
## Pre-nozioni
l operatore $\mu$ è l operatore di minimizzazione dove applicato ad un [[Insiemi|insieme]] di numeri naturali ne restituisce il valore minimo se questo esiste

## Definizione
la classe delle funzioni ricorsive generali è un formalismo per esprimere un [[Nozione di Calcolabilità|Modello di calcolo]] ed è chiamato $\mu-$ricorsività, è la minima classe di [[Funzioni]] $\mathcal{R}$ che soddisfa le condizioni
1. $I-V$ stesse di [[Funzioni Ricorsive Primitive]]
2. $VI \text{(minimizazzione)}$ se $\varphi(x_1,\dots,x_n,y) \in \mathcal{R}$ in $n+1$ variabili, allora la funzione $\psi$ in $n$ variabili $\in \mathcal{R}$ se è definita come
$$\large\psi(x_1,\dots,x_n)= \mu y[\varphi(x_1,\dots,x_n,y) =0 \land \forall z \leq y.\varphi(x_1,\dots,x_n,z\downarrow)]$$
- dove:
1. indica che il _MINIMO_ $y$ che rende l equazione vera
2. per tutto i valori minori di $y$ la funzione converge
3. $\psi$  restituisce esattamente quel $y$

## Espressività
questo formalismo è più protendente delle [[Funzioni Ricorsive Primitive]] perché esprime tutte le funzioni che può esprimere questo formalismo tutte le [[Funzioni totali]]che _NON_ può e tutte le [[Funzioni Parziali]]. questo formalismo esprime tutto ciò che esprime anche la [[Macchina di Turing]] è quindi detta Turing-Equivalente.


## Computazione
1. valuta $\varphi(x_1,\dots,x_n,0)$ se uguale $0$ allora $\large\psi(x_1,\dots,x_n)=0$
2. altrimenti valuta $\varphi(x_1,\dots,x_n,1)$ se uguale $0$ allora $\large\psi(x_1,\dots,x_n)=1$
3.  $\cdots$
 $\vdots. \cdots$

questa computazione potrebbe non finire mai siccome potrebbe essere che 
1. $\forall y \ \exists m_y .\  \varphi(x_1,\dots,x_n,y) =m_y \not=0$
2. $\forall z<k \ \exists m_z .\  \varphi(x_1,\dots,x_n,z) =m_z\not=0 \land\varphi(x_1,\dots,x_2,k)\uparrow$
nel primo caso non troviamo mai in numero naturale che soddisfa quel equazione e nel secondo troviamo un $k$  per cui non riusciamo a terminare la valutazione di $\varphi$. questa non terminazione definisce la parzialità di $\psi$ 


>[!note] Glossario
>Ricorsive : funzioni $\mu-$ricorsive TOTALI, o è [[Funzioni Ricorsive Primitive| ricorsiva primita]] e ha la proprietà $P$

