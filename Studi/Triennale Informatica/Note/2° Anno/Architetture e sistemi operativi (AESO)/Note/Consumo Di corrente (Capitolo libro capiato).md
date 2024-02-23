---
Subject: "[[Architetture e sistemi operativi (AESO)]]"
tags:
  - AESO
topic:
---

# Consumo Di corrente (Capitolo libro capito)
---

Il consumo di potenza è la quantità di energia utilizzata per unità di tempo ed
è un aspetto di grande importanza per i sistemi digitali. La vita di una batteria
nei sistemi portatili come i cellulari e i personal computer è limitata dal consumo di potenza. Ma il consumo di potenza è importante anche per i sistemi
collegati alla presa di corrente, perché l’elettricità costa e perché i sistemi si
surriscaldano se viene utilizzata troppa energia.
I sistemi digitali consumano sia potenza dinamica sia statica. La potenza
dinamica è quella utilizzata per caricare le capacità dei condensatori quando i
segnali cambiano tra 0 e 1, mentre la potenza statica è quella consumata anche
quando i segnali non cambiano e il sistema è inattivo.
Le porte logiche e i fili che le collegano hanno una capacità. L’energia prelevata dall’alimentatore e utilizzata per caricare la capacità C fino alla tensione

VDD è CVDD2. Se la tensione sul condensatore cambia a una frequenza f (si
intende f volte al secondo) questo si carica f/2 volte e si scarica f/2 volte al
secondo. Quando il condensatore viene scaricato non viene prelevata energia
dall’alimentatore, quindi il consumo di potenza dinamica è pari a

$$
P_{dinamica}= \frac{1}{2} CV_{DD}^2f
$$

I dispositivi elettronici usano una certa quantità di corrente anche quando
sono inattivi. Quando i transistori sono spenti, disperdono comunque una
piccola quantità di corrente. Alcuni circuiti, come le porte pseudo-nMOS di
cui si è parlato nel paragrafo 1.7.8, hanno un percorso da VDD a GND attraverso il quale la corrente fluisce continuamente. La corrente statica totale, IDD,
viene anche chiamata corrente di dispersione o “corrente di alimentazione
quiescente” tra VDD e GND. Il consumo di potenza statica è proporzionale a
questa corrente statica

$$
P_{statica}= I_{DD}V_{DD}
$$
