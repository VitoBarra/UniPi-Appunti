---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# CRN - Algoritmo di simulazione stocastico di Gillespie
---
L’**Algoritmo di simulazione stocastico di Gillespie** (SSA) è un approccio esatto per simulare [[CRN - Modelli stocastici|modelli stocastici per CRN]]. Tiene conto esplicitamente della randomicità intrinseca delle reazioni chimiche.

Dato un **insieme di reazioni** $$R = \{R_1, \dots, R_M\}$$per ogni reazione $R_\mu \in R$ si assume una **costante stocastica** $c_\mu$ tale che $c_\mu dt$ è la probabilità che una particolare combinazione di reagenti reagisca nell’**intervallo infinitesimo** $dt$.

La costante $c_\mu$ è usata per calcolare la propensity $a_\mu$ della reazione $R_\mu$ nell’intera soluzione: $a_\mu = h_\mu c_\mu$ dove $h_\mu$ è il numero di distinte combinazioni molecolari reagenti, infatti sia $R_\mu$ la reazione: $$\ell_1 S_1 + \dots + \ell_\rho S_\rho \xrightarrow{c_\mu} \ell'_1 P_1 + \dots + \ell'_\gamma P_\gamma$$ Se $X_i$ è il numero di molecole di $S_i$, il numero di [[combinatoria|combinazioni]] reagenti vale che $$h_\mu = \prod_{i=1}^{\rho} \binom{X_i}{\ell_i}$$

Si osservi che la **propensity** $a_\mu$ è analoga, per opportune scelte delle costanti cinetiche, alle **velocità date dalla legge di azione di massa** (assumendo volume unitario).
- Per la reazione $R_1$, con $k_1 = c_1$, la legge di azione di massa fornisce$k_1 [S_1][S_2] \approx a_1$
- Per la reazione $R_2$, con $k_2 = \frac{c_2}{2}$, la legge di azione di massa fornisce $k_2 [S_1]^2 \approx a_2$


La propensity $a_\mu$ si usa per modellare la [[Definizione di Probabilita|probabilità]] di occorrenza di una reazione usandola come parametro di una [[Variabili Aleatorie Notevoli - Esponenziale|distribuzione esponenziale]]  $Exp(a_\mu)$ che modella il tempo tra due occorrenze successive.


#### Algoritmo

dati le  
- specie $\{S_1,\dots,S_n\}$;
- quantità iniziali $\{X_1,\dots,X_n\}$;
- reazioni $\{R_1,\dots,R_M\}$;

Lo **stato del modello matematico** è descritto da:
- il [[MultiInsieme|multiset]] delle specie chimiche, rappresentato da un vettore che indica il numero di molecole presenti nella soluzione chimica (inizialmente $[X_1,\dots,X_n]$);
- una variabile reale $t$ che rappresenta il **tempo di simulazione** (inizialmente $t=0$).

Le proprietà della [[Variabili Aleatorie Notevoli - Esponenziale|distribuzione esponenziale]] permettono di modellare il **tempo fino alla prossima reazione**.

Si assume che per ogni reazione $R_\mu$ esista una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] $T_\mu$ che rappresenta il **tempo di attesa fino a quando quella reazione avviene**. Ciascuna di queste variabili è [[Variabili Aleatorie Notevoli - Esponenziale|esponenziale]] con parametro pari alla **propensity** $a_\mu$, cioè$$T_\mu \sim \mathrm{Exp}(a_\mu)$$
La prossima reazione che avviene nel sistema è quindi quella con tempo minimo $$\tau = \min\{T_1,\dots,T_M\}$$Poiché il minimo di variabili esponenziali indipendenti è ancora esponenziale, si ha $$\tau \sim \text{Exp}(a_0), \qquad a_0=\sum_{\mu=1}^{M} a_\mu$$Questa variabile rappresenta il **tempo fino alla prossima reazione**.

```pseudo
\begin{algorithm}
\caption{Gillespie's stocastic simulation}
\begin{algorithmic}
      
    \State $t \gets 0$  
    \State \textbf{Input:} stato iniziale $X=[X_1,\dots,X_n]$, reazioni $R[1],\dots,R[M]$
    \State \textbf{Input:} orizzonte di simulazione $t_{\text{stop}}$  
      
    \While{$t < t_{\text{stop}}$}  
      
\State    \Comment{Calcolo delle propensità}    
    \For{$\mu = 1$ \textbf{to} $M$}  
    \State $h[\mu] \gets$ numero di combinazioni distinte di reagenti per $R[\mu]$  
    \State $a[\mu] \gets h[\mu]\cdot c[\mu]$  
    \EndFor  
      
    \State $a_0 \gets \sum_{i=1}^{M} a[i]$  
    \If{$a_0 = 0$}  
    \State \textbf{terminate} \Comment{nessun altro evento possibile}  
    \EndIf  
      
    \State \Comment{Estrazione del tempo fino alla prossima reazione}  
    \State $U_1 \gets \text{Uniform}(0,1)$  
    \State $\tau \gets -\cfrac{1}{a_0}\ln(U_1)$  
      
    \State \Comment{ Selezione della reazione}  
    \State $U_2 \gets \text{Uniform}(0,1)$  
    \State trova il più piccolo $\mu$ tale che  $\sum_{i=1}^{\mu} a[i] > U_2 \cdot a_0$ 
      
    \State \Comment{ Aggiornamento dello stato}  
    \State $X \gets X + v[\mu]$ \Comment{$v[\mu]$ vettore stechiometrico della reazione $R[\mu]$}  
    \State $t \gets t + \tau$  
      
    \EndWhile
\end{algorithmic}
\end{algorithm}
```

