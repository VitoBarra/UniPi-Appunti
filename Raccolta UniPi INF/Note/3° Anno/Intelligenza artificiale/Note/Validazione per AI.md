---
type: nota
course: Intelligenza Artificiale
topic: 
tags: IA
---

Prev: [[Introduzione Intelligenza Artificiale (IIA)]]

# Validazione e problemi teorici per AI
---
 in questa sezione si affrontano concetti generali che si applicano a tutto il campo del [[Machine Learning (ML)|Machine learning]]



### Obbiettivi della validazione
- _Selezione del modello_: si stima la _performance_ (capacita di generalizare) di molti modelli e la si ottimizza per scegliere il modello che generalizza di piu
	- Restituisce un modello   
- _Valutazione del modello_: una volta scelto il modello si stima la sua accuracy su nuovi dati di _test_. ovvero come performa 
	- restituisce una stima 
	 

### Hold out 
è una tecnica per fare raggiungere questi obiettivi ovvero 
si dono i dati che si hanno in 3 insiemi disgiunti 
![[971E52B2-01B1-4377-BA0F-A4822D3AA24D.jpeg]]
i dati vengono partizionati in 
- _Training_ : su cui si allena il modello e si fa il fitting
- _validation_: insieme di validazione su cui si fa la selezione del _miglior_ modello 
	- questi due insieme vengono chiamati insieme di _sviluppo_ o _design_ 
-  _Test_: insieme su cui si testa il modello scelto e si stima l _errore di generalizazione_


>[!warning]
>in generale bisogna stare attenti ad non utilizzare i dati di test per fare validazione. se utilizzo i dati di test per apportare delle correzione al modello sto ”bruciando quei dati” e non sono più utilizzabili per la _valutazione del modelllo_ 


![[C0073B23-3100-45F2-9CBC-3F391035DCAE.jpeg]]

_regola per una corretta validazione_: mantenne una chiara separazione tra obiettivi e dati che si usano per raggiungere quegli obiettivi 



### Meta-algoritmo per l apprendimento
![[2AEBFC72-9030-4874-8811-DBB189E29AED.jpeg]]

>[!Warning]- esercizio
>![[24B1A699-51EC-4934-9B82-78383FBEDC6A.jpeg]]
>Si sta scegliendo il modello quindi si scegli sul VT


### Esempio 
20-30 esempi, 1000 variabilidi input random, •random target0/1 •Scelgo1modellocon una sola variabile/feature cheindovina'per caso'al 99% suldataset e poi suqualsiasisplit successivoin training,validatione test set. Perfect result (a model with accuracy 99% )? What is wrong? 99% non è una buonastimadell’erroredi test (quellacorrettae' 50%) 1. Errorestimatosutraining o validation per model selectionNON è utile per stimadel rischio! Datidi TR o VL non vannousatiper scopidi  test 2. Usaretuttoil data set per feature/model selection ledela correttezzadell stima(risultati biased–«Feature Selectionbias»). –Test set è statousatoimplicitamenteall’inizio*.–Test deveessereseparatoprima, prima di qualsiasimodel selection o design del modello(inclusoselezionedi features) Un test set esterno fornisce invece la stima corretta del 50% (random coinresult!). E’ la correttezza della stima che è in giudizio, non la possibilità di risolvere il task! Delicato confrontandometodidiversie usandotecnichedi K-fold cross-validation chein se non garantisconocorrettezadellaproceduradi validazione
![[793434FB-3D4F-4349-BE60-7216E4C05165.jpeg]]


### K-fold Cross validation
-  Si [[Partizione|partizionano]] i dati in  $k$ set $D_i$ con $i = 1,\dots,k$ 
- Si da l aprendimento su Tutti gli insimi $D$ tranne che sun un certo $D_i$ e si fa la _validazione_ su $D_i$
- si fa la media di tutti i testi su $D_i$
- si possono poi usare tutti i dati per il training del modello scelto precedentemente 
![[8EA4B086-1939-4FF7-A4DE-FFBE28A0529C.jpeg]]
un problema è scegliere il numero di fold. troppe e l allenamento diventa molto costoso (molte iterazioni) troppo perche e allenamento poco precisno


## Esempio di algoritmo con K-fold CV
![[CC356D75-E00C-4B4E-842E-132BFBD6C357.jpeg]]

### Comportamento tipico 
![[2E9BDD5C-D52A-4778-86E5-E3C2ABCC9F24.jpeg]]



