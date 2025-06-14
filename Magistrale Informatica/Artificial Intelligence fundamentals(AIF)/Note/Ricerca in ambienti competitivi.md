---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Ricerca in ambienti competitivi
---
in [[Definizione di Problemi-Ambienti|ambienti multi-agente]] accade che gli agenti siano in **competizione** tra loro, allora se un dato [[Agenti Razionali|agente]] deve raggiungere uno stato [[Problemi di ricerca|obiettivo]] bisognare usare l'approccio dell’**adversarial search**.

Il dominio privilegiato per lo studio di tali dinamiche è rappresentato dai giochi a due giocatori a somma zero, come scacchi, Go e poker, nei quali l’obiettivo di un agente è diametralmente opposto a quello dell’altro. Questi giochi offrono una struttura particolarmente adatta alla formalizzazione algoritmica: la rappresentazione dello stato è generalmente compatta, lo spazio delle azioni è contenuto e le regole che governano la transizione tra stati sono esplicite e ben definite. La semplicità apparente del dominio consente però di sviluppare algoritmi che affrontano efficacemente la complessità insita nella pianificazione contro un avversario che pianifica a sua volta.

La formalizzazione teorica si avvale di strumenti derivati dalla **[[Teoria dei giochi (Game theory)|teoria dei giochi]]**, i quali permettono di distinguere tra tre approcci principali. 
1. tipico dell’**economia**, aggrega i comportamenti degli agenti per trarre previsioni globali senza analizzare le singole azioni.
2. interpreta l’avversario come una fonte di non determinismo, ma perde la specificità dell’intenzionalità strategica.
3. impiega **alberi di gioco** e algoritmi specifici come il **[[Ricerca MiniMax|minimax]]**, una generalizzazione del modello [[Alberi di ricerca AND-OR|AND–OR]]

Il gioco può essere definito formalmente come:
- $S_0$ lo **stato iniziale**  
- $\text{TO-MOVE}(s)$ specifica quale **giocatore** $p$ ha il turno in $s$
- $\text{ACTIONS}(s)$ le azioni in uno stato $s$ 
- $\text{RESULT}(s, a)$ descrive il **modello di transizione** dato un’azione $a$ in $s$.
- $\text{IS-TERMINAL}(s)$, che restituisce vero se $s$ è uno **stato terminale**. 
- $\text{UTILITY}(s, p)$ una **funzione di utilità** che assegna un valore numerico all'esito per ciascun giocatore $p$ in uno **stato terminale** 

le funzioni $S_0$, $\text{ACTIONS}$ e $\text{RESULT}$ definiscono un **grafo dello spazio degli stati**, in cui i nodi sono stati e gli archi rappresentano le azioni. A partire da questo grafo, è possibile costruire un **albero di ricerca**, una struttura sovrapposta che esplora le sequenze di mosse. Quando tale albero comprende tutte le sequenze di mosse fino agli stati terminali, viene definito **albero del gioco** (*game tree*). Il **game tree** può essere anche una struttura infinita a seconda delle regole del gioco in cui si sta facendo ricerca 
***ply***: Ogni mossa di un singolo giocatore 





