---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: 
tags:
  - IA
---

# Validazione e test
---
 la __validazione e  test__ sono un concetti generali del campo del [[Concetti generali del Machine Learning|Machine learning]] infatti 
 - la __validazione__ serve a selezionare dei buoni __iperparametri__ che permettono di selezionare un modello adatto al problema che si sta cercando di risolvere 
 - il __test__ serve ad assicuraci che il modello sia in grado di generalizzare e avere delle risposte corrette anche su dati che non ha mai visto 

Gli __iperparametri__ sono dei parametri che definiscano il modello, questi sono distinti dai parametri che vengono imparati dal modello stesso infatti gli __iperparametri__ sono impostati da un utente, questi cambiano l'espressività del modello alcuni esempi di iperparametri son il numero di unita in un layer di una [[Reti Neurali (NN)|rete neurale]]

il __processo di validazione__ serve a fare __mode selection__ ovvero una buona scelta degli __iperparametri__ in base alle performance osservate dallo un modello con la stessa architettura ma con __iperparametri__ diversi. Si migliora iterativamente la scelta degli __iperparametri__ che si usano in base alla valutazione di diversi modelli con l'obiettivo di trovare quello più adatto al problema. Per scegliere gli __iperparametri__  iniziali non esiste nessuna teoria o regola e quindi si procede in base al esperienza
Nella pratica si scegli un sotto insieme dei dati chiamato __Validation set__ che non viene usato per il learning ma solo per calcolare alcune statistiche che ci permettono di capire quali __iperparametri__ sono generano un modello più adatto. 
Per scegliere il modello piu adatto si cerca di minimizzare la __loss__ calcolata sul __validation set__ ma bisogna stare attenti siccome ad ogni iterazione avviene l'__information leackage__ ovvero si sta dando al modello informazioni sui dati su cui si sta facendo la validazione, facendo troppe iterazioni il modello potrebbe andare in [[Overfitting e Underfitting|overfitting]] sul __validation set__

il __processo di testing__ serve a capire quanto il modello scelto tramite la __validazione__ sia in grado di generalizzare su nuovi dati mai visti. Questo vieni fatto mostrando al modello una parte del data set detto __test set__.
il __test set__ deve essere scelto prima del allenamento e non deve contenere dati usati nel __training set__ o nel __validation set__. Questo processo costruisce una [[Statistica campionaria|statistica]] indicativa per valutare il modello    


le varie tecniche di __validazione e test__ definiscono come dividere ed utilizzare i dati, alcune teche sono le seguenti 

