---
Subject: Algebra Lineare
topic: nota
tags: AL
---

Prev: [[Algebra Lineare (AL)]]

# Sottospazio Vettoriale
---

### Definizione
Sia $V$ uno [[Spazio Vettoriale]] su un campo $\mathbb{K}$. Un sottospazio vettoriale di $V$ è un sottoinsieme $W ⊂ V$ che soddisfa i seguenti tre assiomi:
- $0 ∈ W$
- Se $v,v' ∈ W$, allora anche $v+v' ∈ W$
- Se $v ∈ W$ e $λ ∈ K$, allora $λv ∈ W$

Con queste proprietà possiamo dire che $W$ è uno spazio vettoriale perché ne rispetta gli assiomi e che $W ⊂ V$

### Sottospazio banale e totale

- Il sottospazio banale  $W = \{0\}$, formato da un punto solo, l’origine
- Il sottospazio totale $W = V$ , formato da tutti i vettori di V .

quindi un generico sottospazio $W$

$$
\{0\} \subseteq W \subseteq V
$$

### Esempi di sottospazio:

- **Polinomi con restrizioni:**
    - **$\mathbb{K}_n[x]$**  ovvero polinomi con grado $≤ n$
    - Sia $a \in \mathbb{K}$ un numero fissato. I polinomi $p(x) \ : \  p(a) = 0$ formano un sottospazio vettoriale di $\mathbb{K}[x]$
- **Funzioni con restrizioni:**

     Sia $Y ⊂ X$ un sottoinsieme qualsiasi. Il sottoinsieme

    $W = \{f ∈ F (X, \mathbb{K}) |\ f (x)=0\ ∀x ∈ Y\}⊂ F (X, \mathbb{K})$

    - $W$ è [[Sottospazio Vettoriale]] di $F(X,\mathbb{K})$
- **Matrici quadrate:**

    gli insieme di tutte le matrici che godono di una di queste [proprietà](obsidian://open?vault=UniPi-Appunti&file=Raccolta%20UniPi%20INF%2FNote%2F1%C2%B0%20Anno%2FAlgebra%20Lineare%20(AL)%2FTipi%20di%20matrice%20quadrata) sono sottospazi vettoriali della matrice quadrata $M(n)$

    - $D(n)$  : Diagonali
    - $T^s(n)$ : Triangolari Superiori
    - $T^i(n)$ : Triangolari Inferiori
    - $S(n)$   : Simmetriche
    - $A(n)$  : Antisimmetriche



