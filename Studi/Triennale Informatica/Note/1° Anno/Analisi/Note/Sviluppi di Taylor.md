---
Subject: "[[UniPi-Appunti/Studi/Triennale Informatica/Note/1° Anno/Analisi/Analisi]]"
topic: nota
tags:
  - Analisi
---
# Sviluppi di Taylor
---
gli _sviluppi di Taylor_ sono un modo di approssimare le [[Funzioni|funzioni]] con delle [[Funzioni Polinomiali|funzioni polinomiali]], questo si fa siccome è piu facile lavorare con questo tipo di funzione.   
#### Sviluppo con Resto di Lagrange
_sia_ $f$ [[Funzioni differenziabili|derivabile]] $n$ volte su un intervallo $I$ e siano $x,x_0 \in I$ 
_allora_ esiste un punto $\xi$ compreso tra $x$ e $x_0$ con $x>x_0$ tale che  $$f(x)= \underbrace{\sum^{n-1}_{h=0}\frac{f^{(h)}(x_0)}{h!}(x-x_0)^h}_{P(x)}+ \underbrace{\frac{f^{(n)}(\xi)}{n!}(x-x_0)}_{R_n(x)}$$
dove $P(x)$ è il [[Polinomi|polinomio]] di Taylor mentre $R_n(x)$ è il [[Teorema della divisione tra polinomi|resto del polinomio]] di Taylor

>[!tip]
>[approfondimento](https://youtu.be/3d6DsjIBzJ4?si=D6cMTtFsmczpxypL) 




#### Sviluppo con il resto di Peano
_Sia_ $f$ una [[Funzioni|funzione]] di [[Continuità di una funzione|classe di continuità]] $C^n(I)$  e siano $x,x_0 \in I$ 
_allora_ si ha che$$f(x)=\sum^n_{h=0}\frac{f^{(h)}(x_0)}{h!}(x-x_0)^h+o((x-x_0)^n)$$
