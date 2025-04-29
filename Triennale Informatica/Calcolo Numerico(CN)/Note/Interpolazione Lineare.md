---
Course: "[[Calcolo Numerico(CN)]]"
tags:
  - CN
topic:
---
# Interpolazione Lineare
---
L'**interpolazione lineare** è un metodo che stima il valore di una funzione tra due punti noti utilizzando una [[Rette|retta]] che li _congiunge_. 
Questo approccio fornisce una **stima lineare** del valore della funzione in punti intermedi non noti.

**_siano_**
- $(x_i, y_i)$ e $(x_{i+1}, y_{i+1})$ due punti noti 
- $x$ un punto in cui si vuole stimare il valore con $x_i < x < x_{i+1}$
**_allora_** il valore trovato per l'**interpolazione lineare** è data da:$$f(x)=y =\frac{x_{i+1}-x}{x_{i+1}-x_{i}}\cdot y_i + \frac{{x - x_i}}{{x_{i+1} - x_i}}\cdot y_{i+1}$$dove:
- $\cfrac{x_{i+1}-x}{x_{i+1}-x_{i}} \in (0,1)$  è la [[Definizione di distanza|distanza]] normalizzata di $x$ dal punto $x_{i+1}$
- $\cfrac{{x - x_i}}{{x_{i+1} - x_i}}$  è la [[Definizione di distanza|distanza]] normalizzata di $x$ dal punto $x_i$  
e quindi la formula puo essere interpretata come la somma pesta per la distanza dei valori $y$ nelle coordinate $x_i$ e $x_{i+i}$.  


generalizzando si possono interpolare tutti i valori tra $x_i$ e $x_{i+1}$ definendo un parametro $t \in [0,1]$ si puo riscrivere l'**interpolazione lineare** come $$f(x) =t\cdot y_1 + (1-t)\cdot y_{i+1}$$


Un esempio di **interpolazione lineare** che si puo fare tra _valori reali_ è il seguente 
![[IMG - interpolazione lineare.png]]
dove le linee spezzate sono ciò che riusciamo ad ottenere con l **_interpolazione lineare_**



Le limitazioni principali di questo approccio sono:
1. **Assunzioni Lineari:** assume che la relazione tra i punti noti sia approssimativamente lineare, il che potrebbe non essere vero in tutte le situazioni.
2. **Errori di Approssimazione:**  approssima con una retta, potrebbe introdurre errori significativi in presenza di variazioni non lineari.

