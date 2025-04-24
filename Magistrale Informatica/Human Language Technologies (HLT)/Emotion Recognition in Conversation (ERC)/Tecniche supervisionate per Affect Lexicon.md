---
Course: "[[Human Language Technology (HLT)]]"
Course 2: 
tags:
  - HLT
Area: "[[Emotion Recognition in Conversation (ERC)]]"
topic: "[[Lexicons for Sentiment, Affect, and Connotation]]"
SubTopic: "[[Affect Lexicon]]"
---
# Tecniche supervisionate per affect lexicon
---
Per costruire [[Affect Lexicon]] si possono usare tecniche supervisionate prendendo dei dati testuali etichettati naturalmente, come per esempio recensioni di film, libri, ristoranti e prodotti in cui ogni testo è etichettato da un punteggio (generalmente 1-5 o 1-10).

## Metodo di frequenza di parola per classe
1. Si contano le occorrenze di una parola $w$ nei testi di ciascuna classe $c$ (es. 1 stella, 2 stelle…)
2. Si stima la probabilità $P(w∣c)$ che rappresenta la frequenza di $w$ nei testi con classe $c$.

Per normalizzare le probabilità delle parole su tutte le classi si usa il *Potts score* che restituisce un vettore di distribuzione che mostra quanto un parola è associata a ciascuna classe.

Il Potts score si può visualizzare con il Potts diagram



## Log Odds con Dirichlet Prior

Ha come obiettivo identificare parole fortemente associate a una classe rispetto ad un'altra. Come problema è che può sovrastimare l'importanza di parole rare e di parole troppo frequenti.

Come soluzione si addotta l'aggiunta di un corpus di background 