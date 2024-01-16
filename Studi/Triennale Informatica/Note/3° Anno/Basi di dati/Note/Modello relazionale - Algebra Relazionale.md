---
type: nota
course: Data Base
topic: 
tags:
  - DB
Parent MOC: "[[Data Base (DB)]]"
---

# Modello relazionale -Algebra Relazionale
---
la semplicità  del [[Modello dati - Modello Relazionale|Modello relazionale]] viene anche dalle _operazioni_ su [[Relazioni tra insiemi|relazioni]] che restituiscono altre relazioni.  
per _algebra relazionale_ si intendono proprio queste tipologie di operazioni


### Algebra relazionale
#### Notazione
- $R,S$  sono [[Relazioni tra insiemi|Relazioni]]
- $A,B$  sono _attributi_.
- $X,Y$ sono _insiemi di attributi_.
- $XY$ e' un’abbreviazione per $X \cup Y$;
- $\{t_1, t_2, \dots , t_n\}$ indica le _ennuple_ $t_1, t_2, .\dots , t_n$  della relazione 
- $\{t_1, t_2, \dots , t_n\}$ induca una relazione _vuota_
- $t_k.A_i$  indica il valore del _attributo_ $A_i$ nell’_ennupla_ $t_k$  
- $t.X$ o $t[X]$ con $X$  un _sottoinsieme degli attributi_ di $t$, _Indica_ l’ennupla ottenuta da $t$ considerando solo gli _attributi_ in $X$;
- se due relazioni $R$ ed $S$ hanno lo stesso attributo $A_j$  
	- $R.A_j$ denota l’_attributo_ $A_j$ della _relazione_ $R$
	- $S.A_j$ denota l’_attributo_ $A_j$ della _relazione_ $S$

#### Operazioni primitive
##### Ridenominazione
la _ridenominazione_ cambia il _[[Modello dati - Modello Relazionale|tipo di una relazione]]_ $R$.

_Siano_ 
- $X$ gli _attributi_ di $R$,
- $A,B$  due _attributi_ tali che $A \in  X$ e $B \notin X$. 
_allora_  la _Ridenominazione_ del attributo $A$ in in attributo $B$ di $R$ è una relazione definita come:$$\rho_{A\leftarrow B}(R) = \{t \mid \exists u \in   R . t[B] = u[A] \land  t[C] = u[C]\}$$ con $C \not=B$
dove rispetto al _[[Logica proposizionale|and]]_($\land$)
- la parte sinistra rinomina l attributo mantenendo i valori uguali 
- la parte destra assicura che gli attributi non rinominate non cambino valore 

La relazioni ha _attributi_
$$\rho_{A\leftarrow B}(R) :\{  X − {A} ∪ {B}\}$$
##### Unione
_siano_  $R, S$ _relazioni_ dello _stesso tipo_
_allora_ la loro _unione_ è definita come
$$R \cup S = \{t \mid t \in   R \lor t \in   S\}$$
Restituisce la _relazione_ ottenuta facendo l’unione
delle ennuple di $R$ con quelle di $S$

##### Differenza
_siano_ $R,S$ relazioni dello stesso tipo
_allora_ la _differenza_ tra le due è definita come $$R - S = \{t \mid t \in  R \land t \notin S\}$$Restituisce la _relazione_ contenente le ennuple
di $R$ non presenti in $S$
##### Proiezione
_siano_  $A_1, A_2,\dots , A_m$ _attributi_ di $R$
$$\pi_{A_1,\dots,A_m}(R) = \{t[A_1A_2 \dots A_m] \mid t ∈ R\}$$
Restituisce una _relazione di tipo_ $\{(A_1 : T_1, A_2 :T_2, \dots, A_m : T_m)\}$ i cui elementi sono la copia delle _ennuple_ di $R$ proiettate sugli _attributi_ $A_1, A_2, \dots , A_m$. 

poichè le _[[Relazioni tra insiemi|relazioni]]_ sono _[[Insiemi Matematici|insiemi]]_, eventuali _ennuple_ uguali dopo la proiezione appaiono una sola volta nel risultato.
##### Restrizione
_siano_ $R$ una _relazione_ e $\phi$ una _condizione_
_allora_ una sua _restrizione_$$\sigma_{\phi}(R) = \{t \mid t \in  R \land \phi(t)\}$$
Restituisce una relazione dello _stesso tipo_ di $R$ i cui elementi sono la copia delle ennuple di $R$ che _soddisfano la condizione_.

