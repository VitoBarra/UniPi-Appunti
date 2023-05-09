---
type: nota
course: Calcolo Numerico
topic: 
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Tecniche per l analisi degli errori
---
## Analisi per l [[Tipi di Errore nel calcolo numerico|errore inerente]]
La regolarità della funzione $f(x)$ ha implicazione sulla proprita del problema matematico da essa specificato. la continuità della funzione implica la _buona positura del problema_

dalla relazione 
$$\epsilon_{in}= \frac{f(\tilde x)-f(x)}{f(x)} = \frac{f(\tilde x)-f(x)}{\tilde x-x}\frac{x}{f(x)}\frac{\tilde x -x }{x}$$
si ricava che la [[Funzioni differenziabili|differenziabilita]] di $f(x)$ è essenziale per il controllo dell errore inerente. il particolare se assumiamo che $f(x) \in C^2$  ovvero è derivabile due volte con continuità in $(a,b)$ allora vale lo [[Sviluppi di Taylor#Sviluppo con Resto di Lagrange|Sviluppo di Taylor con lagrange]]
$$f(\tilde x)= f(x)+f’(x)(\tilde x-x)+\frac{f’’(\xi)}{2}(\tilde x-x)^2, \ \ |\xi -x| \leq|\tilde x-x|$$
da cui si ottiene 
$$\epsilon_{in}= \frac{f(\tilde x)-f(x)}{f(x)} \dot =\frac{f’(x)}{f(x)}x\epsilon_x = c_x\epsilon_x, \ \ \ c_x=\frac{f’(x)}{f(x)}x$$
la quantità $c_x=c_x(f)=\frac{f’(x)}{f(x)}x$ detto _coefficiente di amplificazione_  fornisce una misura del condizionamento del problema piu generalmente se $f:\Omega \rightarrow \mathbb{R}$ è definita su un insieme aperto di $\mathbb{R}^n$, differenziabile due volte su $\Omega$ ed il segmento di estremi $\tilde x$ e $x$ è contenuto in $\Omega$ allora vale 
$$\epsilon_{in}=\frac{f(\tilde x)-f(x)}{f(x)} \dot = \frac{1}{f(x)}\sum^n_{i=1}c_x(f)\epsilon_x$$
dove 
$$c_{x_i}(f)=\frac{1}{f(x)}\frac{\partial f}{\partial x_i}(x)x_i, \ \ \ \ 1 \leq i \leq  n$$
detti coefficiente di aplificazione della funzione $f$ rispetto alla $x_i$

## Analisi per l errore Algoritmico

l analisi del [[Tipi di Errore nel calcolo numerico|errore algoritmico ]]può basarsi sui risultato ottenuto per l errore inerente. si distinguono 
1. tecniche di analisi in avanti
2. tecniche di analisi all indientro

##### Analisi in avanti
per l _analisi in avanti_ dell errore algoritmico si consideri un step intermedio dell algoritmo di calcolo over abbiamo da calcolare il valore dell operazione aritmetica $$\psi(\tilde x, \tilde y) \dot = \psi (x,y)(1+c_X(\psi)\epsilon+c_y(\psi)\delta+\gamma), \ |\gamma| \leq u$$
dove $c_x(\psi),c_y(\psi)$ sono rispettivamente i coefficienti di amplificazione e l errore locale del operazione $\psi$. il calcolo dell errore algoritmico totale puo essere reso intuitivo con l aiuto di un grado rappresentato nella figura seguente ove i nodi corrispondo ai risultato intermedi generati dall algoritmo. Se il risultato intermedio $x$ corrisponde al nodo $i$ mentre il risultato intermedio $y$ corrisponde al nodo $j$ allora l operazione $\psi(x,y)=z$ genera un arco dal nodo $i$ al nodo corrispondente a $z$ con perso $c_x(\psi)$.  nel nodo corrispondere a $z$ risulta dato dalla somma dell errore locaple piu i pesi di arco multiplicati per l oerrre algoritmico totale accumulato sul nodo di origine dell arco considerato in accordo della relazione prcedente


![[757FE8DA-6518-4975-A5E8-109F418BAEE2.jpeg]]
l analisi in avanti deo errore algoritmi conduce generalmente a valutazioni eccessivamente pessimistiche assumendo l amplificazione masssima ad ogni passo intermedio del algoritmo


##### Analisi al indietro 



>[!WARNING] da rivedere sul libro
>dispense gimignano 
