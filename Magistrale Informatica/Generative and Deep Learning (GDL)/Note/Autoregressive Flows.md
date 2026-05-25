---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area: Modelli Generativi
topic: Flow-based models
SubTopic:
---
# Autoregressive Flows
---
Gli **Autoregressive Flows** sono una famiglia di trasformazioni invertibili nei [[Normalizing Flows]] in cui ogni coordinata viene trasformata usando le coordinate precedenti come contesto.

In forma generale, una trasformazione autoregressiva puo essere scritta come:

$$y_i = T_i(x_i; x_1,\dots,x_{i-1})$$

Questa struttura rende il jacobiano triangolare, perché ogni uscita $y_i$ non dipende dalle coordinate successive:

$$
\frac{\partial y}{\partial x}
=
\begin{bmatrix}
\frac{\partial y_1}{\partial x_1} & 0 & \dots & 0 \\
\ast & \frac{\partial y_2}{\partial x_2} & \dots & 0 \\
\vdots & \vdots & \ddots & \vdots \\
\ast & \ast & \dots & \frac{\partial y_d}{\partial x_d}
\end{bmatrix}
$$

Quindi il determinante si ottiene facilmente come prodotto dei termini diagonali.

## Differenza rispetto ai coupling flow
Rispetto ai [[Coupling Flow|coupling flow]], qui non si spezza il vettore in due blocchi fissi. In ciascun layer tutte le coordinate possono essere trasformate, ma la dipendenza e organizzata in ordine autoregressivo.

Questo produce un trade-off diverso:
- nei coupling flow molte coordinate restano invariate in ogni layer
- negli autoregressive flow tutte le coordinate possono essere aggiornate
- il prezzo da pagare e che sampling e inversione non hanno lo stesso costo

## MAF e IAF
Nel **Masked Autoregressive Flow** (**MAF**), la trasformazione e progettata in modo da rendere veloce la valutazione della densita. Questo lo rende molto comodo nel training come modello di likelihood, ma il sampling e piu lento, perché le coordinate vanno generate una alla volta.

Nell'**Inverse Autoregressive Flow** (**IAF**) succede il contrario: il sampling e veloce, mentre la valutazione della densita nella direzione opposta e meno comoda. Per questo IAF compare spesso in contesti come i [[Variational Autoencoder (VAE)|VAE]].
![[IMG - Autoregressive flows.png]]
![[IMG - Masked Autoregressive Flow.png]]

## Interpretazione
Gli **Autoregressive Flows** mostrano che la trattabilita del jacobiano non richiede necessariamente uno split in due blocchi come in [[Coupling Flow - NICE]], [[Coupling Flow - RealNVP]] o [[Coupling Flow - GLOW]]. Basta anche una dipendenza autoregressiva che mantenga la struttura triangolare della trasformazione.
