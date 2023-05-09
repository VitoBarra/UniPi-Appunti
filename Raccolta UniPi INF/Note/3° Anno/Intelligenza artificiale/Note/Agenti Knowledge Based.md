---
type: nota
course: Intelligenza Artificiale
topic: 
tags: IA
---

Prev: [[Introduzione Intelligenza Artificiale (IIA)]]

# Agenti Knowledge Based
---
- una [[Agenti Razionali|agente]] basato sulla conoscenza mantiene una _[[Base di conoscenza (KB)|Base di conoscenza]]_ detta _knowledg base_ o _KB_: un insieme di enunciati espressi in un linguaggio di rappresentazione
- interagisce con la KB mediante una interfaccia funzionale tell-ask
	- _tell_: per aggiungere nuovi enunciati da KB
	- _ask_: per interrogare la knowledge base
	- _react_: per eliminare enunciati
- gli enunciati nella _KB_ rappresentano le opinioni/credenze del agente
- la e risposte $\alpha$ devono essere tali che $\alpha$ discende necessariamente da _KB_


## Trade-off fondamentale dell R.C
il problema _fondamentale_ in R.C. è trovare il giusto compromesso tra:
- _Espressivita_ del linguaggio di rapresentazione
- _Complessita_ del meccanismo inferenziale
queste due caratteristiche sono in contrasto tra loro siccome un linguaggio piu _espressivo_ rende meno efficente il meccanismo inferenziale 



### Formalismi per la rappresentazione della conoscenza
una formalismo per la rappresentazione della conoscenza ha tre componenti:
1. _sintassi_: un linguaggio composto d un vocabolario e regole per la formazione delle frasi (_enunciati_)
2. _semantica_: stabilisce una corrispondenza tra gli enunciati e i fatti del mondo; se una agente ha un enunciato $\alpha$ nella sua KB crede che il fatto corrispondente sia vero nel mondo
3.  _[[Sistemi di deduzione (o di Inferenza)|meccanismo inferenziale]]_: codificato tramite delle regole che ci consente di inferire nuovi fatti dai fatti presenti nella KB
 

### Rapresentazione del mondo
![[45A9F253-941A-4547-B9D1-096ACB8D3797.jpeg]]


#### Problemi di questo tipo di agente
1. complessità di $KB \models \alpha$
3. quali sono gli algoritmi di decisione e le strategie di ottimizzazione?
4. i Linguaggi logici:
	1. [[ Calcolo proposizionale (PROP)|calcolo proposizionale]]
	2. [[Logica del primo ordine (FOL)|Logica del predicati del prim ordine]]
5. questi linguaggio sono adatti per la rappresentazione della conoscenza?