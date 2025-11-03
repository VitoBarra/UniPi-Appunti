---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Planning - Agenti Sensorless
---
Gli **agenti sensorless** per il [[Planning - Domini incerti|planning in ambienti incerti]] operano in [[Definizione di Problemi-Ambienti|ambienti non osservabili]], dove non dispongono di alcuna **informazione percettiva** sullo stato del mondo, ma le azioni sono considerate [[Definizione di Problemi-Ambienti|deterministiche]]. In questi scenari, l’agente non può distinguere quale stato effettivo si verifichi dopo l’esecuzione di un’azione, e deve quindi pianificare considerando un insieme iniziale di stati possibili, noto come **belief state iniziale** $b_0$ e partendo da questo si segue lo stesso schema di ricerca [[Ricerca in spazi NON osservabili|ricerca in ambienti non osservabili]] ma in questo si usa il [[Planning - Planning Domain Definition Language (PDDL)|PDDL esteso]] e quindi lo stato è  [[Rappresentazione del ambiente|fattorizato]].

Ogni fluente nel belief state può essere vero, falso o sconosciuto. L’applicazione di un’azione modifica il belief state secondo le seguenti regole:
1. Se l’azione aggiunge un fluente, esso diventa vero in $b'$ indipendentemente dal valore iniziale.  
2. Se l’azione elimina un fluente, esso diventa falso in $b'$ indipendentemente dal valore iniziale.  
3. Se l’azione non influenza, il suo valore rimane sconosciuto se lo era in $b$.  

Questo meccanismo assicura che i belief states rappresentati come congiunzioni di literali ([[K-Forma normale congiuntiva (CNF)|1-CNF]]) rimangano chiusi sotto l’aggiornamento delle azioni PDDL. Ciò permette di rappresentare in modo compatto insiemi molto grandi di stati fisici possibili, con complessità lineare rispetto al numero di fluente $n$, invece che esponenziale $2^n$.  

In presenza di **conditional effects**, gli effetti di un’azione dipendono dallo stato corrente, creando dipendenze tra i fluents e rendendo l’applicazione dell’azione non più un’[[Operazioni chiuse|operazione chiusa]] in 1-CNF. Ad esempio:$$
\begin{align*}
&\text{Action}\Big(\text{Suck}, \\
&\quad \text{EFFECT: } \text{when } \text{AtL: } \text{CleanL} \ \wedge \ \text{when } \text{AtR: } \text{CleanR} \Big)
\end{align*}
$$Per applicare un’azione con conditional effects a un **belief state** $b$, si seguono le regole seguenti:
1. Per ogni condizione soddisfatta nello stato corrente, si applica l’effetto corrispondente.  
2. Se una condizione $when$ non è soddisfatta nel **belief state** l azione non ha effetto.
3. se le $PRECO$ non sono soddisfare applicare l azione rende il **belife state** undefined


La ricerca di un piano sensorless consiste nel trovare una sequenza di azioni $\langle a_1, a_2, \ldots, a_n \rangle$ tale che, partendo da $b_0$, l’applicazione delle azioni conduca a un belief state $b_n$ in cui tutti gli stati soddisfano l’obiettivo $G$:
$$
\forall s \in b_n, \; G(s) = \text{true}
$$
Il piano prodotto è **statico e non condizionale**, poiché l’agente non può reagire a percezioni, ma l’analisi dei belief states consente di verificarne la robustezza rispetto all’incertezza iniziale.  

Per guidare la ricerca nello spazio dei belief states, si utilizzano funzioni euristiche. Una funzione euristica ammissibile $h$ può essere definita considerando sottoinsiemi del belief state: se $b_1 \subseteq b_2$ allora $h^*(b_1) \le h^*(b_2)$. 
