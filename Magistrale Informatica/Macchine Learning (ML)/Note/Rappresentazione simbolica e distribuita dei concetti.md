---
Course: "[[Machine Learning (ML)]]"
tags:
  - IIA
  - ML
Area: 
topic: 
SubTopic:
---
# Rappresentazione simbolica e distribuita dei concetti
I __Concetti__ nel [[Concetti generali del Machine Learning|machine learning]] sono solitamente rappresentati da vettori con valori in $[0,1]$. Il modo in cui questa rappresentazione è costruita è fondamentale per apprendere i concetti e risolvere task che ne fanno uso.  

I __Concetti__ possono essere rappresentati in due modi principali:  

- __Rappresentazione simbolica (o localista)__: si utilizza una codifica __one-hot__, ovvero un vettore sparso in cui solo una posizione è impostata a $1$ (hot) mentre tutte le altre sono $0$. Ogni posizione (un simbolo) rappresenta un concetto specifico.  
- __Rappresentazione distribuita__: si utilizza una codifica densa in cui i valori del vettore possono assumere qualsiasi valore continuo, consentendo una rappresentazione più flessibile.  
  ![[Pasted image 20250206230148.png]]  

Nella __rappresentazione simbolica__, ogni vettore è equidistante dagli altri di $\sqrt{2}$, e quindi non è possibile definire relazioni di similarità tra concetti diversi. Al contrario, nella __rappresentazione distribuita__, la distanza tra i vettori dipende dal modo in cui i concetti sono rappresentati, permettendo di catturare relazioni di similarità: concetti più simili avranno una distanza minore rispetto a concetti molto diversi.  

In generale, la __rappresentazione distribuita__ è più efficiente. Infatti, con una __rappresentazione simbolica__, per rappresentare $n$ concetti servono $n$ valori distinti. Con una __rappresentazione distribuita__, assumendo che ogni posizione del vettore possa assumere $k$ valori diversi, è possibile rappresentare fino a $k^n$ concetti distinti, uno per ogni configurazione possibile. Inoltre, la similarità tra concetti può essere esplicitamente codificata attivando valori simili nelle stesse posizioni. L unico svantaggio è che la __rappresentazione distribuita__ è più difficile da __interpretare__
