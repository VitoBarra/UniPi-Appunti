---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# CRN - Modelli stocastici
---
L’evoluzione dinamica delle [[Chemical Reaction Network (CRN)|CRN]] può essere descritta tramite **modelli stocastici** quando le reazioni sono trattate come eventi discreti e casuali nel tempo, in contrasto con i modelli deterministici basati su [[Ordinary Differential Equation (ODE)|ODE]].

assumendo che  
Motivazione fisica:
- le molecole si muovono in un mezzo fluido **ben mescolato**;
- il moto è dovuto a urti elastici con il solvente;
- l’incontro tra reagenti è un evento casuale;
- l’evento di reazione è intrinsecamente probabilistico.

Sia $X(t)$ il vettore dei numeri interi di molecole. L’evoluzione del sistema non è più una traiettoria deterministica, ma una distribuzione di probabilità $$P(X,t)$$che rappresenta la probabilità che il sistema si trovi nello stato $X$ al tempo $t$.

Questo formalismo richiede algoritmi specifici di simulazione, come [[CRN - Algoritmo di simulazione stocastico di Gillespie|SSA]], che generano traiettorie casuali coerenti con la [[CRN - Modello mass-action|cinetica di mass-action]] interpretata in senso [[Definizione di Probabilita|probabilistico]].

L’uso di modelli stocastici è giustificato dal fatto che, a livello microscopico, l’occorrenza di una reazione non è prevedibile con esattezza. Anche per una reazione semplice $$A \xrightarrow{k} B + C$$ non è possibile determinare l’istante preciso in cui una specifica molecola di $A$ reagirà. Infatti i modelli deterministici:
- descrivono concentrazioni **continue** in tempo continuo, mentre le molecole sono in numero discreto e le reazioni sono eventi discreti;
- assumono la validità del [[Teorema debole dei grandi numeri|regime dei grandi numeri]], che permette di ignorare la randomicità media ma non cattura fluttuazioni rilevanti in piccoli volumi o a basse copie molecolari.

Invece nel modello stocastico:
- lo stato è un vettore di conteggi molecolari interi;
- le reazioni sono eventi discreti;
- il tempo tra due reazioni successive è una variabile casuale;
- la dinamica è un processo stocastico a tempo continuo.

Ha senso usarli quando:
- il numero di molecole è basso;
- il rumore intrinseco influenza il comportamento globale;
- si osservano fenomeni di bistabilità o switching indotti da fluttuazioni;
- le oscillazioni sono sostenute o modulate dal rumore.