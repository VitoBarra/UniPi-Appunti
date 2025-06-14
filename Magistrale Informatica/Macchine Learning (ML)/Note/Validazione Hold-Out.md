---
Course: "[[Machine Learning (ML)]]"
tags:
  - IIA
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