La condizione $\phi$ e una formula definita `
come segue:
- $A_i \ \theta\  A_j$ dove
	-  $A_i$ e $A_j$ attributi di $R$ 
	-  $\theta$ un operatore di confronto $\{<, >, =, \not=, \leq,\geq\}$;
- $A_i\ \  \theta \ \ c$, oppure $c \ \ \theta \ \ A_i$ dove 
 - con $\theta$ un operatore di confronto e $c$ una costante in $dom(A_i)$;
-  se $\phi$ e $\psi$ sono formule, allora lo sono anche $\phi \land \psi,\  \phi ∨ \psi ,\  \neg\psi$.


##### Prodotto
_siano_ $R(A_1 : T_1, \dots , A_n : T_n)$ e $S(A_{n+1} : T_{n+1}, \dots , A_{n+m} : T_{n+m})$ _relazioni_ con _attributi distinti_. 
_allora_ il loro _prodotto_ è definito $$R \times S = \{tu \mid t \in   R \land u \in   S\}$$Restituisce una _relazione_ del tipo $\{(A_1 : T_1, \dots , A_n : T_n, A_{n+1} : T_{n+1}, \dots ,A_{n+m} : T_{n+m})\}$ con elementi ottenuti concatenando ogni _ennupla_ di $R$ con tutte quelle di $S$.

La _concatenazione_ $tu$ di due _ennuple_ $t$ e $u$ è un’ennupla che ha come coppie $(A_i, V_i)$ tutte quelle di $t$ e di $u$, e si indica anche con $t ◦ u$. 

La relazione _risultante_ ha
- _grado uguale_ alla _somma dei gradi degli operandi_, 
- _[[Cardinalità di un insieme|cardinalità]]_ uguale al _prodotto delle cardinalità_ degli operandi. 

Il nome di questo _operatore_ e dato dalla sua somiglianza con il [[Prodotto Cartesiano|prodotto cartesiano]] di insiemi, sebbene dia come risultato un insieme di ennuple concatenate invece di un insieme di coppie di ennuple, come accadrebbe nel normale _prodotto cartesiano_.


#### Espressione dell’algebra relazionale
Un’espressione dell’_algebra relazionale_ e definita come segue: 
- Una relazione $R$ o una relazione ${t_1, t_2, \dots , t_n}$ sono espressioni dell’algebra;
- _se_ $E, E_1 E_2$ sono _espressioni dell’algebra_, lo sono anche
	- $E_1 \cap E_2$, se $E_1$ e $E_2$ hanno lo stesso tipo;
	- $E_1 − E_2$ , se $E_1$ e $E_2$ hanno lo stesso tipo;
	- $E_1 \times E_2$, se $E_1$ e $E_2$ non hanno attributi comuni;
- $\sigma_C(E)$, _se_ $C$ e una condizione su attributi di $E$;
- $\pi_X(E)$, _se_ $X$ sono attributi di $E$;
- $\rho_{A \leftarrow B}(E)$, _se_ $X$ sono gli attributi di $E$, $A$ e $B$ sono due attributi tali che $A \in X$ e $B \notin  X$.


#### Operatori Derivati
Sono _operatori_ derivati dagli _operatori principali_
##### Intersezione
_siano_  $R,S$ relazioni dello stesso tipo$$R \cap S = \{t \mid t \in  R \land t \in  S\}$$Restituisce la _relazione_ ottenuta facendo l’intersezione delle ennuple di $R$ e di $S$. 
Vale l’equivalenza $R \cap S \equiv R − (R − S)$.


##### Divisione
_Siano_
- $XY$ gli _attributi_ di $R$ 
- $Y$ gli attributi di $S$. 
_allora_ l operazione di _divisione_ è definita come 
$$
\begin{array}{}
R \div S  & = &  \{w \mid \forall s \in   S.\ \ \ w ◦ s \in   R\} \\
 & = &  \{w \mid {w} \times S \subseteq R\}
\end{array}
$$
e questo _restituisce_ una relazione $W = R \div S$  con attributi $X$ ed elementi $w$ 

Vale l’equivalenza $$R \div S \equiv \pi_X(R) − R_1$$con $R_1 = \pi_X((\pi_X(R) \times S) - R)$.


_Se_ 
- Gli attributi di $S$ e $W$ sono _disgiunti_ 
- La loro unione restituisce gli attributi di $R$
_allora_ Il _prodotto_ e la _divisione_ sono legati dalle seguenti relazioni
$$(W \times S) \div S = W,(R \div S) \times S \subseteq R$$
 $R \div S$ è il _massimo insieme_ per cui vale $$(R \div S) \times S \subseteq R$$
 
 > [!tip]
 La _divisione_ $R \div S$ è utile compiere operazioni del tipo: 
 trovare le _ennuple_ di $R$ _associate_ a tutte le ennuple di $S$


##### Giunzione
_Sia_  
- $R(A_1 : T_1, \dots , A_n : T_n)$ ed $S(A_{n+1} : T_{n+1}, \dots , A_{n+m} : T_{n+m})$ _relazioni_ con attributi distinti,
- $A_i$ _attributo_ di $R$ e $A_j$ _attributo_ di $S$.
_allora_ l operazione di _giunzione_ è definito come:
$$R \underset{A_i=A_j}{\bowtie}  S = \{tu \mid t \in   R, u \in   S, t.A_i = u.A_j
\}$$
Restituisce una _relazione di tipo_${(A_1 : T_1, \dots. , A_n : T_n, A_{n+1} : T_{n+1}, \dots , A_{n+m} : T_{n+m})}$ con elementi _la copia delle ennuple_ del [[Prodotto Cartesiano|prodotto cartesiano]] di $R$ ed $S$, con valori uguali per gli attributi $A_i$ e $A_j$
ovvero $$(R \underset{A_i=A_j}{\bowtie}  S) \equiv \sigma_{A_i=A_j} (R \times S)$$
Questo _operatore e di solito_ chiamato _equi join_ per distinguerlo dal $\theta$-join


##### Giunzione naturale
_siano_ 
- $R(YX),S(ZX)$ due _relazioni_
- $X$ gli Atributi comuni con stesso nome e _stesso dominio_ 
_allora_ l operatore di _funzione naturale_  è definito come
- $$R \bowtie S = \{t  \mid t[YX] \in   R , \ \   t[ZX] \in  S\}$$
_restituisce_  quindi una relazione con attributi $(YXZ)$

In operatori _primitivi si ha_
 Siano $A_1, \dots, A_n$ gli attributi $X$ comuni ad $R$ ed $S$.
1. Si cambia _il tipo_ di $R$ ed $S$, in modo da rendere diversi gli attributi comuni, definendo:
$$\begin{array}{}
R’ &  = &  \rho_{ A_1\leftarrow RA_1,\dots,A_n\leftarrow RA_n}(R) \\
S’  & = &  \rho_{ A_1\leftarrow SA_1,\dots,A_n\leftarrow SA_n}(S) 
\end{array}
$$
2. Sia $T = \sigma_{RA_1=SA_1 \land \dots  \land RA_n=SA_n}(R’ \times S’)$
3. La _giunzione naturale_ di $R$ ed $S$ e la relazione `
$$\rho_{RA_1\leftarrow A_1
,\dots,RA_n\leftarrow A_n}
(\pi_{ RA_1
,\dots,RA_n,YZ}(T))$$

