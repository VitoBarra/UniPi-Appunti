---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---

# Ricerca Best-first ricorsive (RBFS)
---
è un [[Algoritmi di ricerca informati|Algoritmo di ricerca informata]] basato su [[Ricerca A-Star|A*]] simile a [[Ricerca in profondita#DF ricorsiva|DF Ricorsivo]] 


- Tiene traccia dal ogni livello del migliore percorso alternativo.
- interrompe l esplorazione quando trova un nodo meno promettente (considerando $f$)
- nel tornare indietro ricorda il miglior nodo che ha trovato nel sottalbero esplorato, per poterci eventualmente tornare


$d=$ profondità della soluzione 
_Complessita in spazio_ : $O(d)$


```python
function Ricerca-Best-First-Ricorsiva(problema) returnssoluzioneoppurefallimento return RBFS(problema, CreaNodo(problema.Stato-iniziale), ∞)          // all’iniziof-limiteè un valoremoltogrande function RBFS(problema, nodo,f-limite) returnssoluzioneoppurefallimentoe un nuovolimiteall’ f-costo// restituiscedue valori ifproblema.TestObiettivo(nodo.Stato) thenreturnSoluzione(nodo) successori= [ ] for eachazione inproblema.Azioni(nodo.Stato) do aggiungiNodo-Figlio(problema, nodo, azione) a successori// genera isuccessori ifsuccessoriè vuoto thenreturnfallimento, ∞ for each sin successorido// valutaisuccessori s.f= max(s.g+ s.h, nodo.f)// un modoper renderemonotonaf loop do migliore= ilnodocon f minimotraisuccessori if migliore.f> f_limitethen return fallimento, migliore.f alternativa= ilsecondo nodocon f minimotraisuccessori risultato, migliore.f= RBFS(problema, migliore, min(f_limite, alternativa)) if risultato≠ fallimentothen returnrisultato
```

![[CF822C0E-2B33-4EC6-8698-A6089F3A86BF.jpeg]]