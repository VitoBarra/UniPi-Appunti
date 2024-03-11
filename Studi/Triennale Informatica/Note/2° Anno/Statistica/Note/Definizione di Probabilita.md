---
Subject: "[[Statistica (STAT)]]"
tags:
  - STAT
---
# Definizione di Probabilita
---
Si parla di _probabilità_ quando si analizza un evento il cui _esito_ non è sicuro e vogliamo misurare quanto con quale confidenza un esito specifico accade


l _universo_ di cui analizziamo gli _eventi_ è l _[[Insiemi Matematici|insieme]]_ $\Omega$ chiamato _spazio dei campioni_,  gli _eventi_ sono una [[Insiemi Matematici|famiglia di sottoinsiemi]] di $\Omega$

> [!example]- 
>lo _spazio dei campioni_ sono i valori della roulette quindi   $\Omega = \{0,1,2,\dots,36\}$ e alcuni dei possibili _eventi_ (sotto insiemi di $\Omega$) sono
>- pari $P =\{2,4,\dots,36\}$
>- dispari $D = \{1,3,\dots,35\}$
>- maggiori di 10 $A = \{11,12,\dots,36\}$
>- minori di 10 $A^c= \{0,1,\dots,9\}$
>- pari e maggiori di 10 $P \cap A = \{12,14,\dots,36\}$
>- pari o maggiori di 10 $P \cup A = \{2,4,\dots,8,11,12,\dots,36\}$
>- l’evento sicuro $\Omega$
>- l’evento impossibile $\emptyset$

#### Algebra Delle parti (Definizione)
La _famiglia di sottoinsiemi_ $\mathcal{F}$ dello _spazio dei campioni_ $\Omega$ è chiamata “_eventi_” se questa è [[Operazioni chiuse|stabile (chiusa)]] per
- Unione (finita)
- Intersezione
- Complementazione
allora questa è detta _Algebra delle parti_

#### Probabilità finitamente additiva (Definizione)
_sia_  $\mathcal{F}$ un _algebra delle parti_  di insieme _universo_ $\Omega$ _allora_ la _probabilita finitamente additiva_ $\mathcal{P}$ è una [[Funzioni|funzione]]  definita come 
$$
\mathcal{P} : \mathcal{F}\rightarrow[0,1]
$$
e _tale che_
- con $A,B  \in \mathcal{F}$ vale che se $A \cap B = \emptyset \implies \mathcal{P}(A \cup B) = \mathcal{P}(A)+\mathcal{P}(B)$
- $\mathcal{P}(\Omega) =1$

Alcune conseguenza di questa definizione sono
1. $\mathcal{P}(\emptyset)=0$
2. $\mathcal{P}(A^c) =1-\mathcal{P}(A)$
3. se $B \subset A,\mathcal{P}(A\backslash B) =\mathcal{P}(A)-\mathcal{P}(B)$, dove si è posto $A \backslash B = A \cap B^c$
4. $\mathcal{P}(A\cup B) =\mathcal{P}(A)+\mathcal{P}(B) -\mathcal{P}(A\cap B)$
5. $\mathcal{P}(A\cup B \cup C) =\mathcal{P}(A)+\mathcal{P}(B) +\mathcal{P}(C) -\mathcal{P}(A\cap B)-\mathcal{P}(A\cap C)-\mathcal{P}(B\cap C) + \mathcal{P}(A\cap B \cap C)$
Questa definizione di _probabilità_ utilizza l _additivita semplice_ che pero ha un _limitazione tecnica_ non permettere di fare il [[Limiti di una funzione|limite]] e non permette quindi di [[Integrali|integrare]]

#### $\sigma$-Algebra
per risolvere estendere l _addivita semplice_ si definisce l _addività numerabile_ anche detta _$\sigma$-additivita_ 
 [[Operazioni chiuse|stabile(chiusa)]] per operazioni di
- _unione numerabile_
- _intersezione numerabile_
 una _algebra delle parti_  per cui si puo definire una _$\sigma$-additivita_ detta un _$\sigma$-algebra_


#### Probabilità assiomatica secondo Kolmogorov (definizione)
_sia_  $\mathcal{F}$ un _$\sigma$-algebra_  di un insieme _universo_ $\Omega$ _allora_ la _probabilita_ $\mathcal{P}$ è una [[Funzioni|funzione]]  definita come 
$$
\mathcal{P} : \mathcal{F}\rightarrow[0,1]
$$
e _tale che_
-  $A_{n}$con $n =1,2,\dots$ una _successione_ di elementi di $\mathcal{F}$ a _due a due disgiunti_ si ha $\mathcal{P}(\bigcup^{+\infty}_{n=1}A_{n})=\sum^{+\infty}_{n=1}\mathcal{P}(A_{n})$ 
- $\mathcal{P}(\Omega) =1$

la terna $(\Omega,\mathcal{F},\mathcal{P})$ formata da un insieme $\Omega$, una $\sigma$-algebra di $\mathcal{F}$ di parti di $\Omega$ ed una probabilita $\mathcal{P}$ definita su $\mathcal{F}$ viene chiamata _spazio delle probabilita_


questa definizione grazie alla _$\sigma$-additivita_ ci permette di mandare al limite la _probabilita_ infatti vale la formula$$\mathcal{P}(A)=\lim_{ n \to \infty }\mathcal{P}(A_{n})$$
_dimostrazione_
ponendo $B_{1}=A_{1},B_{n}=A_{n}\backslash A_{n-1}$ per $n>1$. 
gli insiemi $(B_{n})$ per $n=1,2,\dots$ sono a due a due disgiunti e per l addivita unita si ha che $\mathcal{P}(B_{n})=\mathcal{P}(A_{n})-\mathcal{P}(A_{n-1})$ e poiche $\bigcup_{n=1}^{\infty}A_{n}=\bigcup_{n=1}^{\infty}B_{n}$ si ha che 
$$\mathcal{P}(A)=\lim_{ n \to \infty } \sum^{\infty}\mathcal{P}(B_{n})=\lim_{ n \to \infty } \mathcal{P}(B_{n})$$ la dimostrazione segue dalla precedente passando la complementare

Si puo anche dimostrare questo fatto: se la funzione $\mathcal{P}$ è finitamente additiva e passsa al limite allora è _$\sigma$-additiva_ n
 

