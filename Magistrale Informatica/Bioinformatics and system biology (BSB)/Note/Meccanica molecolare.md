---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# Meccanica molecolare
---
La **meccanica molecolare** descrive come calcolare l’[[Energia Molecolare e conformazioni|energia molecolare]] associata alle **[[Energia Molecolare e conformazioni|conformazioni]]** di una [[Molecole|molecola]]. Essa approssima la molecola come un insieme di masse atomiche collegate da forze attrattive, modellate come **sfere connesse da molle**, e utilizza un insieme empirico di funzioni energetiche, noto come **force field** (FF), per stimare l’**energia potenziale** di una data conformazione.

Un **force field** calcola l’energia molecolare come somma di contributi specifici:
1. **bond stretching**: energia di allungamento dei legami  
2. **angle bending**: energia di flessione degli angoli  
3. **torsional rotation**: energia torsionale di rotazione  
4. **van der Waals interactions**: energia di interazioni non leganti  
5. **electrostatic interactions**: energia elettrostatica tra cariche o dipoli  
6. **hydrogen bonding**: energia dovuta ai legami a idrogeno  
La somma di questi termini fornisce l’energia associata a una conformazione. Una parte importante di tale energia è detta **energia sterica**, contributo energetico legato all’ingombro spaziale degli atomi o dei gruppi all’interno della molecola.  
Una visualizzazione del modello sfere e molle: ![[IMG - modello delle molecole a molle.png]]

Il contributo di **bond stretching** calcola la penalità energetica dovuta alla variazione della lunghezza di un legame rispetto al valore di equilibrio. Considerando il legame come una molla, l’energia è approssimata tramite la legge di Hooke: $$E(L)=\sum k(L)(L-L_0)^2$$ dove $k(L)$ è la costante di forza e $L_0$ la lunghezza di equilibrio.  

Il contributo di **angle bending** calcola la penalità energetica dovuta alla deformazione di un angolo di valenza rispetto al suo valore di equilibrio. L’energia è espressa in forma analoga: $$E(\Theta)=\sum k(\Theta)(\Theta-\Theta_0)^2$$ dove $k(\Theta)$ è la costante di flessione e $\Theta_0$ l’angolo di equilibrio.  
![[IMG - livelli di neergia per bond stretching e angle bending.png]]

Il contributo di **torsional rotation** calcola l’energia associata alla rotazione attorno a un legame singolo, originata da interazioni steriche ed elettroniche tra atomi non direttamente legati. La rotazione è descritta dall’angolo torsionale (angolo diedro) $\theta$, definito da quattro atomi consecutivi $A-B-C-D$ e corrispondente all’angolo tra i piani $(A,B,C)$ e $(B,C,D)$. Durante la rotazione alcune orientazioni risultano energeticamente più favorevoli di altre, per cui l’energia varia in modo periodico, mostrando minimi (conformazioni stabili) e massimi (barriere). La minima energia necessaria per superare questi massimi definisce la **barriera torsionale**. L’energia torsionale si esprime come: $$E_\theta=\sum V_i\big[1+\cos(n\theta+t)\big]$$ dove ciascun termine $V_i$ rappresenta un contributo empirico alla **barriera torsionale**, cioè l’entità delle differenze energetiche tra conformazioni durante la rotazione. Il parametro $n$ è la periodicità torsionale: indica quante volte il profilo energetico (minimi e massimi) si ripete durante una rotazione completa di $360^\circ$, quindi il periodo angolare è $360^\circ/n$. Il termine $t$ è un fattore di fase che determina la posizione di minimi e massimi lungo la rotazione.
un [altra fonte](https://dl-sdg.github.io/RESOURCES/FORCE_FIELD/ff7.html)
![[IMG - sfere di influenze per componente tornsionale.png]]

Il contributo di **van der Waals interactions** calcola le interazioni tra atomi non legati direttamente: repulsione a breve distanza e attrazione di dispersione a lunga distanza. Queste interazioni sono descritte dal potenziale di Lennard-Jones: $$V_{LJ}=4\varepsilon\Big[\Big(\frac{\sigma}{r}\Big)^{12}-\Big(\frac{\sigma}{r}\Big)^6\Big]$$ dove $\varepsilon$ e $\sigma$ sono parametri specifici per ciascuna coppia di particelle determinati empiricamente.
![[IMG - interazioni van der waals.png]]

Il contributo di **electrostatic interactions** calcola l’energia dovuta alle attrazioni o repulsioni tra cariche atomiche o dipoli di legame. Per cariche puntiformi: $$E_{el}(R_{AB})=\frac{Q_AQ_B}{\varepsilon R_{AB}}$$ mentre per dipoli: $$E_{el}(R_{AB})=\frac{\mu_A\mu_B}{\varepsilon R_{AB}^3}(\cos\chi-3\cos\alpha_A\cos\alpha_B)$$ dove $Q$ è la carica, $R$ la distanza, $\varepsilon$ la costante dielettrica e $\mu$ il momento di dipolo.  
![[IMG - contribuzione bipolare eletrostatica.png]]

Il contributo di **[[Legami idrogeno|hydrogen bonding]]** calcola l’energia di un legame a idrogeno, interazione attrattiva tra un idrogeno legato a un elemento elettronegativo e un secondo elemento elettronegativo. L’energia di un forte legame a idrogeno varia tra 12 e 21 kJ/mol. Un’espressione utilizzata è: $$E_{HB}=\frac{332}{\varepsilon}\sum\Big(\frac{q_Dq_A}{d_{DA}}+\frac{A_K}{d_{HA}^{12}}-\frac{B_K}{d_{HA}^{10}}\Big)$$ dove $q$ sono le cariche, $d$ le distanze e $A_K,B_K$ parametri empirici.  
![[IMG - contribuzione per interazioni idrogeno.png]]


