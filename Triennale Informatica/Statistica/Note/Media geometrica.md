---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Media geometrica
---
La **media geometrica** è un indice di posizione usato per sintetizzare dati numerici positivi, soprattutto quando i valori rappresentano **fattori moltiplicativi**, rapporti, tassi di crescita o quantità che si compongono tramite prodotto.

_Sia_ $x=(x_1,\dots,x_n)$ un vettore di dati con $x_i>0$ per ogni $i$.
_Allora_ la **media geometrica** è definita come$$G(x)=\sqrt[n]{\prod_{i=1}^{n}x_i}$$ovvero$$G(x)=\left(\prod_{i=1}^{n}x_i\right)^{\frac{1}{n}}$$
#### Forma logaritmica
Poiche il prodotto di molti valori puo essere scomodo da trattare, la media geometrica puo essere riscritta usando i [[Funzione logaritmica|logaritmi]].

Infatti vale$$
\log G(x)
=\log\left(\prod_{i=1}^{n}x_i\right)^{\frac{1}{n}}
=\frac{1}{n}\sum_{i=1}^{n}\log x_i
$$quindi$$
G(x)=\exp\left(\frac{1}{n}\sum_{i=1}^{n}\log x_i\right)
$$cioe la media geometrica è l'esponenziale della [[Statistica descrittiva - Dati Numerici#Media (definizione)|media aritmetica]] dei logaritmi dei dati.

#### Interpretazione
La media **geometrica rappresenta** il valore costante che, sostituito a tutti i dati, lascia invariato il prodotto complessivo.

Infatti se $G(x)$ è la media geometrica, allora$$
G(x)^n=\prod_{i=1}^{n}x_i$$Per questo motivo è adatta quando il fenomeno osservato è moltiplicativo e non additivo.

Per esempio, se una quantità viene moltiplicata successivamente per fattori $x_1,\dots,x_n$, allora $G(x)$ è il fattore medio costante che produce lo stesso effetto complessivo.

#### Relazione con la media aritmetica
Per dati positivi vale la diseguaglianza$$
G(x)\leq \overline{x}
$$dove $\overline{x}$ è la [[Statistica descrittiva - Dati Numerici#Media (definizione)|media aritmetica]], l'uguaglianza vale se e solo se tutti i dati sono uguali.

Questa proprietà mostra che la media geometrica è meno sensibile ai valori molto grandi rispetto alla media aritmetica, perche combina i dati tramite prodotto invece che tramite somma.


