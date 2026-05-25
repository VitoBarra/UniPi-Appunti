---
Course: "[[Machine Learning (ML)]]"
tags:
  - IIA
  - ML
Area:
topic:
SubTopic:
---
# Structural Domain Learning (SDL)
Lo **Structural Domain Learning (SDL)** e il campo del [[Machine Learning (ML)|machine learning]] che studia modelli capaci di ricevere in input un **dato strutturato**, cioe un oggetto in cui non conta solo il contenuto dei singoli elementi ma anche la relazione tra essi. Alberi, grafi, strutture simboliche composte e reti relazionali rientrano tutte in questo quadro, e il problema centrale non e semplicemente classificare vettori, ma apprendere trasformazioni e rappresentazioni che rispettino la struttura del dominio.

## Motivazioni
Lo **Structural Domain Learning (SDL)** nasce dal fatto che molti dati reali non sono naturalmente flat. L'approccio opposto consiste nel forzare la struttura in un [[Vettori|vettore]] per usare modelli che lavorano su input regolari, come [[Reti neurali Feed-Forward (FF)|reti feed-forward]] o [[Convolutional Neural Network (CNN)|convolutional neural network]], oppure trasformarla in una sequenza per usare una [[Recurrent Neural Network (RNN)|rete neurale ricorrente]]. Questa riduzione e spesso possibile, ma tende a perdere o distorcere informazione relazionale, perche impone un ordine o una geometria che il dato originario non possiede.

Lo **Structural Domain Learning (SDL)** diventa quindi necessario quando le relazioni sono parte del dato stesso. Nei grafi, per esempio, il significato di un nodo dipende dal suo **contesto strutturale**; in un albero, la semantica di un nodo dipende dalla sua posizione gerarchica; in una struttura simbolica, il valore informativo sta spesso nella composizione piu che nei singoli simboli. ![[IMG - Esempio uso grafi.png]]
Lo **Structural Domain Learning (SDL)** considera strutture in cui esistono entita e relazioni esplicite tra entita. I grafi sono la formalizzazione piu generale e piu usata, perche permettono di rappresentare nodi, archi, etichette e attributi in modo flessibile. Questa scelta e naturale in molti contesti applicativi:
- **visione artificiale**, dove scene e oggetti possono essere descritti come reti di parti o relazioni spaziali
- **trasporti**, dove reti stradali e flussi di traffico hanno struttura esplicita
- **social network**, dove utenti e interazioni formano grafi relazionali
- **chimica** e **bioinformatica**, dove molecole, proteine e reti biologiche sono strutture naturalmente grafiche
- **linguistica** e **knowledge representation**, dove parsing e grafi semantici rendono esplicite dipendenze e relazioni

## Obiettivo dell'apprendimento strutturato
Lo **Structural Domain Learning (SDL)** vuole mappare dati strutturati in rappresentazioni continue utilizzabili da modelli predittivi. In questa lettura il problema non e diverso, in astratto, da quello del [[Rappresentazione simbolica e distribuita dei concetti|learning di rappresentazione]]: anche qui si cerca una funzione che trasformi l'oggetto osservato in uno **spazio latente** utile per classificazione, regressione o generazione. La differenza e che la funzione di rappresentazione non deve perdere le dipendenze strutturali rilevanti.

Nel caso dei grafi, ogni nodo puo essere descritto da feature locali e ogni arco da etichette o attributi; tuttavia il dato non coincide con l'insieme delle feature, perche la topologia del grafo e parte dell'informazione. Lo **Structural Domain Learning (SDL)** tratta quindi il dato come una coppia formata da contenuto e struttura, e richiede modelli che integrino entrambe le componenti in modo coerente. In questo contesto l'apprendimento gerarchico di rappresentazioni permette di diffondere in modo efficiente l'informazione lungo la struttura del grafo: la rappresentazione di un nodo dipende dal suo contesto, inizialmente locale e poi progressivamente piu ampio all'aumentare della profondita del modello.
![[IMG - propagazione delle informazioni su grafi.png]]

## Task generali
Lo **Structural Domain Learning (SDL)** organizza i problemi in base alla natura dell'output desiderato. Se il dataset e un singolo grande grafo, i task tipici sono predizioni locali o relazionali; se il dataset e una collezione di grafi indipendenti, il task riguarda l'intera struttura. 

Nel caso di un singolo grafo si incontrano soprattutto:
- **Node prediction**, in cui si predice una classe o un valore continuo per un nodo
- **Link prediction**, in cui si predice l'esistenza o il tipo di una connessione tra due nodi
- **Community detection**, in cui si identificano gruppi di nodi fortemente connessi o semanticamente simili
![[IMG - Task in domoni strutturati su singolo grafi.png]]

Nel caso di un dataset di grafi si hanno invece:
- **Graph classification**, in cui si assegna l'intera struttura a una classe
- **Graph regression**, in cui si associa al grafo un valore o un vettore di valori
![[IMG - Task su domini strutturati task sul intero grafo.png]]

La **Trasduzione di grafi**  si guarda alla forma della trasformazione strutturale richiesta. I casi principali sono:
- **structure-to-structure**, in cui input  sono vettori o strutture e output sono entrambi strutture e il modello deve preservare una corrispondenza tra componenti
![[IMG - task di trasduzione su grafi.png]]

## Vincoli strutturali
Lo **Structural Domain Learning (SDL)** impone vincoli che non compaiono nei dati regolari. In un grafo non esiste in generale un ordinamento canonico dei nodi, quindi il modello non deve dipendere dal modo arbitrario in cui la struttura viene serializzata o indicizzata. Questo porta a richiedere proprieta di **permutation invariance** e **permutation equivariance**

Un secondo vincolo e la cardinalita variabile del vicinato: un nodo puo avere pochi o molti vicini, e l'operatore di aggregazione deve quindi lavorare su insiemi o multinsiemi non ordinati. Un terzo vincolo e la presenza di dipendenze a lungo raggio, che rende non banale propagare informazione in profondita senza degradare le rappresentazioni.

## Deep learning su grafi
Il **Deep Learning for Graph** costituisce oggi la realizzazione neurale piu importante dello SDL sui grafi. In questo quadro il nodo non viene rappresentato isolatamente, ma attraverso processi di propagazione locale dell'informazione, aggregazione permutation invariant e costruzione di embedding contestuali. Il ramo include modelli come
- [[Deep Graph Networks (DGN)]]
- [[Graph Convolutional Network (GCN)|Graph Convolutional Networks]],
- [[Graph Attention Network]], 
- [[Graph Echo State Network]],
- [[Deep Reservoirs for Graphs]] 
- [[Graph Transformer]].
Lo **Structural Domain Learning (SDL)** non coincide pero solo con il deep learning su grafi: il campo e piu generale e riguarda ogni situazione in cui il dominio di apprendimento e strutturato. Nei grafi, tuttavia, si concentra oggi la parte piu sviluppata del quadro teorico e applicativo.
