---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Ricerca in ambienti parzialmente osservabili
---
per risolvere un [[Problemi di ricerca|problema di ricerca]] In un **[[Definizione di Problemi-Ambienti|ambiente]] parzialmente osservabile** si vuole  definire la funzione $PERCEPT(s)$  che rappresenta le percezioni locali ottenibili dal [[Agenti Razionali|agente]], queste saranno meno informative di poter vedere tutto il mondo. 
Più **stati** possono generare lo stesso **percetto** e quindi la percezione non individua univocamente lo stato reale, ma definisce uno **belief state** iniziale $b_0$, che rappresenta l’insieme degli stati **coerenti** con il percetto ricevuto.

1. **Predizione**: attraverso la funzione $PREDICT(b, a) = \hat{b}$ (o $RESULT(b, a)$), si calcola lo stato di credenza risultante dall’esecuzione dell’azione $a$ a partire dallo stato di credenza $b$. Questo passaggio è analogo a quello nei [[Problemi di Ricerca in spazi non deterministici]], dove le azioni possono avere effetti multipli.
2. **Percezione possibile**: si determinano i possibili percetti osservabili ($o$) nello stato predetto $\hat{b}$ come segue:$$
   POSSIBLE\text{-}PERCEPTS(\hat{b}) = \{o : o = PERCEPT(s) \land s \in \hat{b} \}
   $$
3. **Update**: per ogni percetto possibile $o$, si calcola uno stato di credenza aggiornato:$$
   b_o = UPDATE(\hat{b}, o) = \{s\ :\  o= PERCEPT(s) \land s \in \hat{b}\}
   $$Questo passaggio consente la riduzione dell’incertezza, poiché l’osservazione agisce come filtro sugli stati coerenti con l’azione appena eseguita. 
	2. la presenza di **non-determinismo** nell’ambiente fisico tende ad ampliare lo stato di credenza nella fase di predizione $\hat{b}$ , ma la successiva fase di update può soltanto restringere l’incertezza e quindi varra che ad ogni step di update $|b_0|\leq \hat{b}$.
	3. Nel caso di **sensing deterministico**, i **belief state** generati da ogni possibile osservazione saranno disgiunti tra loro, formando una [[Partizione di un insieme|partizione]] di $\hat{b}$. 

La combinazione dei tre passaggi produce l’insieme degli stati di credenza futuri:
$$
\begin{array} {l}
RESULTS(b, a)  & =   \{  b_o : &b_o&   = &  UPDATE(PREDICT(b, a), o) \ \text{and} \\
 &            &  o  & \in &  POSSIBLE\text{-}PERCEPTS(PREDICT(b, a))\}

\end{array}
$$


Questa definizione consente l’applicazione diretta dell’algoritmo di [[Alberi di ricerca AND-OR]] ma applicato sul **belief state** corrente. 

La pianificazione su stati di credenza impone inoltre la necessità di confrontare insiemi di stati: l’agente può riconoscere che un belief state già visitato è un sottoinsieme o un sovrainsieme di uno nuovo, e quindi evitare esplorazioni ridondanti. Questo meccanismo migliora significativamente l’efficienza computazionale.

Infine, la struttura risultante è compatibile con l’estensione ad algoritmi di ricerca incrementale, in grado di aggiornare il piano man mano che nuove informazioni vengono acquisite, promuovendo una maggiore reattività e robustezza del comportamento dell’agente in ambienti dinamici.
