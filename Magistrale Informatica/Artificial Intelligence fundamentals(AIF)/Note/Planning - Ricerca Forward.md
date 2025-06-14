---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Planning - Ricerca Forward
---
La **ricerca nello spazio degli stati in forward** per la [[Planning|pianificazione]] si basa sull'applicazione di algoritmi euristici di [[Problem-Solving Agent|ricerca]]. Gli stati di questo spazio sono **stati ground** quindi ogni fluente è **$TRUE$** o $FALSE$. Lo **stato obiettivo** è uno stato che ha tutti i fluenti positivi del **obiettivo** sono soddisfatti e nessuno dei fluenti negativi è presente.  

Le azioni applicabili in uno stato, $Actions(s)$, sono **istanze gournded** degli **schemi d'azione**, ovvero azioni in cui tutte le variabili sono sostituite da costanti. 
Per determinare le azioni applicabili, si effettua un'[[FOL - Algoritmo di unificazione|unificazione]] tra lo stato corrente e le **precondizioni** di ciascuno **schema d'azione**. 
Ogni [[FOL - Algoritmo di unificazione|unificazione]] che produce una **[[FOL - Sostituzione|sostituzione]]** $\theta$ che grazie al fatto che le variabili presenti negli effetti di uno schema deve comparire anche nelle precondizioni, applicandola si ottiene un azione $\alpha$ **grounded** quindi senza variabili.  

Ogni schema può unificarsi in più modi. Quando una precondizione contiene più letterali, ciascuno di essi può potenzialmente corrispondere a più elementi dello stato corrente, aumentando il numero di azioni concrete generate.  

La dimensione dello spazio degli stati può crescere rapidamente in funzione del numero di azioni e della profondità della soluzione. In problemi complessi, il fattore di ramificazione medio può essere molto elevato, rendendo il numero totale di nodi da esplorare proibitivo senza l'uso di euristiche accurate. Gli algoritmi di ricerca sfruttano quindi informazioni euristiche per ridurre lo spazio di ricerca e rendere la pianificazione computazionalmente fattibile. Le euristiche possono essere specifiche del dominio oppure derivabili automaticamente, garantendo l'applicabilità della ricerca in avanti anche a problemi complessi.
