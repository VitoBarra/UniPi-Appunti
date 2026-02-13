---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
Area: "[[Test Statistici]]"
topic:
SubTopic:
---

# Test Statistici - p-value
---
Il $p$-value in un [[Test Statistici|test statistico]] è una quantità che dipende dalla realizzazione del [[Campione Statistico|campione]] e misura il livello minimo al quale l’ipotesi nulla verrebbe rifiutata.

Sia $\{C(\alpha)\}_{\alpha\in(0,1)}$ una famiglia di [[Test Statistici|regioni critiche]] tale che il test con ipotesi nulla $\mathcal H_0:\theta\in\Theta_0$ e regione critica $C(\alpha)$ abbia livello $\alpha$.  
Data una realizzazione $(x_1,\dots,x_n)$ del campione $(X_1,\dots,X_n)$, il **p-value** è il numero
$$
\overline\alpha=\overline\alpha(x_1,\dots,x_n)
$$
per cui:
- se $\alpha<\overline\alpha$ il test con regione critica $C(\alpha)$ **non rifiuta** $\mathcal H_0$ (ipotesi accettata al livello $\alpha$);
- se $\alpha>\overline\alpha$ il test **rifiuta** $\mathcal H_0$.

Il $p$-value rappresenta quindi il più piccolo livello di significatività al quale l’ipotesi nulla verrebbe rifiutata, e fornisce una misura sintetica della compatibilità tra i dati osservati e $\mathcal H_0$.  
Valori piccoli indicano scarsa plausibilità dell’ipotesi nulla rispetto al modello probabilistico considerato, mentre valori grandi indicano che i dati osservati sono compatibili con $\mathcal H_0$.![[IMG - p-value.jpg]]