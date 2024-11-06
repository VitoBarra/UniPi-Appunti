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


### Hold out 
la tecnica di __validazione e test__ __hold out__ questa [[Partizione di un insieme|partiziona]] i dati del dataset in 3 insiemi disgiunti 
![[971E52B2-01B1-4377-BA0F-A4822D3AA24D.jpeg]] 
- _Training_ : su cui si allena il modello e si fa il fitting
- _validation_: insieme di validazione su cui si fa la selezione del _miglior_ modello 
	- questi due insieme vengono chiamati insieme di _sviluppo_ o _design_ 
-  _Test_: insieme su cui si testa il modello scelto e si stima l _errore di generalizzazione_


>[!warning]
>in generale bisogna stare attenti ad non utilizzare i dati di test per fare validazione. se utilizzo i dati di test per apportare delle correzione al modello sto ”bruciando quei dati” e non sono più utilizzabili per la _valutazione del modello_ 


![[C0073B23-3100-45F2-9CBC-3F391035DCAE.jpeg]]

![[2AEBFC72-9030-4874-8811-DBB189E29AED.jpeg]]



### K-fold Cross validation
il __k-fold cross validation__ è una tecnica di validazione che si utilizza quando i dati a propria disposizione sono pochi validare con il metodo __Hold-out__ porta valori di validazione molto diversi molto a seconda di come i valori iniziali sono randomicamente assegnati:
- Si [[Partizione di un insieme|partizionano]] i dati in  $k$ set $D_i$ con $i = 1,\dots,k$ 
- Si allenano $k$  modelli uno per ogni insieme  $D_i$  si allena sulla parte dei dati disignata al allenamento e si fa la _validazione_ sui dati di validazione dello stesso insieme $D_i$
- si fa la media di tutte le statistiche a cui siamo interessati ottenute dagli insiemi  $D_i$
 queste statistiche [[Idd - Media Campionaria|medie]] sono molto piu affidabili del singolo insieme $D_i$ e si possono quindi usare per fare la validazione 
![[8EA4B086-1939-4FF7-A4DE-FFBE28A0529C.jpeg]]
Alla fine del processo di __validazione__ fatta con questa tecnica, per creare il modello finale su cui eseguire i test e si utilizzerà per fare inferenza si mantengono gli __iperparamentri__ trovati e si allena un nuovo modello utilizzano tutti a disposizione ad eccezione di quelli disignati al test 
una  problematica è scegliere il numero di fold infatti vanno bilanciate due cose
- Troppe e l allenamento diventa molto costoso (molte iterazioni)  
- Poche e la validazione diventa meno precisa


## Esempio di algoritmo con K-fold CV
![[CC356D75-E00C-4B4E-842E-132BFBD6C357.jpeg]]

il comportamento tipico del fase di validazione è il seguente
![[2E9BDD5C-D52A-4778-86E5-E3C2ABCC9F24.jpeg]]


### iterastive K-fold cross validation
