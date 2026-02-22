---
Course: "[[Analisi|Analisi]]"
tags:
  - Analisi
Area: 
topic: 
SubTopic:
---
# Integrazione numerica
---
L’**integrazione numerica** consiste nell’approssimare il valore di un [[Integrali|integrale]] definito
$$\int_a^b f(x)\,dx$$
mediante procedure discrete che utilizzano un numero finito di valutazioni della funzione. Questo è necessario quando l’integrale non è calcolabile in forma chiusa oppure quando la funzione è nota solo in un insieme discreto di punti (ad esempio dati sperimentali o risultati di simulazioni).

L’idea di base è sostituire la funzione con un’approssimazione più semplice su una partizione dell’intervallo
$$a=x_0<x_1<\dots<x_n=b$$
e integrare esattamente tale approssimazione. Nel caso di passo uniforme $h=\frac{b-a}{n}$ si ottiene una formula di quadratura della forma
$$\int_a^b f(x)\,dx \approx \sum_{i=0}^n w_i\,f(x_i),$$
dove i pesi $w_i$ dipendono dal metodo scelto.

Geometricamente si approssima l’area sotto la curva tramite figure elementari (rettangoli, trapezi) oppure tramite polinomi interpolanti di grado più alto. All’aumentare della regolarità della funzione e della finezza della partizione, l’errore dell’approssimazione tende a diminuire. Se il passo è $h$, un metodo ha ordine $p$ quando l’errore globale soddisfa $E(h)=O(h^p)$.

Le tecniche di integrazione numerica si distinguono principalmente per il tipo di approssimazione utilizzata e per il modo in cui vengono scelti i punti di valutazione e i pesi. Nel contesto di queste note rientrano in questa categoria:
- [[Integrazione numerica - Quadratura numerica]]
- [[Integrazione Monte Carlo]]