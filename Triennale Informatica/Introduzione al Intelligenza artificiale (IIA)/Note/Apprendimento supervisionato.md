---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Machine Learning (ML)]]"
tags:
  - IA
Area: "[[Concetti generali del Machine Learning]]"
topic: 
SubTopic: 
---
# Apprendimento supervisionato
---
l __apprendimento supervisionato__ è una categoria di algoritmi di [[Algoritmi di Macchine Learning|apprendimento]] caratterizzato dal utilizzo dei dati _etichettati_. 

Questa classe di algoritmi ha lo scopo di approssimare una certa funzione $f$ __sconosciuta__ con un una funzione $h \in \mathcal{H}$ detta __ipotesi__, dove $\mathcal{H}$ è lo [[Algoritmi di Macchine Learning|spazio delle ipotesi]] specifica per l'algoritmo in uso. Per fare ciò questi algoritmi usando dei sample detti __esempi__ della funzione $f$ che sono definiti come coppie $(x_i,y_i)$ dove $y_i = f(x_i)+noise$, ovvero una punto conosciuto della funzione $f$ con l aggiunta di qualche errore.

il training, ovvero la ricerca della $h \in \mathcal{H}$,  avviene tramite l'utilizzo di un __training set__ definito formalmente come segue:
__Sia__  $f(x)$ una __[[Funzioni|funziona]] sconosciuta__  
__allora__ $TS$  il __Training set__ composto da $\ell$ dati è definito come insieme di coppie di punti $$TS=\{(x_1,y_1),(x_2,y_2),\dots,(x_\ell ,y_\ell)\}$$ dove $y_i = f(x_i)+noise$






Formalmente, una metrica è una funzione chiamata funzione di loss $l$ e si definisce il valore di loss come 
 $$Loss=\sum_i^nl(f(x_i),h(x_i))$$ 
Il valore di $\text{Loss}$ quantifica quanto il modello erra nella predizione dell'output.  
Si deve scegliere una funzione di loss adatta al problema che si vuole affrontare in modo che un basso valore di $\text{Loss}$ correli con un miglior risultato.  
Infatti, un algoritmo di _apprendimento supervisionato_ minimizza la loss scelta con l'obiettivo di selezionare un'ipotesi $h$ tra tutte le ipotesi possibili in $\mathcal{H}$.  

I problemi affrontabili con l'_apprendimento supervisionato_ si dividono in due classi:  
1. __Classificazione__: dove l'input deve essere mappato in una o più delle $n \in \mathbb{N}$ categorie disgiunte; se le categorie sono due la classificazione viene detta binaria altrimenti ennaria.  
2. __Regressione__: dove l'input viene mappato in uno o più numeri continui.  

Per queste due classi di problemi si conoscono delle funzioni di loss adatte alla loro risoluzione. Ad esempio, per la _regressione_, è comunemente usata la __Mean Squared Error__ (__MSE__):  
$$\frac{\sum^n_{i=1}(\hat{y}_i - y_i)^2}{n},$$  
mentre, per la classificazione ennaria, si usa la _sparse categorical crossentropy_ o la _categorical crossentropy_ a seconda dell'encoding delle label.


I __dati di training__, detti _training example_ formalizzati come $T$, sono delle associazioni per una funzione sconosciuta detta _target function_. Con i training example se ne definiscono alcuni punti:  
- Le associazioni sono dati da un _teacher_ e sono prese per vere e utilizzate per stimare la funzione corretta.  
- _Trova_: un'approssimazione di $f$ detta _ipotesi_ che verrà poi utilizzata per predire il valore dei nuovi dati non visti.  

Ci sono due tipi di problemi risolvibili con questo tipo di apprendimento:  
- __Classificazione__: la funzione $f(x)$ restituisce la classe corretta assunta per $x$:  
  - $f(x) \in \mathbb{F}^k \times \mathbb{N}$. $f$ è quindi una funzione discreta, e ogni numero intero è una diversa classe.  
- __Regressione__: la funzione $f(x)$ restituisce output reali approssimando la funzione reale _target_:  
  - $f(x) \in \mathbb{F} \times \mathbb{R}^k$.  

	 
![[991D6D4A-9F89-4A4E-BE65-509CB69C0C3C.jpeg]]

>[!example]- Alcuni esempi
>![[84563ACF-1E29-4871-81B7-628DCD565D04.jpeg]]




