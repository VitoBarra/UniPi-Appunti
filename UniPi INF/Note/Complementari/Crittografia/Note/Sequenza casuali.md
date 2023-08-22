---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Sequenza casuali
---
scelto un [[Alfabeto|alfabeto]] $A$ con $|A|=c$ _caratteri_, numeriamo tutte le sequenze costruibili $X_{0},X_{1},\dots$  ordinante con [[Ordinamento canonico|l ordine canonico]] .

dalla teoria della [[Rappresentazione di oggetti matematici con sequenze|rappresentazione di oggetti]] sappiamo che la lunghezza della stringa $X_{h} \simeq$  $\log_{c}h$ e nella _rappresentazione binaria_ si ha che la lunghezza $\simeq \log_{2}h$ e per la regola dei [[Funzione logaritmica|logaritmi del cambi di base]] si ha che la lunghezza è $\Theta(\log h)$

### Definizione
una sequenza binaria $h$ è detta _casuale_ se _NON_ esiste nessun algoritmo di generazione $A$ la cui rappresentazione binaria sia più corta di $h$.

nella partica stiamo dicendo che il modo piu economico per generare la stringa $h$ è _assegnarla direttamente_. questo rende la lunghezza del algoritmo $|A|=n+ c_{1}$ dove $c_{1}$ è la lunghezza che esprime l assegnazione e $|h|=n$ la lunghezza della sequenza. Abbiamo quindi che $n<n+c_{1}$ e quindi rispetta la  definizione di _stringa casuale_.

In contrasto un esempio di _Sequenza NON casuale_ è quella composta da $n$ uni.

_Sia_ $A$ l algoritmo che genera $n$ uni e assumiamo una [[Rappresentazione di oggetti matematici con sequenze|rappresentazione binaria]]. 
Abbiamo che l unica parte variabile del algoritmo è il riferimento al numero $n$  che è rappresentato in $\log_{2}n$ _caratteri_. Di conseguenza abbiamo che l algoritmo $A$ è rappresentato con $c+\log_{2} n=\Theta(\log n)$ _caratteri_ dove $c$ è una costante dipendente dal sistema di calcolo.
Essendo la sequenza $h$ di esattamente $n$ caratteri abbiamo che l algoritmo $A$ al aumentare di $n$ _cresce molto meno velocemente_ rispetto alla lunghezza di $h$ .
- questo vale essendo $\Theta(\log n) < n$. 
di conseguenza $h$ _non è casuale_.


questo ci porta alla conclusione che una stringa per essere casuale non deve avere una _regola precisa_ che la riesce a spiegare

> [!warning]
> Questa definizione _NON_ dice che la stringa  $h$ deve essere generata seguendo la regola che la spiega. Per essere definita _non casuale_ basta che questa regola esista,  poi se il procedimento che ha generato la stringa  non importa.  

### Complessità secondo Kolmogorov
Per dare una fondamenta teorica a questa nozione di casualità nasce la necessita di dimostrare che questa definizione è indipendente dal sistema di calcolo. e quindi si parta dalla [[Calcolabilità|teoria della calcolabilita]] per definire la seguente _complessità secondo Kolmogorov_.

_Siano_ $S_{1},S_{2},\dots$ una serie di sistemi di calcolo. Un algoritmo per generare una sequenza binaria $h$ in un sistema $S_{i}$ è un programma $p$ per $S_{i}$ e quindi abbiamo $S_{i}(p) = h$.
Si _Definisce_ la _complessità secondo Kolmogorov_ della [[Rappresentazione di oggetti matematici con sequenze|sequenza]] $h$  rispetto al sistema di calcolo $S_{i}$ come
$$\mathcal{K}_{S_{i}}(h)= \min\{|p|: S_{i}(p)=h\}$$
dove $|p|$ indica la lunghezza di $p$


nel caso in cui $h$ non sia generabile da una _regola semplice_ il piu piccolo programma e quella che _assegna la sequenza stessa_. 
E quindi abbiamo che in questo caso la complessità è
$$\mathcal{K}_{S_{i}}(h)=|h|+c$$
dove $c$ è una costante positiva che _dipende dal Sistema di calcolo_ $S_{i}$ e rappresenta l assegnamento. 
ora come per la [[Macchina di Turing|macchina di turing]]  esiste almeno un sistema di calcolo $S_{u}$ detto _[[Macchina di Turing universale|universale]]_ che può simulare tutti gli altri sistemi di calcolo.
Questo prende in input _un indice_ $i$ che indica il sistema di calcolo $S_{i}$ e un programma $p$  tale che$S_{i}(p)=h$. 
Abbiamo quindi  che con  $q =\langle i,p\rangle$ e _vale che_
$$h = S_{i}(p)=S_{u}(q)=S_{u}(\langle i,p\rangle)$$
e che la lunghezza di $$|q|= |p| + \lceil \log_{2}(i) \rceil$$
dove $\lceil \log_{2}(i) \rceil$ è la lunghezza della rappresentazione del indice $i$ ed è _indipendente_ da $h$. 

