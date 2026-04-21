---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Regressione lineare - Interpretazione probabilistica
---
La [[Modelli lineari - Retta di regressione|retta di regressione]] può essere interpretata anche come un [[Modelli probabilistici|modello probabilistico]].

in questo modello si assume che ogni osservazione sia generata da una _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_:$$Y_i=a+bx_i+\varepsilon_i$$dove $\varepsilon_i$ rappresenta l'errore casuale.

si assume che gli errori $\varepsilon_i$ siano [[Variabili Aleatorie Notevoli - Gaussiana|gaussiani]], [[Indipendenza Stocastica|indipendenti]] e con [[Variabili aleatoria - Valore atteso|media]] nulla:$$\varepsilon_i\sim \mathcal{N}(0,\sigma^2)$$
 la [[Legge di Probabilita|distribuzione]] di  $Y_i$ [[Probabilita condizionata|condizionato]] su $x_i$ è una variabile gaussiana:
$$Y_i\mid x_i\sim \mathcal{N}(a+bx_i,\sigma^2)$$
Questo succede perché, una volta fissato $x_i$, il termine $a+bx_i$ è una costante. Quindi $Y_i$ è dato da una costante più un errore gaussiano, e sommare una costante a una variabile gaussiana cambia solo la media, non il tipo di distribuzione.

La retta non descrive quindi direttamente tutti i punti osservati, ma descrive la [[Variabili aleatoria - Valore atteso|media]] della distribuzione da cui vengono generati:$$\mathbb{E}[Y_i\mid x_i]=a+bx_i$$La [[Variabili aleatorie - Varianza|varianza]] $\sigma^2$ misura invece quanto i punti possono oscillare attorno alla retta.

#### Relazione con i minimi quadrati
Questa interpretazione è coerente con la definizione tramite [[Modelli lineari - Retta di regressione|minimi quadrati]]. Infatti, sotto l'ipotesi di errori gaussiani, stimare $a$ e $b$ tramite [[Stima Parametrica - Metodo di Massima Verosomiglianza|massima verosimiglianza]] porta allo stesso problema di ottimizzazione:$$\min_{a,b}\sum_i (y_i-a-bx_i)^2$$Quindi la retta dei minimi quadrati può essere vista come lo stimatore di massima verosimiglianza del modello:
$$
Y_i\mid x_i\sim \mathcal{N}(a+bx_i,\sigma^2)
$$
