---
Subject: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Statistiche campionarie su variabili gaussiane
---
Assumendo di ipotesi sul [[Campione Statistico|campione aleatorio]] si possono inferire più informazioni grazie al [[Teorema centrale del limite|Teorema centrale del limite]], molti fenomeni sono ben descritti da campioni di variabili [[Variabili Aleatorie Notevoli - Gaussiane|gaussiane]] 

#### Teorema
_siano_ $X_1,\dots X_{n}$ un [[Campione Statistico|campione statistico]] [[Variabili Aleatorie Notevoli - Gaussiane|gaussiano]] $N(n,\sigma^{2})$ e poniamo $$\overline{X}_{n}=\frac{1}{n}\sum^{n}_{i=1}X_{i}\ \ \ \ \ S^{2}_{n}=\frac{1}{n-1}\sum^{n}_{i=1}(X_{i}-\overline{X}_{n})^{2}$$
_allora_ vale
1. $\overline{X}_{n}$ e $S^{2}_{n}$ sono indipendenti
2. la variabile $\overline{X}_{n}$ ha densita $N\left( m,\frac{\sigma^{2}}{n} \right)$
3. la variabile $\frac{n-1}{\sigma^{2}}S^{2}_{n}$ ha densita ([[Variabili Aleatorie Notevoli - Chi-quadro|chi-quadro]] $X^{2}(n-1)$)
4. la variabile $T=\sqrt{ n }\frac{\overline{X}_{n}-m}{S}$ ha [[Variabili Aleatorie notevoli - Student|densita di student]] $T(n-1)$