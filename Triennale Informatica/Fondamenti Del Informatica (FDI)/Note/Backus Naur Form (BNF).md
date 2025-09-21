---
Course: "[[Fondamenti Del Informatica (FDI)]]"
tags:
  - FDI
Area: 
topic: 
SubTopic:
---

# Backus-Naur Form (BNF)
---
La **Backus-Naur Form** (**BNF**) è una notazione formale utilizzata per descrivere la sintassi dei linguaggi di programmazione e delle grammatiche formali. La sua struttura consente di rappresentare in modo preciso le regole di costruzione delle stringhe appartenenti a un linguaggio. In BNF, ogni regola è composta da un simbolo non terminale, seguito dal simbolo "::=" che indica definizione, e da una sequenza di simboli terminali e non terminali. I simboli non terminali vengono racchiusi tra segni di maggiore e minore, ad esempio $<espressione>$, mentre i simboli terminali rappresentano i caratteri o le sequenze di caratteri effettivamente presenti nel linguaggio.

Le regole possono includere alternative separate dal simbolo "$|$", che rappresenta una scelta tra più opzioni valide. La notazione permette anche la composizione ricorsiva, dove un non terminale può comparire all'interno della propria definizione, consentendo la descrizione di strutture di lunghezza arbitraria.

Matematicamente, una grammatica in BNF può essere definita come una quadrupla:  

$$
G = (N, \Sigma, P, S)
$$
dove:  
- $N$ è l'insieme dei simboli non terminali;  
- $\Sigma$ è l'insieme dei simboli terminali;  
- $P$ è l'insieme delle produzioni o regole di riscrittura, ciascuna nella forma $A ::= \alpha$, con $A \in N$ e $\alpha \in (N \cup \Sigma)^*$;  
- $S \in N$ è il simbolo iniziale della grammatica.  

Le produzioni possono essere rappresentate in maniera schematica, indicando chiaramente le alternative e la sequenza dei simboli. La BNF facilita l'analisi sintattica automatica, permettendo agli strumenti di parsing di riconoscere strutture complesse attraverso la ricorsione e le alternative.  

Le regole di derivazione consentono di costruire una stringa terminale partendo dal simbolo iniziale $S$, applicando ripetutamente le produzioni fino a ottenere una sequenza composta esclusivamente da simboli terminali. Questo processo è alla base della validazione sintattica e della generazione di codice nei linguaggi formali.
