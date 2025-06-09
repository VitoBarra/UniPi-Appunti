---
Course: "[[Human Language Technology (HLT)]]"
Course 2: 
tags:
  - HLT
Area: "[[Emotion Recognition in Conversation (ERC)]]"
topic: "[[Lexicons for Sentiment, Affect, and Connotation]]"
SubTopic: "[[Affect Lexicon]]"
---
# Semi-supervised Induction of Affect Lexicon
---
Per costruire automaticamente degli [[Affect Lexicon]] si possono usare delle tecniche semi-supervisionate, utilizzando un piccolo set di parole "seme" per estendere l'etichettatura ad altre parole, sfruttando delle somiglianza semantiche.

Ne esistono due famiglie : le **Semantic Axis Methods** e le **Label Propagation (Graph-Based Methods)**.


## **Semantic Axis Methods**
Per etichettare le parole con questa tecnica semi-supervisionata si seguono i seguenti passi:
1. Si definiscono parole seme sia positive che negative
2. Si ottengono gli [[Embedding vettoriali]], come ad esempio i [[Word2Vec]] per tutte le parole
3. Si calcolano i centroidi dei due gruppi con le medie vettoriali:
    - $V^+=\cfrac{1}{n}\sum_{i=1}^n E(w_i^+)$
    - $V^-=\cfrac{1}{n}\sum_{i=1}^n E(w_i^-)$
4. Si costruisce l'asse semantico 
   $V_{\text{axis}}=V^+ - V^-$ 
5. Si calcola il punteggio per ogni parola
   $\text{score}(w)=\cos(E(w),V_{\text{axis}})$

Il punteggio finale di una parola indica quanto questa è vicina semanticamente alle parole positive. 
Questo punteggio si può usare sia in modo continuo oppure si può sogliare per ottenere un lessico binario.



## Label Propagation (Graph-Based)
Per etichettare le parole con questa tecnica semi-supervisionata si seguono i seguenti passi:
1. Si crea un grafo lessicale in cui :
	- ogni parola è un nodo 
	- si collegano i $k$ vicini più simili (attraverso il coseno tra embedding)
2. Si definisce un seed set positivo e uno negativo
3.  Si propaga via *random walks*:
	- si simula una passeggiata casuale partendo dalle parole seme. 
	- lo score di una parola è definito dalla probabilità che la random walk la visiti
4.  Si calcola lo score finale
	- score positivo = porzione di cammini che arriva da seme positivo
	- Si può calcolare anche una confidence con [[Ensemble Learning|bootstrap]]

Lo score poi si normalizza : 
$$\text{score}^+(w_i)=\cfrac{\text{rawscore}^+(w_i)}{\text{rawscore}^+(w_i)+\text{rawscore}^-(w_i)}$$



### Altre tecniche
- **Congiunzione sintattica** (Hatzivassiloglou & McKeown, 1997):
    
    - Se due aggettivi sono collegati da “and”, è probabile che abbiano la stessa polarità.
    - Se collegati da “but”, probabilmente hanno polarità opposta.

- **Negazioni morfologiche**:
    
    - adequate ↔ _in_adequate, thoughtful ↔ thoughtless

- **WordNet**:
    
    - Sinonimi ereditano la polarità
    - Antonomi invertono la polarità

-  **SentiWordNet** (Baccianella et al., 2010):
	
	- Etichetta **synset** (non parole) con punteggi **Pos / Neg / Obj**
	- Usa gloss di WordNet + classificatore supervisionato + random walk per rifinire