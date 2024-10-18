---
Course: Intelligenza Artificiale
topic: nota
tags: IA
---

Prev: [[Introduzione al Intelligenza Artificiale (IIA)]]

# Ricerca in profondità limitata DL-AI
---
è un [[AI - Algoritmi di ricerca|Algoritmo di ricerca]] variante della [[AI - Ricerca in profondita|Ricerca in profondià]]  che sfrutta delle proprietà conosciute sul problema.

si va in profondità fino ad un certo livello predefinito $\ell$ da quel livello in poi i nodi vengono trattati come se non avessero nodi successori.

### Analisi della complessità
Sia 
- $b=$ fattore di ramificazione (*B*ranching) quindi il numero massimo di successori
- $d=$ Profondità del nodo obiettivo più superficiale (*D*epth)
- $m=$ lunghezza massima dei cammini nello spazio degli stati (*M*ax)
- $\ell$ la profondità massima scelta

- _Strategia completa_  se
	- Il problema per cui si conosce il limite superiore della profondità
	- se $d<\ell$ 
- _Strategia NON ottimale_
- _[[Complessita]] nel tempo_ (nodi generati) $O(b^\ell)$ 
- _[[Complessita]] in spazio_ $O(b\ell)$  

>[!note]
>la [[AI - Ricerca in profondita|DF]] puo essere vista come un caso speciale di questa con $\ell = \infty$