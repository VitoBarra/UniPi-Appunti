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

Lo spazio dei dati grezzi è molto grande, ma non tutte le configurazioni possibili sono realistiche.
Nel caso delle immagini:
- un punto nello spazio dei pixel può rappresentare una immagine naturale;
- un piccolo movimento lungo la manifold può cambiare un fattore significativo, come posa o illuminazione;
- un movimento fuori dalla manifold può produrre rumore o una immagine non valida.
Quindi i dati reali occupano solo una piccola regione strutturata dello spazio totale.
![[IMG - data manifold.png]]
