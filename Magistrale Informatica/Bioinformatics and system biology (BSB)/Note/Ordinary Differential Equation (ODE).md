---
Course: "[[Analisi|Analisi]]"
tags:
  - Analisi
Area: 
topic: 
SubTopic:
---
# Ordinary Differential Equation (ODE)
---
Una **Ordinary Differential Equation (ODE)** è un’[[Equazioni differenziali|equazione differenziale]] che coinvolge una [[funzioni|funzione]] incognita di una **sola variabile** indipendente e le sue [[derivate|derivate]] rispetto a tale variabile, la forma generale (equazione scalare di ordine $n$): $$F\big(x,y,y',y'',\dots,y^{(n)}\big)=0$$ ogni **ODE** ha associato un ordine e questo è definito dall’**ordine massimo** della derivata, ad esempio in modo esplicito un **ODE** del **primo ordine** risulta come: $\cfrac{dy}{dx}=f(x,y)\iff y'=f(x,y)$
Classificazioni principali:
- Lineare: $y'=A(x)y+b(x)$
- Non lineare: presenza di termini non lineari in $y$.
- Autonoma: $y'=f(y)$ ovvero nella parte destra **NON è** presente la variabile autonoma 
- Non autonoma: $y'=f(y,x)$, ovvero nella parte destra **è** presente la variabile autonoma

Una **soluzione** di una **ODE** è una funzione $y(x)$ sufficientemente regolare (tipicamente $C^n$ se l’equazione è di ordine $n$) definita su un intervallo $I\subseteq\mathbb{R}$ tale che, sostituendo $y$ e le sue [[derivate|derivate]] nell’equazione differenziale, l’identità risulta soddisfatta per ogni $x\in I$. Una **soluzione generale** dipende da costanti arbitrarie in numero **pari all’ordine dell’equazione**, mentre una **soluzione particolare** si ottiene imponendo condizioni iniziali come $y(x_0)=y_0$, che definiscono un **[[ODE - Problema di Cauchy|problema di Cauchy]]** e selezionano, quando esiste ed è unica, una specifica traiettoria nello spazio delle soluzioni. 

Una **soluzione costante** $y(x)=y^*$ è detta **punto di equilibrio** o stato stazionario. Se $y(x)=y^*$ è costante allora per definizione $y'(x)=0$; sostituendo nell’ODE si richiede quindi che il termine di destra si annulli.
- Nel caso **autonomo** $y'=f(y)$ si ottiene $0=f(y^*)$quindi gli equilibri coincidono con gli zeri del campo $f$ e rappresentano configurazioni in cui la dinamica si arresta e lo stato rimane invariato per ogni $x$.
- Nel caso **non autonomo** $y'=f(x,y)$ una soluzione costante $y(x)=y^*$ è un equilibrio solo se $$f(x,y^*)=0\quad\forall x$$cioè se lo stesso valore $y^*$ annulla il campo per ogni valore della variabile indipendente. Questo è possibile solo in **casi particolari**; per questo il concetto di equilibrio come stato costante è soprattutto naturale per sistemi autonomi.