Esempio per l aggiornamento dello stato usando il vettore stechiometrico: per $R_\mu : 2A + B \rightarrow 3C$ si ha $v_\mu = [-2,-1,+3]$. Se $X = [10,5,20]$, il nuovo stato diventa $[8,4,23]$.


Per generare un campione di $\tau$ si utilizza l'[[Inversion sampling|inversion sampling]]. Si vuole quindi trovare una formula che permetta di generare campioni di $\tau$ a partire da numeri $Y\sim U(0,1)$ ottenuti da un [[Generatori di numeri Pseudo Casuali|generatore di numeri pseudo-casuali]] uniforme.

Per la [[Variabili Aleatorie Notevoli - Esponenziale|distribuzione esponenziale]] con parametro $\lambda$ vale$$
\begin{array}{lll}
F(x) & = & 1-e^{-\lambda x} \qquad x\ge0 \\
F^{-1}(y) & = & \cfrac{1}{\lambda}\ln(\cfrac{1}{1-y})
\end{array}
$$Se $Y\sim U(0,1)$ allora$$F^{-1}(Y)=\frac{1}{\lambda}\ln\!\left(\frac{1}{1-Y}\right)$$Poiché $Y$ è uniforme, anche $1-Y$ è uniforme nello stesso intervallo, quindi si può scrivere equivalentemente$$F^{-1}(Y)=\frac{1}{\lambda}\ln\!\left(\frac{1}{Y}\right)$$Nel caso dell'algoritmo sappiamo che $\tau \sim \text{Exp}(a_0)$, quindi per permetterci di generare valori con la distribuzione $\tau$ si usa l inversa $F^{-1}$ ponendo $\lambda=a_0$ e si ottiene quindi $$\tau=\frac{1}{a_0}\ln\!\left(\frac{1}{Y}\right)$$dove $Y$ è generato da un [[Generatori di numeri Pseudo Casuali|generatore]] uniforme.

Una volta determinato $\tau$, bisogna scegliere **quale reazione avviene**.  
La probabilità che avvenga la reazione $R_\mu$ è proporzionale alla sua propensity

$$
\mathcal{P}(R_\mu)=\frac{a_\mu}{a_0}.
$$

Si genera un numero $n$ uniforme in $[0,1)$ e si calcola

$$
N=n\,a_0,
$$

che è uniforme in $[0,a_0)$.  
Si sommano progressivamente le propensità $a_1,a_2,\dots$ fino a superare $N$. Formalmente $\mu$ è il più piccolo indice $k$ tale che

$$
\sum_{i=1}^{k} a_i > n\,a_0.
$$

L'indice così ottenuto identifica la reazione che avviene.

Lo **stato del sistema** è invece descritto dal vettore delle popolazioni molecolari

$$
X(t)=[X_1(t),\dots,X_n(t)],
$$

che rappresenta il [[MultiInsieme|multiset]] delle specie chimiche presenti nella soluzione.  
Quando avviene la reazione $R_\mu$, lo stato viene aggiornato tramite il **vettore stechiometrico** $v_\mu$

$$
X(t+\tau)=X(t)+v_\mu.
$$


Per la [[Variabili Aleatorie Notevoli - Esponenziale|distribuzione esponenziale]] con parametro $\lambda$ vale che: $$F(x)=1-e^{-\lambda x},\quad  \quad x\ge0.$$allora  ponendo $Y$ uniforme in $[0,1)$ si ha$$F^{-1}(Y)=\frac{1}{\lambda}\ln\left(\cfrac{1}{1-Y}\right)$$
Poiché $Y$ è uniforme, anche $1-Y$ è uniforme nello stesso intervallo, quindi
$$F^{-1}(Y)=\frac{1}{\lambda}\ln\!\left(\frac{1}{Y}\right).$$


Nel caso dell'algoritmo imponendo $\lambda=a_0$ si vuole fare sampling di $X$ che rappresenta il tempo alla prossima reazione ed che è equivalente a $X=F^{-1}(Y)$ dove $Y\sim U(0,1)$ è ottenuto da un [[Generatori di numeri Pseudo Casuali|generatore]] uniforme, ovvero fa sampling come $$\tau=\frac{1}{a_0}\ln\!\left(\frac{1}{Y}\right),$$



La scelta di quale reazione avviene ha probabilità proporzionale alla sua **propensity** $a_\mu$, cioè$$\mathcal{P}(R_\mu)=\frac{a_\mu}{a_0}$$Si genera un numero $n$ uniforme in $[0,1)$ e si calcola $$N=n\,a_0,$$ che è uniforme in $[0,a_0)$. Si sommano quindi progressivamente le propensità $a_1,a_2,\dots$ fino a superare $N$. Formalmente $\mu$ è il più piccolo indice $k$ tale che$$\sum_{i=1}^{k} a_i > n\,a_0.$$L'indice così ottenuto identifica la reazione che avviene nel passo corrente della simulazione.



Il costo computazionale può diventare elevato quando il numero di molecole o le costanti cinetiche sono grandi, oppure quando sono necessarie molte simulazioni indipendenti. Questo è il principale svantaggio rispetto ai modelli ODE.
Sono state proposte varianti:
- Gibson–Bruck: strutture dati efficienti per la scelta della reazione;
- riordinamento dinamico delle propensity;
- $\tau$-leaping: più reazioni in un singolo passo temporale;
- slow-scale SSA (ssSSA): separazione tra reazioni veloci e lente;
- simulazioni ibride ODE + stocastiche.
Nonostante le ottimizzazioni, l’SSA standard resta il metodo più utilizzato per semplicità e generalità.