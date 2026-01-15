---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Ricerca conformazionale
---
La **conformazione** di una [[Molecole|molecola]] può modificarsi attraverso variazioni degli [[Meccanica molecolare|angoli di torsione dei legami]]. Lo studio delle geometrie molecolari e delle energie associate è definito "**analisi conformazionale**". 
![[IMG - analisi Conformazionale componenti.png]]
Per una molecola con un solo legame rotabile, la superficie di potenziale conformazionale si rappresenta come una curva dell'energia molecolare in funzione dell'angolo di torsione, dove i minimi corrispondono alle conformazioni a bassa energia. 
![[IMG - superfice del energia potenziale conformazionale.png]]
Nel caso di due legami rotabili, l'energia totale dipende da due angoli di torsione variabili, generando una superficie di energia in due dimensioni. 
![[IMG - energia potenziale per 2 bond ruotabili.png]]
La maggior parte delle molecole possiede più di due angoli torsionali variabili, rendendo impossibile la visualizzazione completa della superficie di potenziale, definita in uno spazio con più di tre dimensioni. Tale superficie può essere schematizzata tramite un parametro $p$ privo di significato geometrico reale, mostrando minimi locali (conformeri a bassa energia), barriere (conformeri ad alta energia) e il minimo globale (conformazione di minima energia). Barriere superiori a 80 kJ/mol impediscono l'interconversione a temperatura ambiente.  

![[IMG - energia ridotta da un parametro.png]]


Un **metodo semplice** per esplorare la superficie di potenziale conformazionale consiste nella scansione sistematica di tutte le geometrie possibili, ma per molecole con numerosi legami rotabili questo approccio diventa impraticabile.

Tutte le geometrie all'interno di uno stesso "pozzo" energetico appartengono alla stessa famiglia di conformeri; l'analisi conformazionale si riduce quindi all'identificazione di queste famiglie tramite minimi locali ottenuti attraverso procedure di minimizzazione. 
Poiché la generazione sistematica di tutti i conformeri non è sempre possibile, si ricorre a metodi che producono conformeri tipicamente diversi, ottenuti attraverso l'analisi dei frammenti (**ricerca sistematica**) o metodi casuali come il **Monte Carlo**. I conformeri generati devono essere sottoposti a minimizzazione per ottenere valori energetici significativi.  
![[IMG - ricerca dei conformanti.png]] 
La **ricerca sistematica** esplora la maggior parte delle conformazioni della molecola ruotando ciascun legame di un angolo specificato (generalmente 120°) e cercando minimi energetici. Questo approccio funziona bene per molecole piccole e acicliche, mentre per molecole grandi diventa proibitivo per la crescita esponenziale del numero di conformeri. 

Nel metodo **Monte Carlo** l’esplorazione conformazionale avviene come campionamento statistico guidato dalla [[Distribuzione di Boltzmann|distribuzione di Boltzmann]]. Ogni perturbazione genera una nuova configurazione con energia $E_{new}$, confrontata con quella corrente $E_{old}$. Quando $\Delta E = E_{new}-E_{old}$ è negativa, la configurazione viene accettata. Quando è positiva, l’accettazione avviene con probabilità $$ P = e^{-\Delta E / kT} $$confrontata con un numero casuale $R$ ($0 \le R \le 1$). Se $P > R$ la struttura è accettata, altrimenti si mantiene quella precedente. Questo criterio consente di privilegiare regioni a bassa energia pur permettendo l’accesso a stati più alti, evitando che il sistema rimanga intrappolato in un minimo locale e garantendo un campionamento coerente con l’equilibrio termodinamico.
![[IMG - schema Metropolis-Hastings MC Algorithm per la ricerca conformazionale.png]]
La conformazione assunta da una molecola al momento del legame con il target biologico è detta **bioattiva**. Essa non coincide necessariamente con il minimo globale e può essere meno stabile, purché l'energia rilasciata dalle interazioni favorevoli compensi l'energia necessaria per assumere la conformazione più tesa. La differenza energetica tra la conformazione bioattiva e il minimo globale è generalmente inferiore a 13 kJ/mol.
