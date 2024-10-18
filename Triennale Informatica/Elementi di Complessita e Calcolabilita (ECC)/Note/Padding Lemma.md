---
Course: Elementi di calcolabilita e complessita
topic: nota
tags: ECC
---

Prev: [[Elementi di Complessità e Calcolabilità (ECC)]]

# Padding Lemma
---
## Teorema
ogni [[Funzioni]] [[Nozione di Calcolabilità|Calcolabile]] $\varphi_x$ ha $|\N|$ indici. inoltre $\forall x$ si può costruire mediante una funzione ricorsiva primitiva un insieme infiniti di $A_x$ di indici tale che 
$$\forall y \in A_x.\varphi_y=\varphi_x$$
ovvero ogni funzione ha infiniti algoritmi che la calcolano.  può essere che $\varphi_x =\varphi_y$ e sicuramente è che  $M_x \not=M_y$  dove $M$ sono [[Macchina di Turing]] e per l [[Tesi di Church-Turing]] si può parlare direttamente di [[Nozione di Calcolabilità|algoritmo]] 

>[!note]
>ovviamente $\varphi_x =m \iff \varphi_y =m$ e $\varphi_x \uparrow \iff \varphi_y\uparrow$

#### Dimostrazione
$\forall M_x$ [[Macchina di Turing]] con $Q = \{q_0,\dots,q_k\}$  la si chiama $M_{x_1}$ con $x_1 \in A_x$ aggiungendo a $Q$ lo stato $q_{k+1}$ e la quintupla a $(q_{k+1},\#,q_{k+1},\#,-)$  a $\delta$ si ottiene una macchina di turing $M_{x_2}$ che calcola la stessa funzione, si può procedere al infinito aggiungendo sempre nuovi stati e aggiungendo quintuple 
