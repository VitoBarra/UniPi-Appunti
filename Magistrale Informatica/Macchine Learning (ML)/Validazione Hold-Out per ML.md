---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Validazione Hold-Out per ML
---
la  __hold out__ è una [[Validazione e test di una modello di ML|tecnica di validazione e test]]  questa [[Partizione di un insieme|partiziona]] i dati del dataset in 3 insiemi disgiunti 
![[971E52B2-01B1-4377-BA0F-A4822D3AA24D.jpeg]] 
- _Training_ : su cui si allena il modello e si fa il fitting
- _validation_: insieme di validazione su cui si fa la selezione del _miglior_ modello 
	- questi due insieme vengono chiamati insieme di _sviluppo_ o _design_ 
-  _Test_: insieme su cui si testa il modello scelto e si stima l _errore di generalizzazione_


>[!warning]
>in generale bisogna stare attenti ad non utilizzare i dati di test per fare validazione. se utilizzo i dati di test per apportare delle correzione al modello sto ”bruciando quei dati” e non sono più utilizzabili per la _valutazione del modello_ 


![[C0073B23-3100-45F2-9CBC-3F391035DCAE.jpeg]]

![[2AEBFC72-9030-4874-8811-DBB189E29AED.jpeg]]

