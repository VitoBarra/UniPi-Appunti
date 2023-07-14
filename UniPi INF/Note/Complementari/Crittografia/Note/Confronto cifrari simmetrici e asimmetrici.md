---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Confronto cifrari simmetrici e asimmetrici
---
Mentre per i [[Cifrari a chiave Simmetrica]]  le chiavi totali necessarie per la comunicazione di $n$ utenti sono $\frac{n(n-1)}{2}$  quelle necessarie per i  [[Cifrari a chiave Asimmetrica|cifrari a chiave assimetrica]] sono $2n$ che è un numero piu facile da gestire rispetto al numero quadratico di scambi di chiavi segrete necessarie nei _cifrari simmetrici_


i sistemi _asimmetrici_ sono piu lenti di 2 ordini di grandezza rispetto a quelli _simmetrici_ e questo puo essere un problema visto la grande crescita di necessita di comunicazione veloce e sicura.


### Approccio moderno
siccome [[Cifrari a chiave Simmetrica|Cifrari a chiave Simmetrica]] e [[Cifrari a chiave Asimmetrica|Cifrari a chiave Asimmetrica]] hanno pregi e difetti complementare nella crittografia moderna si una un approccio _ibrido_ dove si scambiano le chiavi segrete, che sono corte, dei cifrari simmetrici con protocolli Asimmetrici, e poi si utilizza quella chiave per scambiarsi messaggi, piu lunghi, in modo piu veloce 


