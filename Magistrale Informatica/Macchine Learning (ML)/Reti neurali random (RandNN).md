---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Reti neurali random (RandNN)
---
Allo scopo di efficentare il training tramite [[BackPropagation|BackPropagation]] delle reti neurali sono stati provati approccio come le __Random Weight [[Reti Neurali (NN)|Neural Networks]] (RWNNs)__ si mantiene l' architetture [[Reti neurali Feed-Forward (FF)|MLP]]/[[Reti Neurali Ricorrenti (RNN)|RNN]] ma si avita il training inizializzando casualmente una parte della rete e allenando solo l ultimo layer
- **Random Vector Functional Link (RVFL)**
- **Extreme Learning Machine (ELM)**
- **Reti a Funzione Radiale (RBF) con centri random**
![[Pasted image 20250207221310.png]]


L architettura generale degli approccio randomizati prevedono due parti un primo insieme di __hidden layer__ che vengono inizializzatati casualmente e e non allenati e un secondo detto __read out__ che invece viene alleanto
![[Pasted image 20250207214659.png]]
La parte __non trainata__ proietta l' input in uno spazio a più altra dimensionalità ovvero implementa una [[Linear Basis Expansion (LBE)|Large Basis Expansion (LBE)]] __NON__ lineare  e dal __[[Teorema di copertura (Cover Theorem)|Teorema di Copertura]]__ sappiamo che questo rende il problema probabilmente [[Linearmente Separabili|linearmente separabile]].
il __read out__ impara a leggere le [[Rappresentazione simbolica e distribuita dei concetti|feature]] progliettare dagli hidden layer per poterle usare per il task specifico per cui è stato allenato.

## Implementazione di RWNNs
si può realizzare una semplice implementazione di una rete con __pesi randomizati__ usando un [[Reti neurali Feed-Forward (FF)|architettura feed-forward]] 
- Strato nascosto __non allenato__ con pesi casuali $W$
- Lo strato di __output__ con pesi $W_{out}$ viene addestrato con [[Modelli lineari con LMS|metodi lineari]]:
![[Pasted image 20250207221357.png]]

Questo tipo di approccio è __estremamente efficiente__, Adatto a Big Data e dispositivi a basse risorse (es. IoT, [[Cloud-Edge Continuum|edge computing]]).



#### Applicazione in altri contesti
alcuni altri __approccio randomizzati__: 
- __[[Deep Learning|Deep]] Randomized NN__: stack di moduli RVFL/ELM per il deep learning
- [[Reti Neurali Ricorrenti (RNN)|Reti ricorrenti]] randomizzate ([[RandRNN - Reservoir Computing|Reservoir Computing]] / [[Reservoir Computing - Echo State Machine|ESN]]), particolarmente utili per il trattamento di serie temporali.
- __[[Reti Neurali Convoluzionali (CNN)|CNN]] randomizzate__




