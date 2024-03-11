---
Subject: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Illuminazione nella Computer Grafica]]"
SubTopic:
---

# Illuminazione - Interazione della luce con la materia
---
la __[[Fisica - Onde|luce]]__ è un flusso di __energia radiante__ che si sposta da un posto (__source__) a un altro (__reciver__) seguendo una [[Retta|linea retta]]
La __luce__  puo provenire da due tipi di fonti
- __Fonte primaria__: un _Emettitore_ di luce ovvero qualcosa che genera luce
- __Fonte secondaria__: un _Riflettore_ di luce ovvero la luce viene riflessa da un oggetto.]
mentre la luce che arriva ad un __reciver__ è detta
- __Luce diretta__: se viene da una __fonte primaria__
- __Luce indiretta__: se viene da una __Fonte secondaria__

per la natura della [[Fisica - Onde|luce]] questa viene rappresentata come un raggio che viene deviato solo quando interagisce con la materia, utilizzando i raggio stiamo solo approssimato il comportamenti della luce ma è un idea sia semplice computazionalmente sia concettualmente quindi è molto utilizzata. Il campo che studia la luce cosi modellizzata è chiamato __ray optics__ o __geometric optics__.


### Ray optics
In generale abbiamo che la luce che arriva alla camera puo provenire da diversi effetti come la luce __riflessa__ e luca __rifratta__ 
la luce riflessa è composta da __luce diffusa__ $L_{diffuse}$ e __luce speculare__ $L_{pecular}$ e abbiamo quindi $$L_{\text{reflected}} = L_{\text{diffuse}}+L_{\text{specular}}$$e sommandola alla luce __refratta__ abbiamo che la luce totale è $$L_{\text{outgoing}}=L_{\text{reflected}}+L_{\text{refracted}} = L_{\text{diffuse}}+L_{\text{specular}}+L_{\text{refracted}}$$
![[Pasted image 20240227183956.png]]
#### Luce Riflessa 
##### Luce Diffusa
la __Luce diffusa__ è una componente della __luce riflessa__. La quantità di luce riflessa sarà uguale in ogni direzione e questa cosa è indipendente dalla direzione di incidenza della luce. 
una [[Superfice lambertiana|superfice lambertiana]] riflette  solo per __diffusione__  e quindi apparirà illuminato allo stesso modo in tutte le direzioni ovvero in modo __uniforme__
![[Pasted image 20240227184013.png]]
la quantità di luce totale diffusa da una _superfice_ dipende dal inclinazione della luce incidente rispetto alla superfice, siccome questo determina la quantità di luce che raggiunge il punto che  riflette. 
è massima quando la luce è [[Rette perpendicolari|perpendicolare]] alla superfice e [[Rette Parallele|parallela]] alla [[Normale di una superfice|norma]] e minima il contrario o se la luce viene da dietro l oggetto
![[Senzanome 1.png]]
![[coseno giu.png]]
abbiamo quindi che 
_sia_
- $L_{\text{incident}}$ la quantità di luce incidente
- $k_{\text{diffuse}}$ un coefficiente di diffusione che dipende da [[Illuminazione - Materiali|materiale]]
- $N$ la [[Normale di una superfice|normale della superfice]] 
- $\omega_i$ il [[Vettori|vettore]] di direzione della luce incidente
- $\theta$ l [[Angoli|angolo]] tra $\omega$ e $N$ 
_allora_ la luce diffusa sarà$$L_{\text{diffuse}}=L_{\text{incident}}k_{\text{diffuse}}\cos \theta$$per via della relazione tra [[Prodotto scalare euclideo (Dot product)|dot product]] e [[Tringonometria|coseno]] abbiamo che possiamo scrivere $$\cos \theta = N\cdot \omega$$e quindi la definizione standard per il __Riflesso Lambertiano__ sarà $$L_{\text{diffuse}}=L_{\text{incident}}k_{\text{diffuse}}(\boldsymbol{N}\cdot \omega_i)$$
l effetto del coseno puo essere visto come segue
##### Luce Speculare
la __Luce Speculare__ è una componente della __luce riflessa__
la quantità di __luce speculare__ dipende sia dal inclinazione della luce incidente che dalla direzione di riflessione.
infatti quando una superfice riflette specularmente avremo che l illuminazione cambierà a seconda della direzione in cui guardiamo la superfice.

Una superfice ideale per la riflessione speculare riflette la luce con lo stesso angolo rispetto di quella della luce incidente rispetto alla normale , i casi dove la riflessione non è ideale la riflessione avviene anche per diffusione   
![[Pasted image 20240227184035.png]]
per calcolare la direzione di riflessione $R$ si puo utilizzare la formula $$R=2\boldsymbol{N}(\boldsymbol{N}\cdot \boldsymbol{L})-\boldsymbol{L}$$e questa si ottiene geometricamente utilizzando le [[Triangoli|proprieta dei triangoli]]
![[Pasted image 20240227184047.png]]

#### Rifrazione
la __Rifrazione__ è un fenomeno che accade quando una parte della luce non viene riflessa e passa attraverso il materiale
- La quantità di luce rifratta dipende solo dalle proprietà del [[Illuminazione - Materiali|materiale]] che la luce colpisce
- il cambio di direzione della [[Fisica- Luce|luce]] dipende sia dal materiale in cui la luce viaggia che dal materiale che la luce colpisce
questo fenomeno è descritto dalla __legge di riflettanza__ (o legge di snell) che dice
_sia_
- $\eta_1, \eta_2$ gli [[Illuminazione - Materiali#Indice di refrazzione|indici refrattivi]] (velocita della luce al interno di un materiale) dei materiali 1 e 2
- $\theta_{1}$ l angolo tra [[Normale di una superfice|normale]] e luce incidente
- $\theta_2$ l angolo tra [[Normale di una superfice|normale]] e luce rifratta
_allora_ vale che $$\eta_1\sin \theta_1=\eta_2\sin \theta_2$$
la luce passera in accordo a questa legge![[Pasted image 20240227184107.png]]



