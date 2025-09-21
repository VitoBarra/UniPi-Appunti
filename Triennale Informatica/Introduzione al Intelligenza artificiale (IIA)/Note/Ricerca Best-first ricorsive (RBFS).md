---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IIA
---

# Ricerca Best-first ricorsive (RBFS)
---
è un [[Algoritmi di ricerca informata|Algoritmo di ricerca informata]] basato su [[Ricerca A-Star|A*]] simile a [[Ricerca in profondita BackTracking (BDF)|DF Ricorsivo]] 


- Tiene traccia dal ogni livello del migliore percorso alternativo.
- interrompe l esplorazione quando trova un nodo meno promettente (considerando $f$)
- nel tornare indietro ricorda il miglior nodo che ha trovato nel sottalbero esplorato, per poterci eventualmente tornare


$d=$ profondità della soluzione 
_Complessita in spazio_ : $O(d)$


![[CF822C0E-2B33-4EC6-8698-A6089F3A86BF.jpeg]]