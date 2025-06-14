---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area:
topic:
SubTopic:
---

# Inferenza in modelli temporali probabilistici - Hidden markov model
---
L’**Hidden Markov Model** (HMM) è un [[Modelli temporali probabilistici|modello probabilistico temporale]]  in cui il processo sottostante è descritto da una singola [[Variabili Aleatorie (Casuali)|variabile casuale discreta]] $X_t$, che rappresenta lo stato nascosto del sistema al tempo $t$. Gli stati possibili di $X_t$ costituiscono l’insieme delle configurazioni del mondo osservato, mentre le variabili di evidenza $E_t$ forniscono le osservazioni parziali o rumorose di tali stati. 
Questa restirzione permette di fare delle implementazioni specializzate della framework generico di [[Inferenza in modelli temporali probabilistici|inferenza con modelli probabilistici temporali]].

il **modello di transizione** definito da $\mathcal{P}(X_t \mid X_{t-1})$, descrive la probabilità di passare da uno stato $i$ a uno stato $j$ e viene rappresentato da una matrice quadrata $T$ di dimensione $S \times S$, con elementi $T_{ij} = \mathcal{P}(X_t = j \mid X_{t-1} = i)$. 

il **modello sensoriale** definito come $\mathcal{P}(e_t \mid X_t)$, specifica la probabilità di osservare l’evidenza $e_t$ dato lo stato $X_t$, e viene rappresentato da una [[Matrici quadrate|matrice diagonale]] $O_t$, i cui elementi diagonali $(O_t)_{ii}$ corrispondono a $\mathcal{P}(e_t \mid X_t = i)$.  

La rappresentazione matriciale consente di formulare le equazioni di inferenza in modo compatto e computazionalmente efficiente. La procedura di **filtering** aggiorna la distribuzione a posteriori sullo stato corrente in base alla nuova evidenza, secondo l’equazione:$$
f_{1:t+1} = \alpha \, O_{t+1} T^{\top} f_{1:t}
$$dove $f_{1:t}$ rappresenta il messaggio in avanti $\mathcal{P}(X_t \mid e_{1:t})$ e $\alpha$ è un fattore di normalizzazione.  

L’**algoritmo backward** calcola invece il messaggio all’indietro $b_{k+1:t}$, che incorpora l’influenza delle osservazioni future, attraverso:

$$
b_{k+1:t} = T O_{k+1} b_{k+2:t}
$$

L’**algoritmo forward–backward**, combinando i due messaggi, fornisce la distribuzione smoothed $\mathcal{P}(X_k \mid e_{1:t})$ per ogni istante $k$. Tuttavia, tale approccio richiede spazio proporzionale alla lunghezza della sequenza osservata.  

Una formulazione alternativa consente di ottenere lo **smoothing** in spazio costante, propagando simultaneamente i messaggi forward e backward in un’unica passata, grazie alla trasformazione inversa delle equazioni di filtraggio. Questo approccio richiede che la matrice di transizione $T$ sia invertibile e che il modello sensoriale non contenga elementi nulli, condizione che garantisce la validità della moltiplicazione inversa $O_t^{-1}$.  

In un contesto di inferenza online, si adotta lo **smoothing a ritardo fisso (Fixed-Lag Smoothing)**, che consente di stimare la distribuzione smoothed per uno stato $X_{t-d}$, mantenendo un ritardo $d$ costante rispetto al tempo corrente $t$. L’idea centrale consiste nel mantenere e aggiornare due strutture: il messaggio forward $f$ e una matrice di trasformazione backward $B$, che sintetizza l’effetto congiunto delle osservazioni più recenti.  

La matrice $B$ è definita come il prodotto cumulativo delle trasformazioni di transizione e osservazione:

$$
B_{t-d+1:t} = \prod_{i=t-d+1}^{t} T O_i
$$

Essa consente di trasformare il messaggio backward più recente in quello relativo a uno stato precedente. L’aggiornamento incrementale di $B$ avviene secondo la relazione:

$$
B_{t-d+2:t+1} = O_{t-d+1}^{-1} T^{-1} B_{t-d+1:t} T O_{t+1}
$$

che permette di incorporare le nuove evidenze man mano che arrivano, senza rieseguire l’intera sequenza di moltiplicazioni.  

L’algoritmo operativo per lo [[Inferenza in modelli temporali probabilistici|smoothing]] a ritardo fisso è sintetizzato nello schema seguente:
```pseudo
\begin{algorithm}
\caption{Fixed-Lag Smoothing}
\begin{algorithmic}
\Function{Fixed-Lag-Smoothing}{$e_t, hmm, d$}
    \State \textbf{returns} a distribution over $X_{t-d}$
    \State \textbf{inputs:} $e_t$, the current evidence for time step $t$
    \State $hmm$, a hidden Markov model with $S \times S$ transition matrix $T$
    \State $d$, the length of the lag for smoothing
    \State \textbf{persistent:} $t$, the current time, initially 1
    \State $f$, the forward message $\mathcal{P}(X_t \mid e_{1:t})$, initially $hmm$.Prior
    \State $B$, the $d$-step backward transformation matrix, initially the identity matrix
    \State $e_{t-d:t}$, double-ended list of evidence from $t-d$ to $t$, initially empty
    \State \textbf{local variables:} $O_{t-d}, O_t$, diagonal matrices containing the sensor model information
    \State add $e_t$ to the end of $e_{t-d:t}$
    \State $O_t \gets$ diagonal matrix containing $\mathcal{P}(e_t \mid X_t)$
    \If{$t > d$}
        \State $f \gets$ \Call{Forward}{$f, e_{t-d}$}
        \State remove $e_{t-d-1}$ from the beginning of $e_{t-d:t}$
        \State $O_{t-d} \gets$ diagonal matrix containing $\mathcal{P}(e_{t-d} \mid X_{t-d})$
        \State $B \gets O_{t-d}^{-1} T^{-1} B T O_t$
    \Else
        \State $B \gets B T O_t$
    \EndIf
    \State $t \gets t + 1$
    \If{$t > d + 1$}
        \Return \Call{Normalize}{$f \times B \mathbf{1}$}
    \Else
        \Return null
    \EndIf
\EndFunction
\end{algorithmic}
\end{algorithm}
```
Questo procedimento permette di mantenere la complessità temporale indipendente dalla lunghezza totale della sequenza, aggiornando in modo efficiente la stima smoothed con ogni nuova osservazione.