---
Course: "[[Human Language Technology (HLT)]]"
Course 2: 
tags:
  - HLT
Area: 
topic: 
SubTopic:
---
# Sentence segmentation - NLP
---

La **segmentazione in frasi** è un altro passaggio fondamentale nel pre-processing del testo.

#### **Indizi per la segmentazione**

I segnali più utili per suddividere un testo in frasi sono:

- **Punteggiatura**, come: il punto (`.`), il punto interrogativo (`?`) ed il punto esclamativo (`!`)

I punti interrogativi e i punti esclamativi sono generalmente **indicatori chiari e non ambigui** della fine di una frase.  
Al contrario, il **punto (`.`)** può essere **ambiguo**, perché può comparire alla fine di una frase ma anche all’interno di abbreviazioni (es. “Dott.”, “ecc.”, “Sig.”).


### **Segmentazione combinata di frasi e parole**

Proprio per via di questa ambiguità, la **tokenizzazione in frasi** e la **tokenizzazione in parole** possono essere affrontate **insieme**, in modo congiunto.

Una tecnica comune consiste nell’utilizzare un **classificatore binario**, cioè un algoritmo che decide se un punto rappresenta **la fine di una frase**, oppure se è semplicemente **parte di una parola**, come un’abbreviazione.

Per migliorare la precisione di questo processo, è utile avere un dizionario di abbreviazioni comuni, che aiuti il sistema a distinguere tra i due casi.

