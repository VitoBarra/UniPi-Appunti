---
Subject: Elementi di calcolabilita e complessita
topic: nota
tags: ECC
---

Prev: [[Elementi di Complessità e Calcolabilità (ECC)]]

# Teorema di forma normale
---
## Teorema
Esistono un predicato $T(i,x,y)$ (detto anche predicato di Kleene )e una [[Funzioni|funzione]] $U(y)$ [[Nozione di Calcolabilità|calcolabili]], [[Funzioni|totali]]  tale che $$\forall i,x.\varphi_i(x) = U(\mu y.T(i,x,y))$$
inoltre $T,U$ sono  [[Funzioni Ricorsive Primitive|primitive ricorsive]]
#### DImostrazione
$$T(i,x,y)= 
\begin{cases} 
1 & \text{se y termina } \\
0 & altrimenti
\end{cases}$$
dove $y$ è la codifica di una computazione di $M_i$ con dato iniziale $x$. calcolare $T$ si calcola prendendo la macchina $M_i$ dalla lista e comincia a scandagliare i valori $y$ . decodifica ogni o di essi uno alla volta e controlla se la computazione con x in ingresso termina. se termina allora 
$M_i(x) = c_0,\dots,c_n$ questa sequenza di passi termina sempre e quindi T è totale. 

>[!warning] DA CAPIRE
>![[920F3AA3-976A-4BC4-BA17-2DE5E60718D3.jpeg]]
>>[!question] come fai  a codificare una computazione nncpt 
>>la codifica di una macchia a di turing c è ma è equivalente alla codifica della computazione ??? 

### corollario
la funzioni [[Turing-Calcolabilita|T-Calcolbaili]] sono $\mu-$[[Funzioni Ricorsive Generali|ricorsive]]
il che porta ad affermare che
## Teorema
una funzione è [[Turing-Calcolabilita|T-Calcolbaile]] $\iff$ è  $\mu-$[[Funzioni Ricorsive Generali|ricorsiva]] 

### Corollario
ogni funzione [[Calcolabilità|calcolabile]] [[Funzioni Parziali|parziale]] puo essere ottenuta da due [[Funzioni Ricorsive Primitive]] e una sola applicazione del operatore  di [[Funzioni Ricorsive Generali#Pre-nozioni|minimizzazione]] $\mu$ 

questo nel campo della programmazione ha un interessante impatto e ci dice che possiamo riscrivere qualsiasi funzione ricorsive con due Comandi FOR e uno WHILE.


