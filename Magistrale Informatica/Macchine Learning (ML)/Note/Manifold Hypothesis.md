---
Course: "[[Machine Learning (ML)]]"
Corse 1: "[[Generative and Deep Learning (GDL)]]"
tags:
  - ML
  - GDL
Area: Concetti generali
topic: Manifold Hypothesis
SubTopic:
---
# Manifold Hypothesis
---
La **Manifold Hypothesis** è l'ipotesi secondo cui dati ad alta dimensionalità, come immagini, audio o testo, spesso si trovano vicino a una [[Manifolds (Varieta)|varietà]] non lineare di dimensione molto più bassa.

In altre parole, anche se un dato viene rappresentato con molte coordinate, le variazioni realmente significative sono spesso molto meno numerose. Per esempio, un'immagine può avere migliaia di pixel, ma i fattori che spiegano la sua struttura possono essere identità dell'oggetto, posa, illuminazione, stile, rotazione o scala.

## Intuizione

Lo spazio dei dati grezzi è molto grande, ma non tutte le configurazioni possibili sono realistiche.

Nel caso delle immagini:
- un punto nello spazio dei pixel può rappresentare una immagine naturale;
- un piccolo movimento lungo la manifold può cambiare un fattore significativo, come posa o illuminazione;
- un movimento fuori dalla manifold può produrre rumore o una immagine non valida.

Quindi i dati reali occupano solo una piccola regione strutturata dello spazio totale.

![[IMG - manifold.png]]

## Rappresentazioni latenti

Molti modelli di [[Machine Learning (ML)|machine learning]] e [[Deep Learning]] cercano di imparare una rappresentazione che catturi questa struttura.

Una buona rappresentazione dovrebbe:
- preservare le direzioni significative lungo la manifold;
- comprimere o ignorare variazioni irrilevanti;
- rendere vicini esempi semanticamente simili;
- separare esempi semanticamente diversi.

Negli [[Autoencoders (AE)|autoencoders]], questa idea appare nello spazio latente: l'encoder cerca di mappare il dato in una rappresentazione compatta che parametrizzi le direzioni importanti della manifold.

![[IMG - autoencoders come learning di manifold.png]]

## Collegamento con i modelli generativi

La Manifold Hypothesis è centrale anche nei [[Modelli Generativi|modelli generativi]]. Un modello generativo efficace non deve produrre punti qualsiasi nello spazio dei dati, ma campioni che stiano vicino alla manifold dei dati reali.

Esempi:
- gli [[Autoencoders (AE)]] imparano una rappresentazione latente utile alla ricostruzione;
- i [[Denoising Autoencoders (DAE)]] imparano a riportare punti rumorosi verso regioni più probabili;
- i [[Variational Autoencoder (VAE)|Variational Autoencoders]] regolarizzano lo spazio latente per renderlo campionabile;
- le [[Generative Adversarial Networks (GAN)|GAN]] imparano una trasformazione da rumore latente a campioni realistici.

## Conseguenze

La Manifold Hypothesis aiuta a spiegare perché il deep learning può funzionare su dati ad altissima dimensionalità: anche se lo spazio grezzo è enorme, i dati reali hanno una struttura più bassa e più regolare.

Allo stesso tempo, se un modello non impara bene questa struttura, può avere problemi con:
- rumore;
- outlier;
- adversarial examples;
- scarsa generalizzazione fuori dalla distribuzione di training.