Analizzando la _complessità di Kolmogorov_ sul sistema universale avremo che varrà
$$
\begin{array}{}
\mathcal{K}_{S_u}(h)  & =  & |p|+c_{e}   \\
	 & =  & \mathcal{K}_{S_e}(h)+c_{e}& 
\end{array}
$$
dove $S_{e}$ è il sistema di calcolo _piu efficiente_ possibile, ovvero dove $\mathcal{K}_{S_e}(h)$ è minimo tra tutti i _sistemi di calcolo_ e
$c_{e}$ è una costante che dipende dal sistema di calcolo $S_{e}$


analizzando la complessità con gli altri Sistemi di calcolo otteniamo il risultato del _[teorema di invarianza del sistema di calcolo](https://en.wikipedia.org/wiki/Kolmogorov_complexity#Kolmogorov_randomness)_ che ci dice che vale che 
$$\mathcal{K}_{S_u}(h) \leq \mathcal{K}_{S_i}(h) +c_{i}$$
dove $c_{i}$ è una costante che dipende da sistema di calcolo $S_i$
e abbiamo quindi _che vale_
- l _uguaglianza_ quando $S_{i}$ è il sistema di calcolo _piu efficiente_
- il _minore stretto_ quando $S_{i}$ non è il sistema _piu efficiente_.

questo risultato dimostra che per qualsiasi sistema di calcolo la complessità puo essere espressa direttamente con $\mathcal{K}_{S_u}(h)$ _a meno di una costante_, permettendoci cosi di ignorare il sistema di calcolo specifico siccome la complessità non dipende esso.

Si puo quindi definire la _complessità secondo Kolmogorov_ della sequenza $h$ _come_
$$\mathcal{K}(h)$$

e si rifinisce una _sequenza casuale_ quando $$\mathcal{K}(h) \geq |h|- \lceil \log_{2}|h| \rceil$$
dove $\lceil \log_{2}|h| \rceil$ è aggiunto per rendere meno restrittiva la definizione senza cambiare le proprietà di causalità.


### Quantificare le sequenza casuali
_siano_  $S= 2^{n}$ il numero di _sequenze_ di $n$ bit e $T$ il numero di sequenza _NON casuali_ e si vuole studiare la relazione tra $S$ e $T$.
Abbiamo che esistono complessivamente $N=2^{n-\lceil \log_{2}n\rceil}-1$ sequenza piu corte di $n-\lceil \log_{2}n\rceil$ e tra queste cui sono tutti i programmi per generare le $T$ sequenze _non casuali_ lunghe $n$. 
Vale che $T \leq N < S$. e quindi esistono sequenza _casuali_ per ogni $n$. 
Si ha inoltre che $\cfrac{T}{S}<2^{-\lceil \log_{2}n\rceil}$ che è una funzione che tende a $0$ e quindi le _sequenze casuali_ esistono e sono molte piu numerose di quelle non casuali


### Decidere se una sequenza è casuale
decidere se una data sequenza $h$ è una _sequenza casuale_ è un problema [[Calcolabilità|indecidible]]

per mostrare questo si teorizza  una funziona $Random()$ come

$$Random(h)=
\begin{cases}0 &   \text{Se NON casuale} \\ 1  & \text{Se casuale} \\
\end{cases}$$
ed una funzione $paradosso()$ dove $|P|$ è una _costante_ e indica la lunghezza del programma $paradosso + random$.

```pseudo
	\begin{algorithm}
	\caption{Paradosso}
	\begin{algorithmic}
	\Function{Paradosso}{}
	\For{h $\leftarrow$ 1 to $\infty$}
	\If{$|h|-\lceil \log_{2}n\rceil > |P|$ and $Random(h)$}
	\Return $h$
	\EndIf
	\EndFor 
	\EndFunction
	\end{algorithmic}
	\end{algorithm}
```
Siccome le sequenza casuali esistono prima o poi $h$ sarà una _sequenza casuale_ e il programma si dovrebbe fermare, ma questo non puo accadere perché le due clausola sono in contraddizione
Infatti la prima indica che il programma è "_breve_" e genera $h$ abbiamo quindi che $\mathcal{K}(h) < |h|-\lceil \log_{2}n\rceil$  che per definizione ci dice che $h$ _NON è casuale_ ma $Random(h)=1$ e quindi abbiamo un paradosso.
questo ci conclude che la funzione $Random(h)$ non puo esistere. cioè è _indecidibile_



