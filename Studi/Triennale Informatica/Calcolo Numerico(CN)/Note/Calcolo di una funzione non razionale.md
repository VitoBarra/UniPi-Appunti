---
Course: "[[Calcolo Numerico(CN)]]"
topic: nota
tags:
  - CN
---

# Calcolo di una funzione non razionale
---
Si presenta l esigenza di calcolare funzioni non espresse dalle 4 operazioni base, come ad esempio gli esponenziali e i logaritmi. si usa quindi una funzione razionabile che sappiamo  [[Errori nel calcolo di una funzione razionale|calcolare]] che approssima la funzione he vogliamo effettivamente calcolare.  cosi facendo introduciamo oltre gli errori del calcolo un  un’ulteriore errore chiamato _errore analitico_


### Definizione errore analitico
Data una funzione non razionale $f(x)$ e una funzione razionale che approssima $f(x),$ $h(x)$ l errore analitico è definito come 

$$ \epsilon_{an}= \frac{h(x)-f(x)}{f(x)}$$


Si può dimostrare che vale la relazione 
$$\epsilon_{tot} = \epsilon_{an}+\epsilon_{in}+\epsilon_{alg}$$


