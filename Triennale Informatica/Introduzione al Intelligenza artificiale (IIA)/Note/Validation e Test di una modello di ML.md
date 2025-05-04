---
Course: "[[Machine Learning (ML)]]"
Course 2: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Validation e Test di una modello di ML
---
 la __validazione e  test__ sono un concetti generali del campo del [[Concetti generali del Machine Learning|Machine learning]] questi sono definiti come 
 - la __validazione__ serve a selezionare dei buoni __iperparametri__ che permettono fare  __selezionare un modello__ (*__Model selection__*) adatto al problema che si sta cercando di risolvere 
 - il __test__ serve ad assicuraci che il modello sia in grado di generalizzare e avere delle risposte corrette anche su dati che non ha mai visto, viene usato per ottenere una stima delle performance su dati mai visti (__Model Assesment__)


Gli __iperparametri__ sono dei parametri che definiscano architettura e caratteristeche di un [[Modelli di Machine Learning|modello di macchine learning]]. Bisogna stare  attendi a non confonderli con i parametri dei [[Modelli Parametrici|modelli parametrici]] che vengono imparati dal modello stesso infatti gli __iperparametri__ sono impostati da un utente.

il __processo di validazione__ serve a fare __mode selection__ ovvero una buona scelta degli __iperparametri__ in base alle performance osservate variando gli __iperparametri__. Spesso varie configurazioni di iperparametri vengono scelti in modo sistematico impiegando delle [[Tecniche per la ricerca degli iperparametri|strategie di ricerca]]. 
Per scegliere i range di ricerca degli __iperparametri__ non esiste nessuna teoria o regola e quindi si procede in base al esperienza.

Nella pratica si scegli un sotto insieme dei dati chiamato __Validation set__ che non viene usato per il learning ma solo per calcolare alcune statistiche che ci permettono di capire quali __iperparametri__ sono generano un modello più adatto. 
Per scegliere il modello piu adatto si cerca di minimizzare la __loss__ calcolata sul __validation set__ ma bisogna stare attenti siccome ad ogni iterazione avviene l'__information leackage__ ovvero si sta dando al modello informazioni sui dati su cui si sta facendo la validazione, facendo troppe iterazioni il modello potrebbe andare in [[UniPi-Appunti/Triennale Informatica/Introduzione al Intelligenza artificiale (IIA)/Note/Overfitting e Underfitting|overfitting]] sul __validation set__

il __processo di testing__ serve a stimare quanto il modello scelto tramite la __validazione__ sia in grado di generalizzare su nuovi dati mai visti. Questo vieni fatto mostrando al modello una parte del data set detto __test set__.
il __test set__ deve essere scelto prima del allenamento e non deve contenere dati usati nel __training set__ o nel __validation set__. Questo processo costruisce una [[Statistica campionaria|statistica]] indicativa per valutare il modello    

le varie tecniche di __validazione e test__ definiscono come dividere ed utilizzare i dati, alcune teche sono le seguenti 
- [[Validazione Hold-Out]]
- [[K-Fold Cross Validation]]
- [[Double cross validation (Nested k-fold cross validation)]]





 
