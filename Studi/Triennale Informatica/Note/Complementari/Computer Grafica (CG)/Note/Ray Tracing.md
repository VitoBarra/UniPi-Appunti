---
Subject: "[[Computer Grafica (CG)]]"
Area: 
topic: 
SubTopic: 
tags:
  - CG
---

# Ray Tracing
---
il _[[Algoritmi di renderizzazione|Ray Tracing]]_ è uno dei paradigmi di _renderizzazione_.
Osservando il funzionamento fisico della luce avremmo che i _fotoni_ che arrivano dallo spazio rimbalzano sugli oggetti e l osservatore vede quei fotoni quando e se questi raggiungono il suo occhio. 
Il _Ray Tracing_ si basa esattamente sulla simulazioni di questo fenomeno, ma invece di calcolare tutti i fotoni si calcolano solo quelli che raggiungono l _osservatore_, questo si fa per ottimizzare e evitare di calcolare fotoni che l _osservatore_ non puo vedere.
per fare ciò si _spara_ un raggio direttamente da un punto del osservazione, ovvero da un pixel, e si calcola la traiettoria del raggio, se questo colpisce una fonte di luce allora si _renderizza_ il pixel.
![[IMG_0722.jpeg]]
si denota quindi il seguente _algoritmo_
![[IMG_0725.jpeg]]
questa è una versione base che non tiene conto dei limiti che possiamo voler imporre, come ad esempio il _numero massimo di rinbalsi_ o limiti _temporali_, tenendo conto di queste limitazioni si ha 
![[IMG_0726.jpeg]]

> [!tip] 
> Il primo algoritmo ignorando lo step 4 e limitando i rimbalzi ad 1, diventa l algoritmo di _ray cast_ che è un [[Algoritmo di visibilita|Algoritmo di visibilita]] 


Nel caso semplice ogni materiale riflette in modo _totale(tutta la luce) e speculare_ il _Raggio_, ma questo è solo un caso semplificativo.
![[IMG_0780.jpeg]]
Nel caso più generale dobbiamo considerare la _gestione delle ombre_ (ombre “dure”), che sono facili da con il _ray tracing_ siccome basta seguire la seguente procedura
	 _se_ un _ray_ colpisce la scena
		_spara_ un raggio verso la Fonte di luce (_Shadow ray_), se questa interseca qualcosa _allora_ è un punto d _ombra_. 
![[IMG_0779.jpeg]]
i diversi angoli di _riflessione_  che insieme al aumentare il _numero massimo di rimbalzi_ aumentano la realisticità della scena ma anche il costo _[[Complessita|computazionale]]_
![[IMG_0778.jpeg]]
e i fenomeni di _difuzione_ e _refrazione_ degli oggetti traslucidi 
![[IMG_0777.jpeg]]


Esempi di ciò che si puo ottenere con il _ray-tracing_ ![[IMG_0775.jpeg]]
##### Costo computazionali 
per il funzionamento del algoritmo vogliamo _almeno un raggio_ per ogni _pixel_ e vogliamo controllare le intersezioni con ogni oggetto per ogni solato  e quindi il costo puo essere stimato come

_siano_   
- $n_{p}$ il numero di pixel 
- $n_{r}\geq n_{p}$ _raggi_
- $k$ il numero di _rinbalsi_
- $m$ il numero di _primitive_.
- $Int(o_{i})$  il costo del _test_ di intersezione del _raggio_ con l _oggetto_ $o_{i}$
   _allora_ il costo del algoritmo sarà $$cost(rayTracyng)= n_{p}k\sum^{m}_{i=0}Int(o_{i})$$Ci sono delle [[Strutture Dati|strutture dati]] che  fanno scendere il costo di $\sum^{m}_{i=0}Int(o_{i})$ ad una [[Complessita|complessita]] $O(\log (m))$ ma queste non sono adatte ad una scena dinamica siccome in quel caso si deve aggiungere il costo del _update_ della _struttura dati_.

Le _primitive_ possono essere qualsiasi geometrica con cui si puo fare il test di intersezione.

