---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
Area:
topic:
SubTopic:
---
# Famiglia esponenziale di distribuzioni
---
Una **famiglia esponenziale di distribuzioni** è una classe di [[Distribuzione di probabilita|distribuzioni di probabilità]] parametriche che possono essere scritte in una forma comune. Nei [[Generalized Linear Model (GLM)|Generalized Linear Models]], la risposta $Y_i$ è tipicamente assunta provenire da una distribuzione appartenente a questa famiglia.

L'idea importante non è memorizzare la forma più generale, ma capire perché questa classe è utile:
- include molte distribuzioni comuni;
- permette di descrivere distribuzioni diverse dentro uno stesso schema;
- fornisce proprietà matematiche comode per stima e test;
- rende naturale la definizione di **parametro naturale** e **link canonico**.

Esempi di distribuzioni nella famiglia esponenziale:
- [[Variabili Aleatorie Notevoli - Gaussiana|Gaussiana]]
- [[Variabili Aleatorie Notevoli - Bernulli|Bernoulli]]
- [[Variabili Aleatorie Notevoli - Binomiale|Binomiale]]
- [[Variabili Aleatorie Notevoli - Poisson|Poisson]]
- [[Variabili Aleatorie Notevoli - Gamma|Gamma]]

In un GLM si sceglie una distribuzione della famiglia esponenziale in base al tipo di risposta:
- continua: spesso Gaussiana;
- binaria: Bernoulli o Binomiale;
- conteggio: Poisson o, se c'è overdispersion, Negative Binomial;
- positiva continua: Gamma.

Quando una distribuzione viene scritta nella forma della famiglia esponenziale, emerge un parametro detto **parametro naturale**. La funzione che collega la media della risposta al predittore lineare usando questo parametro è detta **link canonico**.

Esempi:
- per la Bernoulli/Binomiale, il link canonico è il **logit**: $$\log\frac{p}{1-p}$$
- per la Poisson, il link canonico è il **log**: $$\log(\mu)$$

Il link canonico non è sempre l'unica scelta possibile, ma spesso è matematicamente naturale e comodo per l'inferenza.

Vedi anche: [[Generalized Linear Model (GLM)]], [[Maximum Liklehood learning]], [[Regressione lineare - Interpretazione probabilistica]], [[Variabili Aleatorie Notevoli - Poisson]].
