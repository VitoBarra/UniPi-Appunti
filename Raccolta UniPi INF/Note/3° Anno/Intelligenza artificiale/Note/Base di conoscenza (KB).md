---
type: nota
course: Intelligenza Artificiale
topic: 
tags: IA
---

Prev: [[Introduzione Intelligenza Artificiale (IIA)]]

# Base di conoscenza (KB)
---
una _base di conoscenza_ è una rappresentazione esplicita, parziale e compatta in un linguaggio simbolico, che contiene:
- Fatti di tipo specifico
	- informazioni specifiche sullo stato di ciò che si sta rapresentando
- fatti di tipo generale, o regolo
	- appunto le regole di un gioco, conseguenze
una caratteristica della base di conoscenza è la _capacita inferenziali_  date dai [[Sistemi di deduzione (o di Inferenza)|Sistemi deduttivi]] , questi danno la capacita di derivare nuovi fatti da ciò che gia si conosce

>[!note]
>facendo un confronto con un  [[DataBase|DataBase]] si puo dire sia un base di conoscenza dove sono presenti solo fatti specifici, nessuna regola di carattere generale e manca quindi la capacita di inferire altra conoscenza. si puo fare solo retrieval di ciò che si gia conosce.



### Conseguenza logica
una formula $\alpha$ è _conseguenz alogica_ di un insieme di formule $KB$ se e solo se in ogni _modello_ di $KB$ anche $\alpha$ è vera ($KB \models \alpha$)

quindi Sia $M(KB)$ l insieme di _modelli_ del insieme di formule in $KB$ e $M(\alpha)$ l insieme dei _modelli_ di $\alpha$ allora
$$KB \models \alpha \iff M(KB) \subseteq M(\alpha)$$
la conseguenza logica si utilizza per formalizzazione di [[Sistemi di deduzione (o di Inferenza)|Sistemi di inferenza]] 

### Teorema di refutazione 
$$KB \models \alpha \iff (KB \land \lnot \alpha) \text{ è insodisfacibbile}$$  
 questo ci dice quindi che la conseguenza logica si puo riportare ad un problema [[Problema della Sodisfacibilita (SAT)|SAT]]
 