Si ottiene cosi una _relazione_ che ha come attributi l’_unione_ di quelli degli _operandi_, con le ennuple formate concatenando quelle di $R$ ed $S$ con _valori uguali_ per gli attributi in comune eliminando le coppie ridondanti.
La _giunzione naturale_, è una abbreviazione dell’ _equi join_ applicato a relazioni in cui l’associazione fra le ennuple e descritta con la _[[Modello Relazionale - Chiavi|chiave esterna]]_ e la chiave _primaria costituite_ da attributi uguali.
Si noti che:
- se $R$ ed $S$ non hanno attributi comuni: $$R \bowtie S \equiv R \times S$$
- se $R$ ed $S$ hanno lo stesso schema: $$R \bowtie S \equiv R \cap S$$

##### Semi-giunzione
_sia_ $X$  gli attributi comuni tra $R$ ed $S$ 
_allora_ l operazione d semi funzione è definito come: $$R \ltimes S = \{t \in  R \mid t[X] \in   \pi_X(S)\}$$
_Restituisce_ le ennuple di $R$ che partecipano
alla _giunzione naturale_ di $R$ ed $S$.
Vale l’equivalenza 
$$R \ltimes S \equiv \pi_{A_1,A_2,\dots,A_m} (R\bowtie S)$$
con $A_1, A_2, \dots , A_m$ gli attributi di $R$


