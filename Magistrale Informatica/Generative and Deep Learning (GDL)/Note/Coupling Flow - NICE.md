---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area: Modelli Generativi
topic: Flow-based models
SubTopic:
---
# NICE
---
Le **NICE** (**Non-linear Independent Components Estimation**) sono una delle prime architetture importanti basate su [[Coupling Flow|coupling layer]] nei [[Normalizing Flows]].

L'idea e usare una sequenza di **additive coupling layers**, cioe trasformazioni del tipo:

$$y_A = x_A$$

$$y_B = x_B + m_{\theta}(x_A)$$

dove $m_{\theta}$ e spesso una [[Reti Neurali (NN)|rete neurale]]. La parte $x_A$ resta invariata, mentre $x_B$ viene traslata in modo dipendente dal contesto fornito da $x_A$.

## Perche e importante
La scelta additiva rende il modello molto elegante dal punto di vista matematico:
- l'inversa e immediata
- il jacobiano e triangolare
- il determinante del jacobiano vale sempre $1$

Quindi ogni coupling layer di NICE e semplice da invertire e da trattare analiticamente.

## Inversa e jacobiano
L'inversa si ottiene subito:

$$x_A = y_A$$

$$x_B = y_B - m_{\theta}(y_A)$$

Poiche il layer effettua solo una traslazione della parte aggiornata, il volume locale non cambia. Per questo NICE e un modello **volume preserving**.

## Architettura
Un singolo layer non e abbastanza espressivo, perché lascia invariata una parte delle variabili. Per questo NICE ottiene complessita mettendo in cascata molti coupling layer e alternando il ruolo delle coordinate.
![[IMG - modello NICE staked Coupling Flow.png]]

In questo modo:
- a un layer viene trasformata una parte del vettore;
- al layer successivo viene trasformata l'altra;
- dopo molti passaggi tutte le componenti vengono aggiornate indirettamente

## Vantaggio e limite
Il vantaggio principale di NICE e la massima semplicita strutturale. Il limite principale e che il layer non puo fare scaling locale, ma solo traslazioni condizionate. Questo riduce l'espressivita della trasformazione rispetto a modelli successivi.

Per questo architetture successive come [[Coupling Flow - RealNVP]] introducono il **coupling affine**, che generalizza NICE aggiungendo anche un termine di scala.

## Interpretazione
Le **NICE** mostrano bene la filosofia iniziale dei flow-based models: ottenere una trasformazione profonda invertibile senza perdere il controllo analitico sul jacobiano.
![[IMG - NICE resoults.png]]
