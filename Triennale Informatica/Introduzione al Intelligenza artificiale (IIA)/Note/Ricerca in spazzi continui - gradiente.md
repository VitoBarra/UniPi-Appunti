---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
topic: nota
tags:
  - IIA
  - AIF
---

# Ricerca in spazzi continui

i [[Problemi di ricerca|Problemi di ricerca]] su [[Definizione di Problemi-Ambienti|spazi degli stati continui]]  hanno variabili di stato assumono **valori reali** all'interno di un intervallo. In tali casi, lo stato è descritto da un vettore continuo $x = (x_1,\dots,x_n)$, e lo spazio delle possibili azioni ha un fattore di ramificazione infinito $d = \infty$. Questo rende inapplicabili gli algoritmi classici di ricerca basati sull’esplorazione esplicita la [[Algoritmi di ricerca informata|ricerca informati]] o [[Algoritmi di ricerca non informati|non informata]] 

Per affrontare questi problemi, si interpretano come [[Problemi di ottimizzazione|problema di ottimizazione]] e si usa il calcol [[Derivate|differenziale]] per fare **ottimizzazione locale** infatti
**Se** la  funzione di valutazione $f$ è [[Continuità di una funzione|continua]] e [[Funzioni differenziabili|differenziabile]]  **allora** Il [[Massimi e minimi|minimo o massimo]] si puoi cercare utilizzando il [[Funzioni Multivariata - Gradiente|Gradiente]], che restituisce la direzione di **massima pendenza** in un punto $x$ questo si può usare per creare una regola di aggiornamento dello stato attuale che segue come $$x_{new}=x \pm \eta\nabla f(x)$$dove 
- $x =$ è il vettore dello stato attuale
- $\eta=$ la dimensione del passo di movimento
- $\nabla f(x)=$ il gradiente di $f$
- $\pm$ da scegliere $+$ se si cerca un massimo (si sale sulla [[Superfici|superficie]]) $-$ se si cerca un minimo (si scende sulla superficie)

Il valore di $\eta$ influisce significativamente sull'efficacia della ricerca: 
- se **troppo piccolo**, il processo richiede molti passi
- se **troppo grande**, si rischia di saltare oltre l'estremo locale.
 Per risolvere tale criticità si ricorre talvolta al metodo del **line search**, che adatta dinamicamente il passo in funzione del comportamento della funzione in direzione del gradiente.

La ricerca di un punto di **minimo o massimo** può anche essere formulata come la ricerca delle radici del gradiente, ovvero trovare $x$ tale che $\nabla f(x) = 0$. In tal caso è applicabile il [[Metodo delle tangenti o di Newton|metodo di Newton]], che utilizza anche l'informazione di secondo ordine, attraverso la matrice [[Matrice Hessiana|hessiana]] $H_f(x)$. L’aggiornamento diventa:$$
x \leftarrow x - H_f(x)^{-1} \nabla f(x)
$$dove ogni elemento della matrice hessiana è definito da:$$
H_{ij} = \frac{\partial^2 f}{\partial x_i \partial x_j}
$$Quando il calcolo della hessiana completa è **oneroso**, si ricorre a varianti approssimate. Nel minimizzando così localmente la funzione obiettivo.

Le difficoltà principali in questi spazi includono la presenza di **massimi locali**, creste e altopiani, caratteristiche che richiedono l’uso di tecniche come restart casuali o [[Ricerca Simulated Annealing|simulated annealing]]. 
![[IMG - landscape del gradiente.jpeg]]