> [!tip]
> gli _operatori di giunzione_, consentendo di correlare ennuple di relazioni diverse tramite il meccanismo di _chiave esterna_

#### Altri Operatori
altri _operatori del algebra_ relazionale sono stati introdotti per la loro utilità in campo. 
questi non possono essere derivati direttamente dagli _operatori base_

##### Proiezione generalizzata
_siano_
 - $e_1, \dots , e_n$ espressioni aritmetiche, ottenute a partire da costanti e attributi di $E$
 - $ide1, \dots , ideN$ etichette distinte.
_allora_ la _proiezione generalizata_ è definita da $$\pi_{e_1 \ \boldsymbol{AS} \ ide1,\dots, e_n\  \boldsymbol{AS} \ ideN}(E)$$

La _proiezione generalizzata_ estende la _proiezione_ con la possibilità di usare costanti o espressioni aritmetiche nella lista degli attributi. 
Per comodità si può anche assegnare un’etichetta ad un’espressione con l’operatore _AS_



##### Funzione di aggregazione e raggruppamento
Le _funzioni di aggregazione_ hanno come argomenti _[[Struttura dati - MultiInsieme|multinsiemi]]_ e ritornano come risultato un _valore_.

Per esempio, le funzioni di aggregazione 
- _sum_ ritorna la _somma_ degli
elementi
- _avg_ ritorna la _media_ dei valori
- _count_ ritorna il _numero_ degli elementi,
-  min e max ritornano _il minimo e il massimo_ valore degli elementi. 

se vogliamo trattare il _mutiinsieme_ come _[[Insiemi Matematici|insieme]]_ ovvero vogliamo  ignorare i duplicati si aggiunge alla funzione la _stringa_ “-distinct” 

Le _funzioni di aggregazione_ si possono usare con l’operatore di _proiezione generalizzato_ per produrre una _relazione_ con un’unica ennupla. 

_siano_
- $R$ una relazione
- $A_1,\dots,A_{m}$ sono attributi di $R$ 
- dove $f_{1},\dots,f_{n}$ sono _funzioni di aggregazione_
- $ide_1,\dots,ide_n$ identicatori distinti
_allora_ le funzioni di aggregazione nella selezione generalizzata si possono usare _come_$$\pi_{f_{1}(A_i)\ \ \boldsymbol{AS} \ \ ide_{1},\ \dots \ , f_{n}(A_n)\ \  \boldsymbol{AS}\ \ ide_{n}(R)}$$
nella _proiezione_, le _funzioni di aggregazione_ __non__ si possono usare insieme ad attributi diversi da _costanti_.
infatti l espessione: `
$$\pi_{A_1, f_{i}(A_{j}) \boldsymbol{AS} ide_{i}}(R)$$
è __Scorretta__.

Per combinare nella proiezione _attributi_ e valori di _funzioni di aggregazione_ bisogna
usare le _funzioni di aggregazione_ con l’operatore di raggruppamento $\gamma$, 

definito come
_sia_
- $E$ Relazione
-  $A_1, \dots, A_n$ sono attributi di $E$ 
-  $f_1, \dots , f_m$ sono _funzioni di aggregazione_ 
_allora_ un operatore di _raggruppamento_ è definita come $$A_1,\dots,A_n \gamma f_1,\dots,f_m(E)$$
Restituisce una _relazione di tipo_ ${(A_1: T_1, \dots , A_n : T_n, f_1 : T_{f1}, \dots , f_m :T_{f_m})}$
con $T_{f_1}, \dots , T_{f_m}$ i tipi dei risultati delle _espressioni_ $f_1, \dots , f_m$, 

Le espressioni sono calcolate nel seguente modo:
- si _partizionano_ le ennuple di $E$ in un _insieme di gruppi_, mettendo nello stesso gruppo tutte le ennuple che coincidono su tutti gli attributi $A_1, \dots , A_n$. Se l’insieme
$\{A_1, \dots , A_n\}$ è vuoto, gli elementi di E fanno parte di un _unico gruppo_;
- si calcolano le _funzioni di aggregazione_ per ogni _gruppo_;
- si _restituisce_ una relazione con _un’ennupla per ogni gruppo_ e componenti i valori degli attributi $A_1, \dots , A_n$ e i risultati delle espressioni $f_1, \dots, f_m$.
![[IMG_1062.jpeg]]
