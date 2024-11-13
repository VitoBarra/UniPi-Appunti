---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---

# Ricerca con approfondimento iterativo ID
---
è un [[Algoritmi di ricerca|Algoritmo di ricerca]] che utilizza i concetti di [[Ricerca in ampiezza BF|BF]] e di [[Ricerca in profondità limitata DL|DL]] infatti è un buon compromesso tra i due. avendo cosi le buone proprietà della prima e il basso consumo di memoria della seconda

l algoritmo esplora piu volte l albero aumentando ad ogni iterazione il limite $\ell$ di 1. l esplorazione è fatta come in DL con quindi taglio del branch completamente esplorato 
![[Pasted image 20230212021002.png]]
### Analisi della complessità

Sia 
- $b=$ fattore di ramificazione (*B*ranching) quindi il numero massimo di successori
- $d=$ Profondità del nodo obiettivo più superficiale (*D*epth)
- $m=$ lunghezza massima dei cammini nello spazio degli stati (*M*ax)

- _Strategia completa_   prima o poi li guarda tutti
- _Strategia ottimale_:  se tutti i costi sono uguali come per la [[Ricerca in ampiezza BF|BF]]
- _[[Complessita]] nel tempo_: $O(b^d)$
	- $db+(d-1)b^2+(d-2)b^3+\dots+1b^d$
	-  nodi generati più volte rispetto a [[Ricerca in ampiezza BF|BF]] ma asintoticamente uguali   
- _[[Complessita]] in spazio_: $O(bd)$   