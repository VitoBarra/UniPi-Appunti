---
Course: "[[Analisi|Analisi]]"
tags:
  - Analisi
Area: 
topic: 
SubTopic:
---
# ODE - integrazione numerica - Metodo di Eulero
---
Il **Metodo di Eulero** è il metodo di [[Integrazione numerica|integrazione numerica]] **esplicito** a **passo singolo** per approssimare la soluzione del [[ODE - Problema di Cauchy|problema di Cauchy]] di una [[Ordinary Differential Equation (ODE)|ODE]] di primo ordine $$\frac{dy}{dx}=f(x,y),\quad y(x_0)=y_0.$$  
Si discretizza la variabile indipendente come $$x_{n+1}=x_n+h$$ con passo $h>0$.

L’integrazione segue lo schema numerico esplicito $$y_{n+1}=y_n+h\,f(x_n,y_n).$$  
Geometricamente, nell’intervallo $[x_n,x_{n+1}]$ la soluzione viene approssimata con la [[Retta tangente|retta tangente]] alla curva nel punto $(x_n,y_n)$. Infatti dall’ODE si ha $y'(x_n)=f(x_n,y_n)$, cioè la pendenza della soluzione in quel punto è $f(x_n,y_n)$; la retta tangente passante per $(x_n,y_n)$ è quindi
$$\ell(x)=y_n+f(x_n,y_n)(x-x_n).$$
Valutandola in $x_{n+1}=x_n+h \implies h=x_{n+1}-x_n$ si ottiene $$\ell(x_{n+1})=y_n+f(x_n,y_n)h$$ che coincide con la formula del metodo di Eulero. In questo modo la curva soluzione viene sostituita localmente dalla sua tangente e il punto successivo è preso sulla retta anziché sulla soluzione esatta.![[IMG - ODE - Metodo di Eulero.png]]

Questo metodo commette i seguenti errori
- **Errore locale (di discretizzazione)**: è l’errore commesso in un singolo passo assumendo di partire dal valore esatto $y(x_n)$. Si confronta la soluzione esatta al punto successivo con un passo di Eulero eseguito dal valore esatto:
$$el_{n+1}=\left|\,y(x_{n+1})-\big(y(x_n)+h\,f(x_n,y(x_n))\big)\right|.$$
Per il metodo di Eulero vale $el_{n+1}=O(h^2)$.

- **Errore globale**: è la differenza tra soluzione esatta e approssimazione numerica dopo $n$ passi, valutata nello stesso punto $x_n$:
$$e_n=\left|\,y(x_n)-y_n\right|.$$
Per il metodo di Eulero, su un intervallo fissato, vale $e_n=O(h)$.


## Versione implicita (Metodo di Eulero implicito)

La versione **implicita del metodo di Eulero** si ottiene valutando la pendenza nel punto successivo invece che in quello corrente:$$y_{n+1}=y_n+h\,f(x_{n+1},y_{n+1})$$Si discretizza sempre la variabile indipendente con $x_{n+1}=x_n+h$, ma ora la derivata è valutata in $(x_{n+1},y_{n+1})$.

Interpretazione geometrica: mentre il metodo esplicito utilizza la retta tangente nel punto $(x_n,y_n)$, il metodo implicito utilizza la tangente nel punto finale $(x_{n+1},y_{n+1})$. Il nuovo valore viene quindi determinato in modo coerente con la pendenza nel punto di arrivo, rendendo il metodo molto più stabile.

La formula è implicita perché $y_{n+1}$ compare in entrambi i membri; a ogni passo è necessario risolvere un’equazione (in generale non lineare)$$y_{n+1}-h\,f(x_{n+1},y_{n+1})=y_n,$$tipicamente tramite metodi iterativi ([[Metodo delle tangenti o di Newton|Newton]], [[metodo del punto fisso|punto fisso]], ecc.). Nel caso **lineare** la soluzione può essere esplicita.

Per l’equazione test lineare$$y'=\lambda y$$si ottiene$$y_{n+1}=y_n+h\,\lambda y_{n+1}\quad\Rightarrow\quad y_{n+1}=\frac{1}{1-h\lambda}\,y_n.$$La stabilità richiede$$\left|\frac{1}{1-h\lambda}\right|<1,$$condizione soddisfatta per ogni $h>0$ quando $\operatorname{Re}(\lambda)<0$. Il metodo è quindi **A-stabile**: la regione di stabilità contiene tutto il semipiano $\operatorname{Re}(\lambda)<0$, rendendolo adatto a **[[ODE - Sistemi|sistemi stiff]]**.

Errore analoghi al metodo esplicito:
- errore locale: $O(h^2)$,
- errore globale: $O(h)$,
quindi l’ordine resta 1 come nella versione esplicita, ma con proprietà di [[Tipi di Errore nel calcolo numerico|stabilità]] molto migliori.