---
Course: Crittografia
topic: nota
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Funzioni One-Way
---
le _Funzioni one-way_ sono [[Funzioni|funzioni]] facili da calcolare ma difficili da invertire, ovvero richiede _[[Complessita|tempo polinomiale]]_ calcolare $y =f(x)$ ma _[[Complessita|tempo esponenziale]]_ calcolare $x=f^{-1}(y)$, le complessità sono calcolare nelle lunghezza della rappresentazione. 
In generale invertire la funzione impiega risolvere un problema della _classe_ $\mathbf{NP-hard}$


Di solito queste tipologia di funzioni fanno impiego della teoria del _[[Algebra modulare|algebra modulare]]_ per avere la proprieta _One-Way_

un esempio è la funzione 
$$f(x)=x^{2}\mod n$$
con $n$ non [[Numeri primi|primo]].

#### Predicati Hard-core
Un _[[Predicati|predicato]]_ $b(x)$  per una funzione _One-way_ $f(x)$
è detto _Hard-Core_ se è facile da calcolare conoscendo $x$ ma difficile da prevedere con [[Definizione di Probabilita|probabilita]] $>\cfrac{1}{2}$ (quindi con probabilità maggiore di tirare a caso) conoscendo solo il valore di $y=f(x)$

per la funzione $f(x)=x^{2}\mod n$ un predicato _hardcore_ è
$$b(x)= x \text{ è dispari}$$

#### Proprietà
_sia_ $f(x)$ funzione _one way_ e $b(x)$ un _predicato hardcore_ per $f(x)$ e indicando con $f^{(i)}(x)$ l _applicazione_ di $i$  volte di $f(x)$ avremo che la _sequenza binaria_
$$S = b(f^{(i)}(x)) \ \ \ b(f^{(i-1)}(x)) \ \ \ \cdots \ \ \ b(f^{(1)}(x))  \ \ \ b(x) $$
supera il _test di prossimo bit_ dei [[Generatori di numeri Pseudo Casuali#Test statistici per la casualità|test statistici per i generatori]]
questo discendo direttamente dalle proprietà delle funzioni _one way_ e dei predicati _hardcore_  

