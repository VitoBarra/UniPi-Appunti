---
Course: "[[Analisi|Analisi]]"
tags:
  - Analisi
Area: 
topic: 
SubTopic:
---
# ODE - Integrazione Numerica
---
L’integrazione numerica di una ODE nasce dal **problema di Cauchy** $$\frac{dx}{dt}=f(t,x),\quad x(t_0)=x_0$$ che consiste nel determinare una funzione $x(t)$ che soddisfi l’equazione differenziale e la condizione iniziale. Si veda [[Problema di Cauchy per ODE|definizione formale del problema di Cauchy]].

Nella maggior parte dei casi non è disponibile una soluzione analitica esplicita; anche quando esiste, può non essere computazionalmente accessibile. Per questo si introducono metodi numerici che costruiscono una successione discreta $t_n=t_0+n h$ con $x_n\approx x(t_n)$.

Schema generale a passo singolo:
$$x_{n+1}=x_n+h\,\Phi(t_n,x_n,h)$$
dove $\Phi$ approssima il campo vettoriale medio nell’intervallo $[t_n,t_{n+1}]$.

Perché servono metodi diversi:
- Equazioni non lineari raramente integrabili in forma chiusa.
- Sistemi di grande dimensione.
- Presenza di scale temporali multiple.
- Necessità di controllo dell’errore.
- Compromesso tra costo computazionale e accuratezza.

Classificazioni:
- Passo singolo vs multistep.
- Espliciti vs impliciti.
- Passo fisso vs adattativo.

Metodi principali:
- [[ODE - integrazione numerica - Metodo di Eulero|Metodo di Eulero]]
- [[ODE - integrazione numerica - Metodo di Eulero implicito|Metodo di Eulero implicito]]
- [[ODE - integrazione numerica - Metodo di Runge-Kutta|Metodi di Runge-Kutta]]
- [[ODE - integrazione numerica - Runge-Kutta 4 (RK4)|Runge-Kutta di ordine 4]]
- [[ODE - integrazione numerica - Metodi di Adams|Metodi multistep di Adams]]
- [[ODE - integrazione numerica - Metodo di Backward Differentiation Formula (BDF)|Backward Differentiation Formula (BDF)]]

Ordine del metodo: è $p$ se l’errore globale è $O(h^p)$ e l’errore locale è $O(h^{p+1})$.

Stabilità numerica: analizzata tramite l’equazione test $$x'=\lambda x$$; la regione di stabilità determina per quali $h\lambda$ l’errore non cresce.

Un sistema è detto **stiff** quando contiene autovalori con parte reale molto negativa che impongono passi $h$ estremamente piccoli per metodi espliciti. In tali casi sono preferibili metodi impliciti (es. [[ODE - integrazione numerica - Metodo di Eulero implicito|Eulero implicito]], [[ODE - integrazione numerica - Metodo di Backward Differentiation Formula (BDF)|BDF]]).

La nozione teorica di stiff system è trattata in [[Ordinary Differential Equation (ODE)|nota generale sulle ODE]], mentre qui si considerano le implicazioni computazionali.