---
Course: "[[Data Base (DB)]]"
topic: nota
tags:
  - DB
---

# Schemi Relazionali - Decomposizione di schemi
---
La _decomposizione_ degli [[Modello dati - Modello Relazionale|schemi relazionali]] è un operazione necessaria per la rimozione delle _anomalie_ 
questo si fa _scomponendo_ che si presentano con _relazioni grandi_ in _relazioni più piccole_ che sodisfano certe proprietà ovvero sono in _[[Normalizzazione di schemi relazionali|forme normale]]_ 


#### Decomposizione (Definizione)
_sia_ $R(T)$ uno [[Modello dati - Modello Relazionale|schema relazionale]] 
_se_ $\bigcup_{i}T_{i} =T$
_allora_ $\rho=\{ R_{1}(T_{1}),\dots R_{K}(T_{K}) \}$ è una _decomposizione_ di $R(T)$

>[!note]
>le relazione nella decomposizione $\rho$ non sono _necessariamente disgiunte_


#### Decomposizione che preservano i dati
_Sia_ 
- $R \langle T,F \rangle$ uno [[Modello dati - Modello Relazionale|schema relazionale]]
- $\rho= \{ R_{1}(T_{1}),\dots,R_{k}(T_{k})\}$ è una _decomposizione_ di $R$
_Se_ per ogni relazione $r$ che soddisfa $R \langle T,F \rangle$ vale che $$r = \pi_{T_1}(r)\bowtie\dots \bowtie\pi_{T_k}(r)$$_allora_ $\rho$ è una _decomposizione che preserva i dati_ 



##### Teorema
_sia_
- $R\langle T,F\rangle$ uno [[Modello dati - Modello Relazionale|schema relazionale]] 
- $\rho= \{ R_{1}(T_{1}),\dots,R_{k}(T_{k}) \}$ una _decomposizione_ di $R$
_allora_ si ha che _per ogni istanza_ $r$ di $R(T)$ vale $$r \subseteq \pi_{T_1}(r) \bowtie\dots \bowtie\pi_{T_k}(r)$$

###### _dimostrazione_
siccome $\bigcup_{i}T_{i}=T$ anche la relazione $\pi_{T_1}(r) \bowtie\dots \bowtie\pi_{T_k}(r)$ è definita su $T$
Data l _ennupla_ $t\in r,t[T_{i}]\in \pi_{T_i}(r)$ e data la definizione di [[Modello relazionale - Algebra Relazionale|giunzione naturale]] segue che $t\in \pi_{T_1}(r) \bowtie\dots \bowtie\pi_{T_k}(r)$


##### Teoria 
Questo teorema definisce cos è una _perdita di informazione_, Con perdita di informazione si riferisce al fatto che fare il join sulle relazioni della decomposizione restituisce più ennuple di quante c è  ne fossero nella relazione originaria



##### Teorema
_sia_ 
- $R\langle T ,F\rangle$ uno [[Modello dati - Modello Relazionale|schema relazionale]] 
- $\rho= \{ R_1(T_1),R_2(T_2) \}$ con $\bigcup_iT_i =T$ una _decomposizione_ di $R$
_se e solo se_ $T_{1} \cap T_{2} \rightarrow T_{1} \in F^+$ oppure $T_{1} \cap T_{2} \rightarrow T_{2} \in F^+$ ovvero nella [[Schema relazionali - Chiusura di Insiemi di dipendenze|chiusura]] di $F$
_allora_ La _decomposizione_ $\rho$ _preserva i dati_


