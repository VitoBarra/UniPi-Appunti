---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# CRN - Michaelis-Menten kinetics
---
La **Michaelis–Menten kinetics** descrive una cinetica [[CRN - Modello mass-action|non–mass-action]] applicata a una [[Chemical Reaction Network (CRN)|CRN]] quando una reazione **enzimatica** viene modellata in forma ridotta, sostituendo il meccanismo elementare con una legge efficace.

Si considera il meccanismo:$$E + S \xrightleftharpoons[k_{-1}]{k_1} ES \xrightarrow{k_2} E + P$$dove $E$ è l’enzima, $S$ il substrato, $ES$ il complesso intermedio e $P$ il prodotto.

Ipotesi strutturali:
- il binding/unbinding $E+S \leftrightarrow ES$ è molto più veloce della conversione catalitica $ES \to E+P$ quindi la concentrazione di $[ES]$ è considerata in **equilibrio dinamico**
- l’enzima non viene consumato: $$E_{tot} = [E] + [ES]$$è costante nel tempo.

Applicando il [[CRN - Modello mass-action|Modello mass-action]] si ottiene:
$$
\begin{array}{rcl}
\cfrac{d[ES]}{dt} & = & k_1[E][S]-(k_{-1}+k_2)[ES] \\
\cfrac{d[P]}{dt}  & = & k_2[ES]
\end{array}
$$
Si introduce la **Quasi-Steady-State Approximation (QSSA)** assumendo:
$$\frac{d[ES]}{dt}\approx 0$$
e utilizzando la conservazione dell’enzima
$$E_{tot} = [E] + [ES] \quad \Rightarrow \quad [E]=E_{tot}-[ES]$$
da cui si ricava:
$$[ES]=\frac{E_{tot}[S]}{K_M+[S]}$$
con costante di **Michaelis**:$$K_M=\cfrac{k_{-1}+k_2}{k_1}$$mentre la velocità di formazione del prodotto ($v$) diventa:$$v=\frac{d[P]}{dt}=k_2[ES]=\frac{V_{max}[S]}{K_M+[S]}$$dove:
- $V_{max}=k_2E_{tot}$ è la **velocità massima**, ottenuta quando tutto l’enzima è nello stato $ES$ (enzima saturo);
- $V_{max}$ è l’asintoto della curva velocità di reazione $v$ vs $[S]$;
- ponendo $[S]=K_M$ si ottiene $$v=\frac{V_{max}K_M}{K_M+K_M}=\frac{V_{max}}{2}$$ quindi $K_M$ è la concentrazione di substrato $[S]$ che produce metà della velocità massima.
Interpretazione:
- $K_M$ misura l’affinità enzima–substrato;
- $K_M$ piccolo $\Rightarrow$ alta affinità (mezzo-saturazione a basse concentrazioni);
- $K_M$ grande $\Rightarrow$ bassa affinità.
![[IMG - Michaelis-menten kinetics.png]]

Essa costituisce un caso particolare della [[CRN - Hill kinetics|Hill kinetics]] con coefficiente di Hill $h=1$.
### Confronto con mass action
La cinetica di **Michaelis–Menten** sostituisce il meccanismo della [[CRN - Modello mass-action|mass-action]] con una legge cinetica efficace che elimina la variabile intermedia $[ES]$ tramite **QSSA**, riducendo la dimensionalità del corrispondente [[ODE - Sistemi|sistema di ODE]] pur preservando il comportamento macroscopico della trasformazione $S \to P$.  Infatti la stessa reazione con  **ODE ottenute da mass-action**$$
\begin{cases}
\dfrac{d[E]}{dt} = (k_{-1}+k_2)[ES] - k_1[E][S] \\
\dfrac{d[ES]}{dt} = k_1[E][S] - (k_{-1}+k_2)[ES] \\
\dfrac{d[S]}{dt} = k_{-1}[ES] - k_1[E][S] \\
\dfrac{d[P]}{dt} = k_2[ES]
\end{cases}
$$Sistema a 4 equazioni accoppiate che include:
- dinamica dell’enzima libero $[E]$;
- dinamica del complesso intermedio $[ES]$;
- due scale temporali (binding veloce, catalisi lenta).

mentre l' **ODE ottenute da Michaelis–Menten** è $$
\begin{cases}
\dfrac{d[S]}{dt} = -\dfrac{V_{\max}[S]}{K_M + [S]} \\
\dfrac{d[P]}{dt} = \dfrac{V_{\max}[S]}{K_M + [S]}
\end{cases}
$$Sistema ridotto a 2 equazioni:
- eliminazione esplicita di $[E]$ e $[ES]$;
- incorporazione dei parametri microscopici in $K_M$ e $V_{\max}$;
- descrizione diretta della trasformazione $S \to P$.

[[ODE - Integrazione Numerica|Simulazione numerica]] con:
$$
k_1=0.1, \quad k_{-1}=1000, \quad k_2=0.3
$$
condizioni iniziali:
$$
[E]_0=100, \quad [S]_0=10000, \quad [ES]_0=0, \quad [P]_0=0
$$

Poiché $k_{-1}\gg k_2$, il binding/unbinding è molto più rapido della catalisi: la separazione di scala temporale rende valida la QSSA e le traiettorie del modello ridotto risultano praticamente sovrapponibili a quelle del modello mass-action completo.
![[IMG - CRN - Michaelis-menten kinetics confornto con mass action.png]]