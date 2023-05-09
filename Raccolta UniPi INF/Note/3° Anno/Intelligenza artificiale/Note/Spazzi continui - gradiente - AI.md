---
type: nota
course: Intelligenza Artificiale
topic: 
tags: IA
---

Prev: [[Introduzione Intelligenza Artificiale (IIA)]]

# Spazzi continui - gradiente - AI
---
- Molto casi reali hanno spazi di ricerca continua
-  lo stato è descritto  da variabili continue $x_1,\dots,x_2$ , vettore $x$
- in spazzi continui il fattore di ramificazione $d= \infty$ il che rende impossibile utilizzare gli[[Algoritmi di ricerca per AI| algoritmi classici di risoluzione]] ma si possono usare altri approcci che portano a soluzioni anche molto efficienti.

### Gradiente per scegliere la direzione
Ipotesi:
- Se la  funzione di valutazione $f$ è [[Funzioni Continue|continua]] e [[Funzioni differenzibili|differenziabile]] 
tesi:
- Il minimo p massimo si puoi cercare utilizzando il [[Gradiente di una funzione multivariabile|Gradiente]], che restituisce la direzione di massima pendenza del punto.

esempio:
[[Ricerca in salita o HIll Climbing per AI|Hill climbing iterativo]] dove  il nuovo vettore di stato $x_{new}$
è dato da $$x_{new}=x \pm \eta\nabla f(x)$$
dove 
- $x =$ è il vettore d’elogio stato attuale
- $\eta=$ la dimensione del passo di movimento
- $\nabla f(x)=$ il gradiente di $f$
- $\pm$ da scegliere $+$ se si cerca un massimo (si sale sulla [[Superfici - Analisi|superficie]]) $-$ se si cerca un minimo (si scende sulla superficie)
![[AE4E90A6-22E4-4080-B2C1-682C7D8872CC.jpeg]]




