---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Curvatura su superfici discrete
--- 
### Curvature principali
le **curvature principali discrete** sono le [[Curvatura di una superfice|curvature]] calcolate su una [[Mesh Poligonali|mesh poligonare]] 
$$k_M = H + \sqrt{ H^2 -G } \quad\quad\quad k_m = H - \sqrt{ H^2 -G }$$

### Curvatura Media  
la **curvatura media discreta** è la [[Curvatura media|Curvatura media]]  calcolata su una [[Mesh Poligonali|Mesh Poligonale]]  $$H = \| \Delta_S X \|$$ dove è  $\Delta_S X$ è il [[Laplaciano di una funzione discreta|laplaciano discreto]] calcolato con il metodo delle cotangenti è quindi semplificando diventa:  $$H(p) = \frac{1}{2A} \sum (\cot \alpha_i + \cot \beta_i) \|p - p_i\|$$ e questa Rappresenta la [[Divergenza di una superfice|divergenza]] media della superficie rispetto ai vicini.  
![[IMG - Curvatura media discreta.png]]



# Curvatura gaussiana
la curvatura **Curvatura Gaussiana discreta** è la [[curvatura gaussiana|curvatura gaussiana]] calcolata su una [[Mesh Poligonali|mesh poligonale]]   
Definita come **difetto angolare** normalizzato:  
$$K_G(v_i) = \frac{1}{3A} \left(2\pi - \sum_{t_j \text{ adj } v_i} \theta_j\right)$$  
Dove $\theta_j$ sono gli angoli al vertice $v_i$ e $A$ è l’area dei triangoli adiacenti. Intuitivamente, misura quanto la superficie si discosta da un piano.  
![[IMG - Curvatura gaussiana discreta.png]]


  
La **curvatura gaussiana discreta** può essere instabile su [[Mesh Poligonali|mesh]] irregolari, soprattutto se **triangoli piccoli** generano **picchi di curvatura**.  

per risolvere questo problema nella pratica si fa **fitting** delle curvature in una superficie parte dalla definizione di un **intorno locale** di raggio $r$ attorno a un punto $p$. Questo parametro di scala $r$ determina l'ampiezza della regione considerata, influenzando direttamente la capacità del metodo di filtrare il rumore ad alta frequenza.  

In dettaglio:  
1. Si raccolgono tutte le facce nell'intorno di raggio $r$.  
2. Si calcola l'asse medio $w = \frac{1}{n_v} \sum_{i=1}^n n_i$, dove $n_v$ è il numero di vertici e $n_i$ le normali.  
3. Si scartano i vertici $v_i$ con $n_i \cdot w < 0$ per garantire coerenza nell'orientazione .  

4. Si definisce poi un **[[Frames|sistema di riferimento]] locale** $(u, v, w)$, con $w$ come asse principale e $u$, $v$ ortogonali su un piano perpendicolare a $w$ .
5. I vertici vengono proiettati in questo sistema  e approssimati tramite un polinomio quadratico:  $$f(u,v) = au^2 + bv^2 + cuv + du + ev$$
6. Le curvature a $p$ si derivano analiticamente dalle forme fondamentali di $f$ nell'origine.  

Il **fitting** polinomiale permette di **approssimare localmente** la superficie, sostituendo la geometria originale con una versione "morbida" che filtra le micro-variazioni (rumore). La scelta di $r$ è cruciale: un raggio ampio smorza le asperità, evidenziando il comportamento a larga scala, mentre un raggio piccolo preserva i dettagli fini. Questo approccio è analogo alle tecniche di **image processing multiscala**, dove feature come le curvature diventano robuste a rotazioni e variazioni locali, fornendo descrittori invarianti (es. vettori di Fisher).  
![[IMG - fitting multi scala.png]]
Il metodo nasconde implicitamente le **asperità** al di sotto della scala definita da $r$, trasformando una superficie irregolare (con curvature "spike") in una rappresentazione regolare. Ciò è particolarmente utile in contesti con rumore, dove l'obiettivo è catturare l'andamento globale della superficie anziché le fluttuazioni casuali.

