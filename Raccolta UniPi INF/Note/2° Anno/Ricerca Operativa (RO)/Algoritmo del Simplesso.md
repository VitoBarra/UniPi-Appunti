---
type: nota
course: Ricerca Operativa
topic: 
tags: RO
---

Prev: [[Ricerca Operativa (RO)]]

# Algoritmo del Simplesso
---

# Simplesso primale

### *Teorema*

L’algoritmo del simplesso primale termina dopo un numero finito di iterazioni.

- se il valore ottimo del problema è $+\infty$, l’ algoritmo trova una direzione di recessione che è anche di crescita per la funzione obbiettivo
- Se il valore ottimo de problema è finito, l’algoritmo trova un vertice ottimo

### *Algoritmo*

1. Trova una [[Basi e vertici|base]] $B \ | \ \overline {x} = A_B^{-1}b_B$ si ammissibile
2. Calcola la soluzione di base duale $\overline{y} =\begin{pmatrix}\overline{y}_B \\\overline{y}_N\end{pmatrix}$ dove $\overline{y}_B^T = c^TA_B^{-1}, \overline{y}_N=0$
3. Se $\overline{y}_B \geq 0$ **allora** STOP \[ $\overline{x}$  è ottimo per il primale e $\overline{y}$ è ottima per il duale \]
**altrimenti**  trova l indice uscente
$h=\min\{i \in B \ | \ \overline{y}_i <0\}\ \ \ \ \ \text{(regola anticiclo di Bland)}$
poni $W=-A_B^{-1}$ e denota $W^h$ la $h\text{-esima}$ colonna di $W$
($W^h$ è la direzione di spostamento)
4. Se $A_iW^h \leq 0 \ \ \forall i \in N$  **Allora** STOP \[ valore ottimo primale $+\infty$ e duale $\emptyset$ \]
**altrimenti** calcola
           $ϑ= \min\begin{Bmatrix}\frac{b_i-A_i\overline{x}}{A_iW^h} \ |\ i \in N,A_iW^h > 0\end{Bmatrix}\ \ \ \\text{(Passo di spostamento)}$
  Trova l indice entrate
        $k= \min\begin{Bmatrix}i \in N \ | \\frac{b_i-A_i\overline{x}}{A_iW^h} = ϑ,\ A_iW^h > 0\end{Bmatrix}\ \ \\text{(regola anticiclo di Bland)}$
aggiorna la base: $B = B \backslash \{h\} \cup \{k\}$,
calcola $\overline{x} =A_B^{-1}b_B$ e torna al passo 2

![[Simp Prim.png]]

consideriamo un problema primale

$$
\begin{cases}
\max c^Tx \\
Ax \leq b
\end{cases}
$$

in cui $rank(A) =n$ e quindi esistono vertici (soluzioni di base ammissibili ) del poliedro primale.

l algoritmo del simplesso primale parte da un vertice del [[Poliedro]] primale

se il vertice del poliedro duale corrisponde alla stessa [[Basi e vertici|base]] è ammissibile, allora il vertice primale è ottimo e l algoritmo si ferma.

altrimenti l algoritmo trova una direzione di spostamento che è una [[Direzioni di crescita e di decrescita|direzione di crescita]] per il primale

se tale direzione è di [[Poliedro#Direzione di recessione|recessione]] per il poliedro primale, allora il valore ottimo del primale è $+\infty$ e l algoritmo si ferma.

altrimenti l algoritmo trova il passo di spostamento lungo la direzione trovata e una nuova base, cambiando un solo indice rispetto alla vecchia base, in modo che la nuova soluzione di base primale rimanga ammissibile (il nuovo vertice è adiacente al vertice precedente)

### Trovare soluzione di base ammissibile

![[Raccolta UniPi INF/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 1 14.png]]

![[Raccolta UniPi INF/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 2 9.png]]

---

# Simplesso Duale

### *Teoreama*

L’algoritmo del simplesso duale termina dopo un numero finito di iterazioni.

- se la regione ammissibile del primale è vuota, l algoritmo trova una direzione di recessione per il duale che è anche di decrescita.
- Se la regione ammissibile del primale non è vuota, l algoritmo trova un vertice ottimo

### *Algoritmo*

1. Trova una [[Basi e vertici|base]] $B \ | \ \overline {y} = \begin{pmatrix}\overline {y}_B  \\\overline {y}_N\end{pmatrix}$
dove $\overline{y}_B = c^TA_B^{-1} ,\overline{y}_N = 0$  si ammissibile
2. Calcola la soluzione di base duale $\overline{x} = A^{-1}_B b_B$
3. Se $A_N\overline{x} \leq b_N$ **allora** STOP \[ $\overline{x}$  è ottimo per il primale e $\overline{y}$ è ottima per il duale \]
**altrimenti**  trova l indice uscente
$k=\min\{i \in N \ | \ A_i\overline{x}>b_i\}\ \ \ \ \ \text{(regola anticiclo di Bland)}$
poni $\eta_B=-A_kA_B^{-1}$, la direzione di spostamento $d$ è $d_i\ =\begin{cases}-\eta_i \ \ \ \ se \ i\in B \\1 \ \ \ \ \ \ \ \ se \ i = k \\0 \ \ \ \ \ \ \ se \ i\in N \ \backslash \ \{k\} \\\end{cases}$
4. Se $\eta_B \leq 0$  **Allora** STOP \[  primale $\emptyset$ e valore ottimo duale $-\infty$ \]
**altrimenti** calcola
           $ϑ= \min\begin{Bmatrix}\frac{\overline{y}_i}{\eta_i} \ |\ i \in B,\ \eta_i >0\end{Bmatrix}\ \ \ \\text{(Passo di spostamento)}$
  Trova l indice entrate
        $h= \min\begin{Bmatrix}i \in B \ | \\frac{\overline{y}_i}{\eta_i}= ϑ,\eta_i > 0\end{Bmatrix}\ \ \\text{(regola anticiclo di Bland)}$
aggiorna la base:  $B = B \backslash \{k\} \cup \{h\}$,
calcola $\overline{y}_B = c^TA_B^{-1}$ e torna al passo 2

![[Raccolta UniPi INF/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 3 7.png]]

consideriamo un problema primale

$$
\begin{cases}
\max c^Tx \\
Ax \leq b
\end{cases}
$$

in cui $rank(A) =n$ e quindi esistono vertici (soluzioni di base ammissibili ) del [[Poliedro]] primale.

L’algoritmo del simplesso duale parte da un vertice del poliedro duale

se il vertice del poliedro primale corrisponde alla stessa [[Basi e vertici| basi]] è ammissibile allora il vertice primale è ottimo e l algoritmo si ferma. altrimenti trova una direzione di spostamento che è una [[Direzioni di crescita e di decrescita|direzione di decrescita]] per il duale.

Se tale direzione è di [[Poliedro#Direzione di recessione|recessione]] per il [[Dualità|poliedro duale]], allora la regione ammissibile del primale è vuota e l algoritmo si ferma.
altrimenti l algoritmo trova il passo di spostamento lungo la direzione trovata e una nuova base, cambiando un solo indice rispetto alla vecchia base, in odo che la nuova soluzione di base duale rimanga ammissibile (il nuovo vertice duale è adiacente al vertice precedente)

### Trovare soluzione di base ammissibile

![[Raccolta UniPi INF/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 4 5.png]]
