---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Machine Learning (ML)]]"
tags:
  - IA
Area: "[[Concetti generali del Machine Learning]]"
topic: 
SubTopic: 
---
# Algoritmi di apprendimento supervisionato
---
l'__apprendimento supervisionato__ è una categoria di algoritmi di [[Algoritmi di Machine Learning|apprendimento]] caratterizzato dal utilizzo dei dati _etichettati_.

Questa classe di algoritmi ha lo scopo di approssimare una certa funzione $f$ __sconosciuta__ con un una funzione $h \in \mathcal{H}$ detta __ipotesi__, dove $\mathcal{H}$ è lo [[Algoritmi di Machine Learning|spazio delle ipotesi]] specifica per l'algoritmo in uso. Per fare ciò questi algoritmi usando dei sample detti __esempi__ della funzione $f$ che sono definiti come coppie $(x_i,y_i)$ dove $x \in \mathbb{F}^n$ e $y_i = f(x_i)+noise$, ovvero una punto conosciuto della funzione $f$ con l aggiunta di qualche errore.
 
il training, ovvero la ricerca della $h \in \mathcal{H}$,  avviene tramite l'utilizzo di un __training set__ definito formalmente come segue:
__Sia__  $f(x)$ una __[[Funzioni|funzione]] sconosciuta__  
__allora__ $TS$  il __Training set__ composto da $\ell$ dati è definito come insieme di coppie di punti $$TS=\{(x_1,y_1),(x_2,y_2),\dots,(x_\ell ,y_\ell)\}$$ dove $y_i = f(x_i)+noise$



Gli __algoritmi di learning__ che fanno parte della categoria del __learning supervisionato__ formulano il problema del learning come problema di minimizzazione di una certa funzione detta di $Loss$ che misura l'errore di predizione della ipotesi selezionata dal algoritmo.     

Formalmente, la funzione da minimizzare è definita come
__sia__
- $l(y,x)$ una funzione che misura errore di predizione di una __singolo__ esempio
- $TR$  il training set con $\ell$ il numero di esempi
- $h$ l ipotesi scelta 
__Allora__ la funzione di __$Loss$__ è definita come $$Loss_{TR}(h)=\sum_i^\ell l(y_i,h(x_i))$$il valore $Loss_{TR}(h)$ quantifica quanto l'algoritmo erra nella predizione dell'output e minimizzare questa  permette di selezionare un'ipotesi $h$ tra tutte le ipotesi possibili in $\mathcal{H}$. che dia delle buone performance, misurate, anche le performance sono misurate con una certa funzione che dipende dal problema che si sta affrontando.

Per fare si che l' algoritmi selezioni un ipotesi con una buona performance c'è bisogno di scegliere una funzione di $Loss$  in modo che la sua minimizzazione correli con una buona performance.



I __problemi affrontabili__ con l'__apprendimento supervisionato__ si dividono in due classi:  
1. __Classificazione__: dove l'input deve essere mappato dal ipotesi in una o più delle $c \in \mathbb{N}$ categorie disgiunte; quindi si ha che $h \in \mathbb{F}^k\times \mathbb{N}$. Se $c=2$ allora la classificazione viene detta binaria altrimenti ennaria.  
2. __Regressione__: dove l'input viene mappato in uno o più numeri reali e quindi si ha che $h \in \mathbb{F}^n\times \mathbb{R}^m$
	 
![[991D6D4A-9F89-4A4E-BE65-509CB69C0C3C.jpeg]]





