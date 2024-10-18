---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Macchine Learning (ML)]]"
tags:
  - IA
Area: "[[Machine Learning]]"
topic: 
SubTopic:
---
# Apprendimento supervisionato
---
l __apprendimento supervisionato__ è una categoria di algoritmi di [[Macchine Learning (ML)|apprendimento]] che utilizza dei dati _Etichettati_ 

_dati_: dati di training detti _training example_ formalizzati  come $<input,output> = (x,d)$, sono delle associazioni per una funzione sconosciuta $f$ detta _target function_. con i training example se ne definiscono alcuni punti 
- le associazioni sono dati da un _teacher_ e sono prese per vere e utilizzate per stimare le funzione corretta
_Trova_: un approssimazione di $f$ detta _ipotesi_ che verrà poi utilizzata per predirei il valore dei nuovi dati non visti 


ci sono due tipi problemi risolvibili con questo tipo di apprendimento 
- _Clssificazione_: la funzione $f(x)$ restituisce la classe assunta corretta per $x$
	- $f(x)\in \mathbb{F}^k\times \mathbb{N}$. $f$ è quindi una funzione discreta, e ogni numero intero è una diversa classe 
- _Regressione_: la funzione $f(x)$ restituisce output reali approssimando la funzione reale _target_
- $f(x)$ $\in \mathbb{F}\times\mathbb{R}^k$
	 
![[991D6D4A-9F89-4A4E-BE65-509CB69C0C3C.jpeg]]

>[!example]- Alcuni esempi
>![[84563ACF-1E29-4871-81B7-628DCD565D04.jpeg]]
