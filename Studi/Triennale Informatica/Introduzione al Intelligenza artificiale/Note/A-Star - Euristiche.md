---
tags:
  - IA
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic:
---

# A*- Euristiche 
---
le euristiche utilizzate negli [[AI - Algoritmi di ricerca informati|Algoritmi di ricerca informati]] come l [[AI - Ricerca A-Star|A*]]  possono essere confrontate e misurate.
la scelta del euristica più adatta si fa solitamente basandosi sul _Grado di informazione posseduto_
in generale un euristica più è informata più questa rende efficiente la ricerca, ma più si alza anche il costo del calcolo del euristica.
di solito per le euristiche ammissibili si ha  
$$ 0 \leq h(n) \leq h^*(n)$$
dove  $h^*(n)$ è  il massimo del informazione, _l’ oracolo_, ovvero sa gia dove è la soluzione.

![[E7C468EE-BB1B-4E07-B8C8-7A115AC800E7.jpeg]]

## Teorema
se $h_1(x) \leq h_2(x)$ i nodi espansi da $A^*$ con $h_2$ sono un sottoinsieme di quelli espansi da $A^*$ con $h_1$
-  $A^*$ espande tutti i nodi $f(n)=g(n)+h(n) <C^*$  e con una $h_2(n)$ si espandono meno nodi siccome ci sono meno valori di $h(n)$ che soddisfano la disuguaglianza  
 Si ha che $h_1 \leq h_2$ si ha che $A^*$ con $h_2$ è efficiente almeno quando $A^*$ con $h_1$

### Definizione
date due euristiche $h_1, h_2$ si dice che $h_2$ Domina $h_1$ se si ha che 
$$\forall n.h_1(n) \leq h_2(n)$$

### Misura del potere euristico
si misura con il _fattore di diramazione effettivo_ indicato con $b^*$
dato 
- $N$: numero di nodi generati
- $d$: Profondità della soluzione 
$b^*$ è il fattore di diramazione di un albero uniforme con $N+1$ nodi ed è la soluzione di 
$$N+1=b^*+(b^*)^2+\cdots+(b^*)^d$$
in generale un buon fattore di diramazione effettivo $b^*$ è un fattore $< 1.5$ . 
migliorare di poco il fattore di diramazione come per esempio passare da $b=2$ a $b=1.5$ può far si che con la stessa generazione di noti si arrivo al doppio della profondità 


## Come si crea una nuova euristica
##### Rilassando il problema
si può calcolare una nuova euristica dimenticandosi di alcuni vincoli che ha il problema 
##### Massimizzazione di euristiche
data una serie di euristiche ammissibili $h_1,\dots,h_k$ senza che nessuno _domini_ un altra allora si può prendere il massimo delle euristiche

$$h(n) = max(h_1(n),h_2(n),\dots,h_k(n))$$
- $h(n)$ è ammissibili se tutte le $h_i(n)$ lo sono
- $h(n)$ _domina_ tutte le altre
##### Euristica da sotto problemi 
si possono prendere sotto problemi più semplici e stimare il costo di quella ricerca. 
con un sotto problema sufficientemente facile si può memorizzare la soluzione di alcuni pattern e utilizzare i valori salvati per calcolare l euristica.

Questo porta a _sotto problemi multipli_, ovvero divido il problema originare in sotto problemi che so risolvere o stimare  i sotto problemi possono essere 
- _dipendenti_ se: Risolvere un sotto problema contribuisce alla soluzione di un altro sotto problema (Contribuisce non necessariamente aiutando)
- _indipendenti_ se: non sono _dipendenti_ (_Pattern disgiunti_)
con sottoproblemi _Dipendenti_ si massimizza l euristica prendendo l $h_1$ maggiore 
con sottoproblemi _Indipendenti_ si possono sommare l euristiche trovando cosi un euristica migliore. 

> [!warning]
> Provare a sommare euristiche di sottoproblemi _dipendendi_ porta ad euristiche non ammissibili

##### Apprendere dall esperinza
- Far girare il programma, raccogliere dati: 
	- coppie < Usare i dati per apprendere a predire la h con algoritmi di apprendimento induttivo (da istanze note stimiamo h in generale)
-  Gli algoritmi di  apprendimento caratteristiche salienti dello concentrano ( feature, x apprendiamo che da numero tasselli fuori posto 5 i ) 

##### Combinazioni di euristiche 
- Quando diverse caratteristiche influenzano la bontà di uno stato, si può usare una [[Combinazioni Lineari|combinazione lineare]]
$$h(n) = c_1x_1(n)+\cdots +c_kx_k(n)$$
dove:
- $x_1(n)$ sono  le caratteriste influenzanti
- $c_i$ sono coefficienti, un peso che si da alla caratteristiche
	- questi coefficienti si possono aggiustare con l esperienza 
- con questa metodologia l ammissibilità e la [[AI - Ricerca A-Star#Consistenza di un euristica|consistenza]] _non_ sono garantite

