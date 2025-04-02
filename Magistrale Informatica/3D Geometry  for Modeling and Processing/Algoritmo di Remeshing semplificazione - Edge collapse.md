---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Algoritmo di Remeshing semplificazione - Edge collapse
---

si Usano algoritmi gready : 

si scegli l operazione migliore che alza di meno l errore. 

solitamente si usa la versione con gli edge che ha parte combinatoria facile e geometrica leggermente piu difficile, mentre quelli con la faccia meno.

con i vertici la parte combinatoria è difficile, non c è un unico modo per collegare i vertici restanti.





![[IMG - Algoritmo gready.png]]

L'accuratezza dell'approssimazione è valutata con una funzione di energia:
che valuta la **Fitness** geometrica e la **Compattezza**.$$
E(M) = E_{\text{dist}}(M) + E_{\text{rep}}(M) + E_{\text{spring}}(M)
$$Dove 
- $E_{\text{dist}}$: somma delle distanze quadrate dei punti originali da \( M \).
- $E_{\text{rep}}$: fattore proporzionale al numero di vertici in \( M \).
- $E_{\text{spring}}$: somma delle lunghezze degli edge.

si vuole anche migliorare la mesh durante questo processo.
![[IMG - Algoritmo di semplificazione gready mesh optimization.png]]



una delle problematiche di questo tipo di algoritmi e che può  creare situazione non [[Manifolds|manifold]] ad esempio 
![[IMG - algoritmo gready per la semplificazione casi non manifold.png]]
ma ci sono dello condizioni per cui si puo evitare che questo accada. 


la condizione 
- $\Sigma$ sia un $2$-[[complesso simpliciale|complesso simpliciale]] senza [[Mesh Poligonali|bordo]], $\Sigma'$ si ottiene collassando l'arco $e = (ab)$.
- $\operatorname{Lk}(\sigma)$ è l'insieme di tutte le facce dei co-faces di $\sigma$ disgiunti da $\sigma$.

![[IMG - Condizione per mantenere la manifoldnes per algoritmi gredy di semplificazione di mesh.png]]

![[IMG - Intersezione link condizione per colasso di edge.png]]

![[IMG - Semplificazione vertice dimmy per condizione di semplificazione.png]]




Valutazione del errore:
Uno dei problemi è la valutazione de errore che via via che la mesh viene semplificata diventa sempre piu costosa perche bisognerà andare a confrontare la nuova faccia con una porzione sempre piu grande della mesh originale.


![[IMG - Semplificazione vertice medio.png]]



![[IMG - scelta verticie Mediano.png]]


![[IMG - quadratic error minimization.png]]



![[IMG - Semplificazione Comparison.png]]

![[IMG - Edge collaps penalizazione forme brutte.png]]
![[IMG - Edge collaps miglioaramento per la valenza.png]]

