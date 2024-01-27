---
type: nota
course: Intelligenza Artificiale
topic: 
tags:
  - IA
Parent MOC: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
---

# Bias Induttivo
---
è un concetto di [[Machine Learning (ML)|ML]] fondamentale per l apprendere senza _BIas_ non puo esistere generalizzazione 

### proprietà
un apprendere senza bias è incapace di generalizzare, ovvero è solo in grado di classificare correttamente i dati dati di esempio
##### Dimostrazione
ogni instanza non osservata verra classificata come positiva da precisamente meta delle ipotesi mentre l altra meta la classificherà come negativa. 
$\forall h$ consistente con $x$ $\exists h‘$ identica a $h$ tranne che per $h(x) <>h’(x), h\in VS \rightarrow h’ \in VS$ sono indentiche sugli esempi di training D



### Bias Unduttivo
dati
- un algoritmo di [[ML - Concept Learning|concept learning]] $L$
- instanze $X$ 
- un concetto target c
- training example $D_c = \{<x,c(x)>\}$
- è denotiamo con $L(x_i,D_c)$  la classificazione assegnata al instanza $x_i$ da $L$ dopo esser stato allenato su $D_c$

Il _bias induttivo_ di $L$ è ogni insieme minimale di asserzioni $B$ tale che per ogni concetto target $c$ e i suo corrispondenti  training example $D_c$ $$(\forall X_i \in X)[B \land D_C \land x_i] \vdash L(x_i,D_c)$$
dove $A\vdash B$ significa che A è conseguenza logica di B