---
Course: "[[Fondamenti Del Informatica (FDI)]]"
tags:
  - FDI
Area: 
topic: 
SubTopic:
---

# Dimostrazione per induzione
---


### Definizione
sia $\mathbb{N}^*$ l insieme degli interi positivi escluso lo $0$ e siano  $a$ e $b$ interi diversi da $0$ l insieme $S = \{c \in \mathbb{N} ^* . \ \ a \mid c,\ b \mid c\}$  è un insieme non vuoto siccome $ab \in S$. (_gli appunti dicono $\pm$ mai numeri sono solo positivi probabilmente errore da segnalare_ )
il minimo di questo insieme viene chiamato _mcm_(a,b); minimo comuni multiplo

## Dimostrazione per induzione 
Sia $P(n)$ una proposizione per ogni $n \in \mathbb{N}$ Supponiamo che $P(0)$ e che $P(k)\implies P(k+1)$ allora $P(n)$ è vera per ogni $n\in \mathbb{N}$  


##### Dimostrazione con principio di buon ordinamento 
supponiamo 
$$S = \{k\in \mathbb{N} | P(k) \text{ è falsa}\}$$
essere un [[Insimi| Insiemi]] non vuoto allora $S$ ha un elemento minimo $s$.
- per ipotesi $0$ non appartiene ad $S$.quindi $s \geq 1$ in particolare $s-1$ non appartiene ad $S$ pertanto $P(s-1)$ è vera. per ipotesi ciò implica che $P(s)$ sia vera e quindi $s$ non è un elemento mento di $S$.
- siccome $s$ era l elemento minimo non ci sono altri elementi e questo è una contradizione perciò $S$ è necessariamente vuoto 

##### Dimostrazione utilizzando il principio di induzione
supponiamo 
$$S = \{k\in \mathbb{N} | P(k) \text{ è vera}\}$$
allora $0 \in S$ per Ipotesi. per i poteri, $n \in S \implies n + 1 \in S$ quindi $S = \mathbb{N}$ 

> [!note]
> Si può anche iniziare l’induzione da k = L invece che da k = 0. Si tratta solo di reindicizzare l’elenco delle proposizioni: $Q(k) = P(k − L)$.

> [!note]
>  La forma completa del principio di induzione  implica la seguente forma forte di induzione: Sia P(n) una proposizione per ogni n ∈ N. Supponiamo che 
>  - $P(0)$ sia vera; 
>  - $P(0),...,P(k)$ siano vere implica che $P(k +1)$ sia vera. Allora $P(n)$ è vera per ogni $n \in N$.

