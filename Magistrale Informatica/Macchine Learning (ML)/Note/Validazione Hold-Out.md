---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Validazione Hold-Out
---
la  __hold out__ è una [[Validation e Test di una modello di ML|tecnica di validazione e test]]  questa [[Partizione di un insieme|partiziona]] i dati del dataset in 3 insiemi disgiunti 
![[971E52B2-01B1-4377-BA0F-A4822D3AA24D.jpeg]] 
- _Training_ : su cui si allena il modello e si fa il fitting
- _validation_: insieme di validazione su cui si fa la selezione del _miglior_ modello 
	- questi due insieme vengono chiamati insieme di _sviluppo_ o _design_ 
-  _Test_: insieme su cui si testa il modello scelto e si stima l _errore di generalizzazione_


>[!warning]
>in generale bisogna stare attenti ad non utilizzare i dati di test per fare validazione. se utilizzo i dati di test per apportare delle correzione al modello sto ”bruciando quei dati” e non sono più utilizzabili per la _valutazione del modello_ 


![[C0073B23-3100-45F2-9CBC-3F391035DCAE.jpeg]]


- Separare __TR__ (training), __VL__ (validation) e __TS__ (test) sets  
- Cercare il __miglior__ $h_{w,\lambda}()$ variando gli iperparametri del modello $\lambda$ [ad esempio, l'ordine del polinomio, il lambda per la regressione ridge]:  
- Per ciascun valore diverso di $\lambda$ (grid search)  
  - Cercare il __miglior__ $h_{w,\lambda}()$ che minimizza l'errore/la loss empirica (adattandosi al __TR__ set) trovando i migliori parametri $w$,  
    dove __miglior__ = errore minimo sul __TR__ set [ad esempio, $\arg\min_w Loss(w)$ in $L_2$]  
  - Selezionare il __miglior miglior__ $h_{w,\lambda}()$: dove __miglior__ = errore minimo sul __VL__ set  
  - (__Opzionale__: Ora è anche possibile adattare $h_{w,\lambda}(x)$ su __TR+VL__ con il modello con il miglior $\lambda$)  
- Valutare il modello finale $h_{w,\lambda}(x)$ sul __TS__  

---

Questa è un ciclo doppio: cercare il __miglior__ valore può essere un __for__ su una griglia di valori nel ciclo esterno:  
per ogni valore di $\lambda$, si allena un modello $h_{w,\lambda}$ (nel ciclo interno, ad esempio il ciclo di discesa del gradiente)  
e si calcolano i risultati (accuratezza) sul __VL__ set.  
Poi si prende il __miglior__ valore di $\lambda$, cioè il modello con __VL__ errore minimo o __VL__ accuratezza massima, ecc.







# Hold out
For the basic setting, we can simply divide the dataset $D$ in three sets: Training $TR$, Validation $VL$ and test $TS$, and use $TR$ for training, $VL$ for model selection and $TS$ for model assessment.

We can call te union of $TR$ and $VL$ *Development/design set*.
![[hold out sets.png]]
![[Hold out.png]]
Se venisse utilizzato il test set per modificare il modello da scegliere questo potrebbe non generalizzare su nuovi dati e con le stesse performance ottenute sul test.


Se i dati fossero insufficienti per essere organizzati in 3 macro insiemi può aiutare la ***k-fold cross validation***
