---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Modelli temporali probabilistici
---
i **[[Agenti Razionali|modelli temporali probablistici]]** sono un estensione [[Modelli Probabilistici|modelli probabilistici]] a **[[Definizione di Problemi-Ambienti|domini dinamici]]**, nei quali le variabili casuali evolvono nel tempo. Il mondo è rappresentato come una sequenza discreta di istanti $t = 0, 1, 2, \ldots$, detti “**time step**”, separati da un intervallo costante $\Delta$. A ogni intervallo temporale corrisponde un insieme di variabili di stato $X_t$, non direttamente osservabili, e un insieme di variabili di evidenza $E_t$, osservabili. Le osservazioni sono espresse come $E_t = e_t$, mentre la notazione $X_{a:b}$ denota il gruppo di variabili comprese tra $X_a$ e $X_b$ con **estremi inclusi**.

per modellare la dinamica temporale il modello usa due componenti fondamentali: 

**il modello di transizione**: descrive l’evoluzione dello stato nel tempo mediante la distribuzione condizionata $P(X_t \mid X_{0:t-1})$. Per garantire la trattabilità del modello si introduce l’[[Markov chains|assunzione di Markov]], che riduce la dipendenza dello stato corrente a un numero finito di stati precedenti. Nel caso del processo di Markov di primo ordine, la relazione si riduce a $P(X_t \mid X_{0:t-1}) = P(X_t \mid X_{t-1})$, affermando che il futuro è [[Indipendenza condizionata|condizionatamente indipendente]] dal passato dato lo stato attuale. Il modello assume inoltre **omogeneità temporale**: le leggi che regolano le transizioni rimangono costanti nel tempo, per cui la distribuzione $P(X_t \mid X_{t-1})$ è identica per ogni valore di $t$.

**il modello sensoriale** definisce la relazione tra **stati** e **osservazioni**, ogni stato dovrebbe essere da solo capace di determinare le sue osservazioni e quindi si fa l'[[Markov chains|assunzione di Markov per i sensori]], espressa come $P(E_t \mid X_{0:t}, E_{1:t-1}) = P(E_t \mid X_t)$ e $P(E_t \mid X_t)$ è il modello dei sensori.

e quindi il modello finale rappresenta la [[Full Joint Distribution (FJD)|distribuzione congiunta]] puo essere descritta con l’insieme delle **relazioni probabilistiche dinamiche** del modello come:$$
P(X_{0:t}, E_{1:t}) = P(X_0) \prod_{i=1}^{t} P(X_i \mid X_{i-1}) P(E_i \mid X_i),
$$dove $P(X_0)$ è il modello iniziale, $P(X_i \mid X_{i-1})$  il modello di transizione e $P(E_i \mid X_i)$ il modello sensoriale e questo permette di rappresentare un numbero unbounded ti **time step** $t$

L’ipotesi di primo ordine è valida quando le variabili di stato racchiudono tutte le informazioni necessarie a determinare la distribuzione del successivo stato. Tuttavia, l’accuratezza del modello può essere migliorata in due modi: 
- aumentando l’ordine del [[Markov chains|processo di markov]]:  includendo più stati passati nella dipendenza
- **ampliando l’insieme delle variabili di stato**: così da integrare nuovi fattori che descrivono la dinamica del sistema. 
 La seconda soluzione mantiene fisso l’ordine delle [[Markov chains|processo di markov]] ma richiede di prevedere anche l’evoluzione delle variabili aggiuntive, accrescendo la complessità predittiva. Un insieme di variabili di stato risulta autosufficiente quando conserva la proprietà di Markov, ovvero contiene l’informazione necessaria per la previsione del passo successivo. L’aggiunta di nuovi sensori che forniscono misure dirette di tali variabili contribuisce a ridurre l’incertezza e a migliorare la capacità inferenziale del modello temporale.
ds
