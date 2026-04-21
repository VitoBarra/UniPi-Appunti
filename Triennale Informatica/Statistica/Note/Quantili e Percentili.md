---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Quantili e Percentili
---
In [[Statistica descrittiva|statistica descrittiva]], **quantili** e **percentili** sono valori che permettono di dividere un insieme di dati ordinati in parti.

Sia $\mathbf{x}=(x_1,\dots,x_n)$ un insieme di dati ordinato in senso crescente. 

Il **$\beta$-quantile**, con $\beta \in (0,1)$, è un valore $t$ tale che:
- almeno una frazione $\beta$ dei dati è minore o uguale a $t$
- almeno una frazione $1-\beta$ dei dati è maggiore o uguale a $t$
ovvero, il $\beta$-quantile è una soglia che divide i dati ordinati secondo una certa proporzione.

Alcuni quantili hanno nomi particolari:
- il **primo quartile** è il $0.25$-quantile
- il **secondo quartile** è il $0.50$-quantile, cioè la **mediana**
- il **terzo quartile** è il $0.75$-quantile


I **percentili** sono un caso particolare dei quantili. Se si considera un numero $k \in (0,100)$, il percentile $k$-esimo corrisponde al quantile di ordine $$\beta = \frac{k}{100}$$quindi, per esempio, il $25$-esimo percentile coincide con il primo quartile, il $50$-esimo percentile con la mediana e il $75$-esimo percentile con il terzo quartile.

Il percentile $k$-esimo può essere descritto come un valore $t$ tale che:
- almeno il $k\%$ dei dati è minore o uguale a $t$
- almeno il $(100-k)\%$ dei dati è maggiore o uguale a $t$

A seconda della convenzione usata, il percentile può non essere unico; in questi casi si sceglie una regola convenzionale per determinarlo.