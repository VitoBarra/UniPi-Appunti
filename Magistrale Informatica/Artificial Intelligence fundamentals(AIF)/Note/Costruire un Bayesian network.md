---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Costruire un Bayesian network
---
Il metodo di costruzione di una [[Bayesian network|rete bayesiana]] segue questi passaggi:
1. **Selezione delle variabili**: determinare le variabili necessarie per modellare il dominio.
2. **Ordinamento topologico**: numerare i nodi un qualsiasi ordine funziona ma facnedo in modo che le **cause** siano prima **degli effetti** si ottiene un [[Bayesian network|Bayesian network]] piu compatto, questo crerera un [[Ordinamento topologico|ordinamento topologico]]
3. **Selezione dei genitori**: per ogni nodo $X_i$, scegliere un insieme minimo di genitori dai nodi precedenti $X_1, \dots, X_{i-1}$ in modo che:$$
   P(X_i | X_1, \dots, X_{i-1}) = P(X_i | Parents(X_i))
   $$
4. **Creazione dei collegamenti**: inserire frecce dai genitori selezionati a $X_i$.
5. **Definizione delle CPT**: specificare le probabilità condizionate $P(X_i \mid Parents(X_i))$ per ogni nodo.

Questa costruzione garantisce che la rete sia aciclica e non contenga probabilità ridondanti, evitando possibili incoerenze con gli [[Definizione di Probabilita|assiomi della probabilità]]