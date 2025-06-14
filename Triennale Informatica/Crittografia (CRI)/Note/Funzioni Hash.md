---
Course: "[[Programmazione e Algoritmica (PEA)]]"
topic: nota
tags:
  - PEA
---
# Funzioni Hash
---
sono particolari tipi di [[Funzioni|funzioni]] $h:X \rightarrow Y$ dove _vale che_
$$n=|X| \gg |Y|=m$$
e che $\exists X_{1},\dots X_{m}\subseteq X$ _disgiunti_ tale che
$$\begin{array}{}
X = X_{1} \cup \dots \cup X_{m} \\
\forall  i \forall x \in  X_{i} . h(x)=y
\end{array}
$$
ovvero c è una [[famiglia di Insiemi|famiglia di sottoinsiemi]] del _dominio_ $X$  per cui ogni elemento porta alla stessa _immagine_ $y$ nel _codominio_ $Y$   


una __*buona*__ funzione _hash_ ha le seguenti proprietà
1. I _sotto insiemi_ $X_{1}\dots X_{m}$ hanno circa la stessa [[Insiemi - Cardinalita|cardinalità]]
	- questo assicura che presi su valori a caso da $X$ hanno una [[Definizione di Probabilita|probabilita]] è circa $\frac{1}{m}$ di avere la stessa _immagine_ in $Y$
2. Elemento di $X$ _molti simili_ tra loro appartengono a sotto insiemi diversi
	- ad esempio se $X= \mathbb{N}$ allora numeri prossimi devono avere immagine molto diverse.



### Realizzazioni
solitamente queste funzioni sono _realizate_ con l [[Algebra modulare|algebra modulare]] e funzionano meglio se sono in modulo con un numero $p$ [[Numeri primi|primo]] siccome genera meno collisioni