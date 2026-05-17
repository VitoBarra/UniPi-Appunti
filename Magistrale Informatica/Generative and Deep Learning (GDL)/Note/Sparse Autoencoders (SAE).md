---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area: Modelli Generativi
topic: Autoencoders
SubTopic:
---

# Sparse Autoencoders (SAE)
---
Gli **Sparse Autoencoders** (**SAE**) sono una variante degli [[Autoencoders (AE)|autoencoders]] in cui si aggiunge una penalità sulla rappresentazione latente $z$.

L'obiettivo è ottenere un codice **sparso**: anche se lo spazio latente può avere molte dimensioni, per ogni esempio solo poche unità dovrebbero essere attive. In questo modo il modello è costretto a rappresentare il dato usando pochi fattori latenti rilevanti.

Uno **sparse autoencoder** mantiene l'obiettivo di ricostruzione, ma aggiunge una regolarizzazione sul codice latente:
$$
J_{\text{SAE}}(\theta,\phi)
=
\sum_{x \in \mathcal{D}}
\left[
\mathcal{L}(x, \tilde{x})
+ \lambda \Omega(z(x))
\right]
$$

dove:
- $\Omega(z(x))$ misura quanto il codice latente è non sparso;
- $\lambda$ controlla il peso della penalità;
- $z(x) = f_{\theta}(x)$ è la rappresentazione prodotta dall'encoder.

tipicamente è usare una [[Norme Matriciali e Norme Vettoriali|norma 1]] $L_1$ che promuove proprio la sparsita:
$$
\Omega(z(x)) = \lVert z(x) \rVert_1
$$

quindi:
$$
J_{\text{SAE}}(\theta,\phi)
=
\sum_{x \in \mathcal{D}}
\left[
\mathcal{L}(x, g_{\phi}(f_{\theta}(x)))
+ \lambda \lVert f_{\theta}(x) \rVert_1
\right]
$$

La penalità $L_1$ spinge molte componenti di $z$ verso zero. Il risultato è che, per ogni input, il modello usa solo un sottoinsieme piccolo di neuroni latenti.

Questo è diverso dal ridurre semplicemente la dimensionalità del codice. Uno SAE può anche avere $K > D$, cioè uno spazio latente più grande dell'input, ma la sparsità impedisce al modello di usare tutte le unità contemporaneamente per copiare l'input.

La sparsità agisce come un bottleneck regolarizzato. Il modello non è vincolato solo dalla dimensione dello spazio latente, ma anche dal numero effettivo di unità attive.

Questo aiuta a:
- evitare una funzione identità banale;
- ottenere rappresentazioni più interpretabili;
- separare fattori latenti diversi;
- ridurre ridondanza nel codice;
- migliorare la robustezza della rappresentazione.
In termini intuitivi, il modello deve scegliere pochi elementi del codice per spiegare ogni input.

## Interpretazione probabilistica
La funzione obiettivo degli **SAE** ha anche una lettura probabilistica. 
La reconstruction loss si può interpretare come un termine di [[Formula di Bayes|likelihood]]: $\log P_{\phi}(x \mid z)$mentre la penalità sul codice latente si può interpretare come un prior su $z$:  $\log P(z)$
Quindi la regolarizzazione assomiglia a una stima [[Maximum a posteriori (MAP) learning|MAP]]:$$\log P(z, x)=\log P_{\phi}(x \mid z)+\log P(z)$$Con una penalità $L_1$, il prior corrispondente è di tipo **Laplace**:$$P(z) \propto \exp(-\lambda \lVert z \rVert_1)$$Per questo la penalità $L_1$ favorisce codici sparsi: valori diversi da zero sono costosi, quindi il modello tende ad attivare solo le componenti latenti necessarie.

Questa non è però una lettura [[Formula di Bayes|bayesiana]] completa: in un autoencoder il codice $z$ non è campionato da un vero posterior, ma viene prodotto deterministicamente dall'encoder:$$z = f_{\theta}(x)$$La lettura probabilistica serve quindi a capire il ruolo della regolarizzazione: reconstruction term come likelihood, penalità come prior.
