---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# edgeR - DE per RNAseq
---
**edgeR** è un framework statistico per [[Analisi RNA-seq|RNA-seq]] basato su conteggi discreti che integra normalizzazione tra campioni, modellizzazione con [[Variabili aleatorie Notevoli - Negative Binomial|Negative Binomial]] [[Generalized Linear Model (GLM)|GLM]] e test di espressione differenziale. Opera sulla matrice **geni × campioni** di conteggi grezzi e utilizza la normalizzazione **TMM (Trimmed Mean of M-values)** per correggere differenze globali di library size e composizione tra campioni, mantenendo i conteggi nel dominio originale per l’inferenza.

Per ciascun gene $g$ e campione $i$ i conteggi sono modellati con [[Variabili aleatorie Notevoli - Negative Binomial|NB]]$$Y_{gi}\sim\text{NB}(\mu_{gi},\theta_g)$$con varianza$$\mathrm{Var}(Y_{gi})=\mu_{gi}+\phi_g\mu_{gi}^2$$dove $\phi_g$ è la dispersione specifica del gene. La parametrizzazione descrive l’overdispersion rispetto al modello [[Variabili Aleatorie Notevoli - Poisson|Poisson]].

La media è collegata al disegno sperimentale tramite un NB GLM con link [[Funzione logaritmica|log]]:
$$\log \mu_{gi} = \log s_i + x_i^T \beta_g$$
dove $s_i$ rappresenta i fattori di normalizzazione TMM e $x_i$ le covariate sperimentali.

La stima della dispersione $\theta_g$ è centrale. edgeR procede tipicamente in tre fasi:
- stima di una **common dispersion** globale
- stima di una **trended dispersion** dipendente dall’abbondanza
- stima di dispersioni gene-specifiche (“tagwise”)

Le dispersioni tagwise sono sottoposte a **empirical Bayes shrinkage** verso il valore comune o trended, stabilizzando le stime in presenza di pochi replicati e riducendo la varianza delle statistiche di test.

Una volta stimata la dispersione, il test di espressione differenziale è applicato ai coefficienti $\beta_g$ del GLM. edgeR utilizza:
- **Exact test NB** (analogo al test esatto di Fisher per due gruppi semplici)
- **Likelihood Ratio Test (LRT)** nei GLM generali
- **Quasi-likelihood F-test (QLF)**, più robusto in presenza di variabilità residua

Il [[Test Statistici|test]] valuta tipicamente:$$H_0: \beta_{g,\text{condizione}} = 0$$La dispersione stimata entra nel calcolo della varianza del coefficiente, ma non è l’oggetto del test.

Interpretazione:
- $\theta_g$ → livello di variabilità biologica
- $\beta_g$ → effetto della condizione sperimentale
- il test verifica se l’effetto è grande rispetto alla variabilità stimata

Per analisi esplorative edgeR utilizza trasformazioni leggere come **logCPM con prior** per stabilizzare i conteggi bassi, oppure metodi **MDS** basati sui principali log-fold-change tra campioni. La gestione della dipendenza media–varianza è incorporata direttamente nel modello NB, senza necessità di trasformazioni esplicite tipo VST o rlog prima del test.

L’output comprende log-fold change stimati, statistiche di test e [[Test Statistici - p-value|p-value]] per ciascun gene. Poiché vengono effettuati migliaia di test simultanei, i p-value sono corretti per test multipli controllando il [[FDR|False Discovery Rate]] tramite la procedura di Benjamini–Hochberg.
