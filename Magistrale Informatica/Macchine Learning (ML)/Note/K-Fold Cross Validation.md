---
Course: "[[Machine Learning (ML)]]"
tags:
  - IIA
  - ML
Area: 
topic: 
SubTopic:
---
# K-Fold Cross Validation
---
la __k-fold cross validation__ è una [[Validation e Test di una modello di ML|tecnica di validazione]] che si utilizza quando i dati a propria disposizione sono pochi validare con il metodo __Hold-out__ porta valori di validazione molto diversi molto a seconda di come i valori iniziali sono randomicamente assegnati:
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
- Suddividere i dati in __TR__ e __Test set__ (qui semplice hold-out o un K-fold CV)

- __Selezione del modello__ Usa:re la K-fold CV (__interna__) sul set __TR__, ottenendo nuovi set __TR__ e __VL__ in ogni suddivisione, per trovare i migliori iperparametri del modello 
  (es. ordine del polinomio, lambda della regressione ridge, ...): Come?
  Applicare una __grid-search__ con molteplici valori possibili degli iperparametri.

  - Ad esempio, una K-fold-CV per $\lambda = 0.1$, una K-fold-CV per $\lambda = 0.01$, ...  
    e poi scegliere il miglior $\lambda$ (confrontando gli errori medi calcolati sui set di validazione ottenuti 
    da tutti i fold di ogni K-fold CV, ... i risultati sono sulla diagonale nella slide precedente).

- Addestrare il modello finale sull'intero set __TR__

- __Valutazione del modello__ Valutare il modello sul __Test set__ esterno


il comportamento tipico del fase di validazione è il seguente
![[2E9BDD5C-D52A-4778-86E5-E3C2ABCC9F24.jpeg]]
