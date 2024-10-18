---
Course: Elementi di calcolabilita e complessita
topic: nota
tags: ECC
---

Prev: [[Elementi di Complessità e Calcolabilità (ECC)]]

# Linguaggi FOR e WHILE
---
I linguaggio sono [[Nozione di Calcolabilità|modelli di calcolo]] 
## Sintassi astratta

la sintassi astratta di un _nucleo_ di un linguaggio di programmazione è
$$
\begin{align*}
&E:= n  | X | E_1 + E_2 | E_1 *E_2 | E_1 /  E_1| E_1 - E_2 \\
&B := b | E_1-E_2 | \neg b | B_1 \lor B_2 \\
&C := skip | x=E | C_1;C_2 | if\  B \ then \ C_1 \ else \ C_2 | \ while \ B \ do\  C | \ for \ x=E \ to \ E_1 \ do\  C
\end{align*}
$$

dove viene definito linguaggio _FOR_ quello dove è omesso il $C :=\ while \ B \ do\  C$  e linguaggio _WHILE_ quello dove invece c è con indifferenza della presenza o meno del costrutto for. questo perché il for si può emulare con un while mentre il contrario no

il linguaggio _WHILE_ è più espressivo perché può esprime i programmi che non terminano mai, mentre il linguaggio _FOR_ non può fare questo perché è garantito che dopo un numero finito di esecuzioni del for si esca da esso.

>[!note]
>questo linguaggio rappresenta solo numeri natura e espressioni booleane

## Computazione
per la computazione abbiamo bisogno di definire delle funzioni 
### 1. _Funzione della memoria_ 
$$\sigma: Var \rightarrow \mathbb{N}$$
che è la funzione memoria che va da una variabile ad un valore nei naturali siccome questa è l unica cosa esprimibile in questo linguaggio 
### 2. _funzione d aggiornamento della memoria_ 
$$-[-/-]:(Var \rightarrow \N)\times\N \times Var \rightarrow(Var \rightarrow \N)$$
definita come: 
$$
\sigma[n/x](y)=\begin{cases}
 n        & \text{ se y=x} \\
\sigma(y) & \text{ altrimenti}
\end{cases}
 $$
 questa funzione aggiorna il valore in $\sigma$ rendendo $x=n$ 
 ### 3. _semantica delle espressioni_ 
 $$\mathcal{E}\bsl-\bsr-:E\times(Var \rightarrow\N)\rightarrow\N $$
 definita come:
	 $$
	 \begin{array}{ccc}
	 \mathcal{E} \bsl n \bsr \sigma & = & n \\
	 \mathcal{E} \bsl x \bsr \sigma & = & \sigma(x) \\
	 \mathcal{E} \bsl E_1+E_2 \bsr \sigma & = & \mathcal{E} \bsl E_1\bsr\sigma 
	 \text{ più }\mathcal{E} \bsl E_2 \bsr\sigma \\
	 \mathcal{E} \bsl E_1 \times E_2 \bsr \sigma & = & \mathcal{E} \bsl E_1\bsr\sigma \text{ per }\mathcal{E} \bsl E_2 \bsr\sigma \\
	 \mathcal{E} \bsl E_1-E_2 \bsr \sigma & = & \mathcal{E} \bsl E_1\bsr\sigma \text{ meno }\mathcal{E} \bsl E_2 \bsr\sigma \\
	 \end{array}
	 $$
dove "più" ,"per", "meno" sono funzioni effettive e non simboli sintattici. la funzione "meno " è limitata siccome da vede andare dai naturali ai naturali se la sottrazione  risulta un numero negativo restituisce 0
### 4. _Semantica delle espressioni booleane_
$$
\mathcal{B}\bsl-\bsr-: B \times (Var \rightarrow \N) \rightarrow Bool
$$
Definita come:
$$
\begin{array}{ccc}
\mathcal{B}\bsl t\bsr \sigma & =& tt \\
\mathcal{B}\bsl f\bsr \sigma & =& f \\
\mathcal{B}\bsl E_1 < E_2\bsr \sigma & =& \mathcal{E}\bsl E_1\bsr\sigma \text{ minore } \mathcal{E}\bsl E_2\bsr\sigma \\
\mathcal{B}\bsl \neg B \bsr \sigma & =& \text{not } \mathcal{B}\bsl B\bsr\sigma\\
\mathcal{B}\bsl B_1 \lor B_2\bsr \sigma & =& \mathcal{B}\bsl B_1\bsr\sigma \text{ or } \mathcal{B}\bsl B_2\bsr\sigma 

\end{array}
$$
dove "minore", "not" e "or" sono funzioni effettive e non simboli sintattici.
### 5. _Sistema di transazioni_
$$(\Gamma, \rightarrow)$$
dove 
- $\Gamma$ è la classe delle configurazioni (nel nostro caso la classe delle coppie $⟨c \in C, \sigma⟩$ dove $\sigma$ è definita per ogni variabile che appaia in comando; la coppia con il comando c vuoto ($\not=$ skip) è abbreviata da $\sigma$);
- $\rightarrow \subseteq \Gamma \times \Gamma$ è una funzione, detta di _transizione_

definito da: 
![[Pasted image 20221012224529.png]]
sono regole  operazionali definite con le regole di inferenza; descrivono da quale stato si può transire a quale altro restando del tutto generali sul comando specifico. 
queste regole derivano dalla sintassi e sono tutte e sole le transizioni possibili il che significa che questa è la minima classe che contiene tutte le istanze degli assiomi ed è chiusa rispetto alle regole di inferenza 
ovvero 
- minima :soddisfano queste e _solo_ queste proprieta
- chiusa: ogni regola porta ad uno stato che può coprire una regola nel insieme 

>[!warning]
>la regola del FOR ha un problema sulla spostamento del indice $E_i$ siccome si mescola sintassi e semantica

### Definizione finale
questo definisce tutte le funzioni che servono a definire la computazione che è quindi definita in questo caso da un approccio [[Semantica dinamica#Small Step|Small Step]] ovvero
$$\textlangle c,\sigma\textrangle \rightarrow \textlangle c',\sigma'\textrangle$$
ovvero la [[Macchina Astratta]] che sta eseguendo la nostra computazione passa dal primo stato al secondo grazie ad un passo d esecuzione

possiamo definire l intera computazione come 
$$\textlangle c,\sigma\textrangle \rightarrow^* \textlangle c',\sigma'\textrangle$$
dove 
- Se _termina_ converge ($\downarrow$) a $\sigma'$
- se _non termina_ diverge ($\uparrow$) 