> [!note]
> ovvero non devono esserci [[Normalizzazione di schemi relazionali#Linee guida per la progettazione|ennuple spurie]]

###### _Dimostrazione_
$( \ \Longleftarrow\ )$: 
_Sopponiamo_ che $T_{1} \cap T_{2} \rightarrow T_1 \in F^+$
_sia_ 
- $r$ un istanza valida di $R\langle T,F\rangle$ 
- $s=\pi_{T_1}(r) \bowtie\pi_{T_2}(r)$ una decomposizione di $R$
- $t$ una _ennupla_
assumendo $t \in s$ bisogno dimostrare che $t \in r$
per _definizione_ di $s$ _esistono_ due _ennupla_ $u,v\in r$ tale che
- $u[T_1]=t[T_1]$
- $v[T_2]=t[T_2]$
- $u[T_1 \cap T_2] =v[T_1 \cap T_2]=t[T_1 \cap T_2]$
_siccome_ $T_1 \cap T_2 \rightarrow T_1 \in F^+$ vale che 
- $u[T_1]=v[T_1]\implies t=v$

Il caso $T_{1} \cap T_{2} \rightarrow T_2 \in F^+$ è _analogo_ con $t=u$

$( \implies )$: 
Sopponiamo che _pero ogni_ istanza valida $r$ di $R \langle T,F\rangle$ valga che $r =\pi_{T_1}(r) \bowtie \pi_{T_2}(r)$ 

Bisogna dimostrare che valga $T_1 \cap T_2 \rightarrow T_1 \in F^+$ o $T_1 \cap T_2 \rightarrow T_2 \in F^+$ 
dimostriamo per [[Dimostrazione di Teoremi per assurdo o contraddizione|assurdo]] assumendo che nessune delle due implicazioni _condizioni sino verificate_

_sia_
- $W = (T_1 \cap T_2)^+$
- $Y_1=T_1-W$
- $Y_2=T_2 - W$
abbiamo che $Y_1,Y_2$ sono non vuoti per _ipotesi_ e $Y_1,Y_2,W$ sono una [[Partizione di un insieme|Partizione]] di $T$ 

per ogni $A_i\in T,1\leq i\leq k$ consideriamo due valori $a_i,a_i'\in dom(A_i)$ con $a_i\not=a_i'$
_costruiamo_ le relazione $r$ con attributi $WY_1Y_2$ formate dalle due ennuple
- $e_{1}=a_{i} \ \ \ 1 \leq i\leq k$
- $e_{2}=\begin{cases}a_{i}&if&A_{i} \in W\\ a_{i}'& if & A_{i}\in Y_{1}Y_{2}\end{cases}$
$r$ _soddisfa ogni dipendenza_ $V \rightarrow Z \in F$ infatti 
- _se_ $V \not\subseteq W \implies e_1[V] \not=e_2[V]$ ed $r$ soddisfa ovviamente la dipendenza 
- _se_ $V \subseteq W\implies(T_1 \cap T_2 )\rightarrow V$ e per _[[Schema relazionali - Assiomi di Armstrong|transitività]]_ vale $(T_1 \cap T_2 )\rightarrow Z$ quindi $Z \subseteq W$  e $e_1[Z]=e_2[Z]$ e quindi $r$ sodisfa la [[Schemi relazionali - Dipendenze funzionali|dipendenza]]

poiché $Y_1,Y_2$ non sono _vuoti_ $\pi_{T_1}(r)$ e $\pi_{T_2}(r)$ contengono due _ennuple_ e la loro [[Modello relazionale - Algebra Relazionale|giuzione naturale]] ne contiene $4$ che sono più di quelle di $r$ quindi $$\pi_{T_1}(r)\bowtie\pi_{T_2}(r)\not=r$$ _contradicendo l ipotesi_.
>[!note]
>questo risultato è stato _generalizzato_ con un numero $n$ di relazioni nella decomposizione anzi che solo 2


#### Decomposizione che preservano le dipendenze

Una delle proprietà della decomposizione degli schemi relazionali e quello di conservare le _dipendenze_.

Questo è importante siccome _se non_ si conservassero le dipendenze dello schema originale si potrebbero inserire nel database delle _ennuple_ che soddisfano le dipendenze delle singole tabelle della decomposizione ma _non_ le dipendenze della tabella originali, rendendo cosi i due schemi relazionali non equivalenti


##### Proiezione di un insieme di dipendenze (definizione)
_sia_ 
- $R \langle T,F\rangle$ uno [[Modello dati - Modello Relazionale|schema relazionale]]
- $T_i \subseteq T$ un sotto _insieme di attributi_
_allora_  la [[Modello relazionale - Algebra Relazionale|proiezione]] di $F$ su $T_i$ è definita come $$\pi_{T_i}(F)=\{ X \rightarrow Y \in  F^+ \mid X,Y \subseteq T_i \}$$
##### Algoritmo banale
un algoritmo _banale_ di [[Complessita|complessità]] _esponenziale_ per calcolare un _copertura_  di $\pi_{T_i}(F)$ è il seguente
```pseudo
	\begin{algorithm}
	\caption{Copertura di $\pi_{T_i}(F)$ }
	\begin{algorithmic}
	\Function{FindCover}{F,$T_i$}
	\State $\pi_{T_i}=\emptyset$
	\For{$\boldsymbol{each} \ Y \subset T_i$ }
	\State $Z:=Y^+_F-Y$
	\State $\pi_{T_i} =\pi_{T_i} \cup Y\rightarrow (Z \cap T_i)$
	\EndFor 
	\Return $\pi_{T_i}$
	\EndFunction 
	\end{algorithmic}
	\end{algorithm}
```

##### Decomposizione che preserva le dipendenze (definizione)
_sia_  
- $R \langle T,F\rangle$ uno _[[Modello dati - Modello Relazionale|schema relazionale]]_
- $\rho=\{ R_1(T_1),\dots R_n(T_n) \}$ una _decomposizione_ di $R$
_se e solo se_ $\bigcup \pi_{T_i}(F) \equiv F$ dove $\pi_{T_i}$ è una _proiezione_ su $F$ 
_allora_ $\rho$ preserva le dipendenze 


##### Determinare se una decomposizione preserva le dipendenze
per controllare che una data decomposizione preservi le dipendenze dobbiamo controllare che $\forall X \rightarrow Y \in F$ valga che $X \rightarrow Y \in G^+$ con la  $G^+$ [[Schema relazionali - Chiusura di Insiemi di dipendenze|chiusura]] e $G = \bigcup \pi_{T_i}(F)$ 

calcolando la [[Schema relazionali - Chiusura rispetto gli attributi|chiusura]] di $X$ rispetto a $G$ indicata con $X^+_G$ si può evitare di _calcolare esplicitamente_ $G^+$
```pseudo
	\begin{algorithm}
	\caption{Copertura di $X$ rispetto $G$}
	\begin{algorithmic}
	\Function{CalcoloXPIU}{$\rho$,$X$}
	\State $X_G^+=X$
	\While{$X_G^+$ è cambiato}
	\For{$\boldsymbol{each} \ i=1 \ \boldsymbol{to}\ k$}
	\State $X_G^+=X_G^+\cup ((X^+_G \cap T_i)^+_G\cap T_i)$
	\EndFor
	\EndWhile
	\Return $X_G^+$
	\EndFunction
	\end{algorithmic}
	\end{algorithm}
```
e $(X^+_G \cap T_i)^+$ viene [[Schema relazionali - Chiusura di Insiemi di dipendenze#Algoritmo di chiusura veloce|con l algoritmo di chiusure veloce]] che ha [[Complessita|complessità polinomiale]]
ed agni passo l _istruzione_ nel for  aggiunge a $X^+_G$ gli attributi $A_i$ tali che $(X_G^+ \cap T_i \rightarrow A_i \in \pi_{T_i}(F)$ 

e quindi l algoritmo di determinazione segue come
```pseudo
	\begin{algorithm}
	\caption{decidere se $\rho$ preserva le dipendenze}
	\begin{algorithmic}
	\Function{CheckIfPreserveDipendency}{$\rho$}
	\For{$\boldsymbol{each}\  X \rightarrow Y \in F$}
	\State $X_G^+ =$ \Call{CalcolaXPIU}{$\rho$,$X$}
	\If{$Y \not\subseteq X_G^+$}
	\Return false
	\EndIf
	\EndFor
	\Return true
	\EndFunction
	\end{algorithmic}
	\end{algorithm}
```
e questo è un algoritmo _polinomiale_

#### Decomposizione che preserva Dati e dipendenze
il _preservare_ dati e _dipendenze_ di una decomposizione sono due __proprietà indipendenti__, Ma esiste un criterio per assicurare di averli entrambi

##### Criterio di Sufficienze
_sia_
- $R \langle T,F\rangle$
- $\rho=\{ R_i\langle T_i,F_i\rangle \}$ una _decomposizione_ di $R$
_Se_
- $\rho$ _preserva e dipendenze_
- $\exists j. T_j$ è [[Modello Relazionale - Chiavi|super chiave]] per $R$
_allora_ $\rho$ preserva _anche i dati_


###### _Dimostrazione_
si assume senza perdita di generalità che $T_1$ sia [[Modello Relazionale - Chiavi|superchiave]] di $R$
Dobbiamo dimostrare che per ogni istanza $r$ di $R$ valga $$\pi_{T_1}(r) \bowtie \dots \bowtie \pi_{T_n}(r) \subseteq r$$ sia $e \in  \pi_{T_1}(r) \bowtie \dots \bowtie \pi_{T_n}(r)$ 
per _[[Modello relazionale - Algebra Relazionale|definizione di giunzione]]_ si ha che esistono $e_i \in \pi_{T_i}(r)$ tale che per $i$ in $i,\dots,n,e_i[T_i]=e[T_i]$
per _[[Modello relazionale - Algebra Relazionale|definizione di proiezione]]_  esistono $e_i' \in r$ tale che per $i$ in $1,\dots,n,e'_i[T_i]=e_i[T_i]$ da cui $e'_i[T_i]=e[T_i]$

allora basta dimostrare che $e=e_1'$ siccome da questo segue la tesi poiché $e'_1 \in r$

Costruendo la relazione $s$ con schema $R(T)$ con solo le due ennuple $e$ e $e'_1$ se questa soddisfa $F$ allora vale $e=e_1'$ siccome queste due coincidono sulla _superchiave_

Poiché la scomposizione _preserva le dipendenze_, è sufficiente dimostrare che $s$ soddisfa $\pi_{T_i}(F)$ per ogni $i$  
osservando che per goni dipendenze $X \rightarrow Y$ e per ogni $T' \subseteq T$ che includa $X,Y$ un relazione $r \in \langle T,F \rangle$ soddisfa la dipendenza se e solo se la soddisfa $\pi_{T'}(r)$.
Quindi anche $s$ soddisfa $\bigcup_i\pi_{T_i}(F) \iff \pi_{T_i}$ ovvero $\{ e[T_i],e'[T_i]\}$ soddisfa $\pi_{T_i}(F)$ per ogni $i$

$\{ e[T_i],e'[T_i]\}$ soddisfa $\pi_{T_i}(F)$  poiché $\{ e[T_i],e'[T_i]\} \subseteq \pi_{T_i}(r)$ e quindi $e_i'[T_i]=e_i[T_i]$ e $e'_1$ ed $e_i'$ sonno entrambi in $r$