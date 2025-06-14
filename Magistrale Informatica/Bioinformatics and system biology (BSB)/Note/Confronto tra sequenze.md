---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Confronto tra sequenze
---
Il **confronto tra sequenze** è uno dei problemi dell’[[Analisi di sequenze]] e riguarda lo studio delle relazioni tra due stringhe simboliche, con l’obiettivo di valutarne la **somiglianza**, la **dissimilarità** o la presenza di **strutture comuni**. L’obiettivo è individuare **regolarità**, **ripetizioni**, **pattern condivisi** o differenze strutturali, senza imporre vincoli formali sul modo in cui le sequenze devono essere messe in relazione.

Per questo scopo vengono impiegate nozioni di [[Definizione di distanza|distanza]], utili a quantificare quanto due stringhe differiscano l’una dall’altra. Alcuni esempi di tali misure sono la [[Edit distance]] e la [[Hamming distance]].

È inoltre possibile visualizzare la relazione tra due stringhe mediante un **dot plot**, una matrice bidimensionale associata a due stringhe $X$ e $Y$ di lunghezza rispettivamente $n$ e $m$. L’asse orizzontale indica le posizioni di $X$, mentre l’asse verticale indica quelle di $Y$. Il dot plot può essere definito come una funzione binaria
$$
D:\{1,\dots,n\}\times\{1,\dots,m\}\to\{0,1\}
$$
in cui $D(i,j)=1$ quando la coppia di posizioni $(i,j)$ soddisfa un criterio di corrispondenza prefissato. Solitamente si usa il semplice criterio:$$
D(i,j)=1 \iff X_i = Y_j
$$Questa definizione evidenzia direttamente corrispondenze locali tra simboli, mentre strutture globali emergono come configurazioni geometriche di punti.
![[IMG - confronto tra stringhe dot plot.png]]
