---
type: nota
course: Computer grafica
topic: 
tags:
  - CG
Parent MOC: "[[Computer Grafica (CG)]]"
---
# Ray Tracing
---
il _[[Algoritmi di renderizazione|Ray Tracing]]_ è uno dei paradigmi di _renderizazione_.
Guardando a come funziona la luce avremmo che i _fotoni_ che arrivano dallo spazio rimbalzano sugli oggetti finche non arrivano al occhi di chi percepisce la luce.
Il _Ray Tracing_ si basa esattamente sulla simulazioni di questo fenomeno, ma invece di calcolare tutti i fotoni si calcolano solo quelli che raggiungono l _osservatore_.
Questo si fa partendo facendo partire un raggio direttamente da un punto del osservazione, ovvero da un pixel, e si calcola la traiettoria del raggio, se questo colpisce una fonte di luce allora si _renderizza_ il pixel.
![[IMG_0722.jpeg]]
si denota quindi il seguente _algoritmo_
![[IMG_0725.jpeg]]
questa è una versione base che non tiene conto dei limiti che possiamo voler imporre, come ad esempio il _numero massimo di rinbalsi_ o limiti _temporali_, tenendo conto di queste limitazioni si ha 
![[IMG_0726.jpeg]]

> [!tip] 
> Il primo algoritmo ognorando lo step 4 e limitando i rimbalzi ad 1, diventa l algoritmo di _ray cast_ che è un [[Algoritmo di visibilita|Algoritmo di visibilita]] 



##### Costo computazionali 
Nel caso semplice ogni materiale riflette in modo _totale(tutta la luce) e speculare_ il _Raggio_, ma questo è solo un caso semplificativo
Nel caso più generale dobbiamo considerare i diversi angoli di _riflessione_  e i fenomeni di _difuzione_ e _refrazione_. 

per il funzionamento del algoritmo vogliamo _almeno un raggio_ per ogni _pixel_ e vogliamo controllare le intersezioni con ogni oggetto per ogni solato  e quindi il costo puo essere stimato come

_siano_   
- $n_{p}$ il numero di pixel 
- $n_{r}\geq n_{p}$ _raggi_
- $k$ il numero di _rinbalsi_
- $m$ il numero di oggetti.
   _allora_ il vostro del algoritmo sarà $$cost(rayTracyng)= n_{p}k\sum^{m}_{i=0}Int(c_{i})$$dove $Int(c_{i})$ è il costo del _test_ di intersezione del _raggio_ con l _oggetto_ $c_{i}$. ci sono delle [[Strutture Dati|strutture dati]] che  fanno scendere il costo di $\sum^{m}_{i=0}Int(c_{i})$ ad una [[Complessita|complessita]] $O(\log (m))$ ma queste non sono adatte ad una scena dinamica siccome in quel caso si deve aggiungere il costo del _update_ della _struttura dati_.

