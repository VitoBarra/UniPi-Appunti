---
Course: "[[Human Language Technology (HLT)]]"
Course 2: 
tags:
  - HLT
Area: 
topic: "[[Text Classification]]"
SubTopic:
---
# Sentimental analysis
---
La **sentimental analysis** è un task di [[Text Classification]] con il quale si vuole assegnare ad una parola, frase o testo un etichetta relativa all'emozione corrispondente. 
Per far ciò bisogna estrarre dalle espressioni le emozioni correlate.

La versione più semplice di sentimental analysis è una classificazione binaria in cui le classi corrispondono all'emozione positiva o negativa.

Esistono altre [[Tassonomie delle emozioni|tassonomie per l'identificazione delle emozioni]] che si basano su gli stati affettivi che comprendono:
- Emozioni
- Stati d'animo 
- Relazione tra gli speakers
- Attitude
- Tratti della personalità

Sono stati creati degli [[Affect Lexicon]] con cui si possono classificare le emozioni. Oltre a quelli semplici [[Affect Lexicon - Lessici binari|Binari]], questi possono essere di tue tipi: [[Affect Lexicon - Lessici categoriali|categoriali]], in cui le classi sono ben definite e corrispondo alle emozioni, o [[Affect Lexicon - Lessici dimensionali (VAD)|dimensionali (VAD)]], in cui vengono analizzate 3 dimensioni (Valenza, Attivazione e Dominanza) per ogni emozione.

# Sentiment Analysis Classification
Il [[Naive Bayes Classifier]] per essere applicato alla *Sentimental analysis* può essere modificato per ottenerne una versione chiamata : ***Binary Multimodal Naive Bayes***, che usa lo stesso algoritmo con la sola eccezione che per ogni documento si rimuovono i tutte le parole duplicate prima di concatenare i documenti della solita classe e poi si rimuovono anche le parole duplicate nel test set.

Un altro problema nella classificazione per la sentiment analysis sono le negazioni. Per sistemarle si fa text normalization e la parola negata vine modificata in una nuova parola con la negazione davanti. (esempio: didn't like -> not_like)

In altri scenari, in cui non si hanno abbastanza data etichettati si usano i [[Affect Lexicon]], liste di termini pre-annotati. Un modo per utilizzarli è aggiungere una feature dove appare il termine.