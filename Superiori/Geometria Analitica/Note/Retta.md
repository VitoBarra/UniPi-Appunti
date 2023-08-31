---
type: nota
course: Analisi
topic: 
tags: GA
---

Prev: [[Geometria analitica (GA)]]

# Retta
---
una _retta_ è un insieme infinito di punti allineati nel piano o nello spazio ed è un ente geometrico fondamentale.

una _retta_ nel piano cartesiano 
![[Pasted image 20230523021918.png]]
è rappresentata dal equazione in _forma esplicita_
$$y=mx+q$$
dove 
- $m$ è detto _coefficiente angolare_
	- rappresenta la pendenza della retta
- $q$ è detto _termine noto_
	- rappresenta il punto di intersezione con l asse $x$

mentre in _forma implicita_ é espressa come
$$ax +by+c=0$$
le due forme sono equivalenti e si puo passare dal una al latra con dei passi algebrici. si ha che supponendo $b \not = 0$
$$m=-\frac{a}{b} \ \ \ \ \ q =-\frac{c}{b}$$
per $a =0$ si ha la _retta orizzontale_ 
$$y = -\frac{c}{b}$$
e per $b=0$ si ha la _retta verticale_
$$x=-\frac{c}{a}$$


## Formule
#### Retta passante per 1 punto
_sia_ $P_1=(x_{1},y_{1}) \in \mathbb{R}^{2}$ un punto
##### Equazione della Retta passante per 1 punto
_sia_ $m$ il coefficiente angolare noto
_allora_ la formula della retta passante per il punti $P_{1}$ di coefficiente $m$ è
$$y-y_{1}=m(x-x_{1})$$


#### Retta passante per 2 punti
_siano_ $P_1=(x_{1},y_{1}),P_2=(x_{2},y_{2}) \in \mathbb{R}^{2}$ due punti

##### Equazione della Retta passante per 2 punti
_se_ $x_{1} \not = x_{2}$ e  $y_{1} \not = y_{2}$
_allora_ la formula per calcolare l equazione passata per i due punti è
$$\frac{y-y_{1}}{y_{2}-y_{1}}=\frac{x-x_{1}}{x_{2}-x_{1}}$$

##### Coefficiente e termine noto
_se_ $x_{1} \not = x_{2}$
_allora_ il coefficiente angolare della retta passante per i due punti si calcola come
$$m=\frac{y_{2}-y_{1}}{x_{2}-x_{1}}\ \ \ \ \ q= \frac{x_{2}y_{1}-x_{1}y_{2}}{x_{2}-x_{1}}$$

#### Condizione di parallelismo
due rette sono dette _parallele_ se questo hanno lo stesso coefficiente angolare
$$m_{1}=m_{2}$$
o in _forma implicita_
$$a_{1}b_{2}-a_{2}b_{1} =0$$
#### Condizione di perpendicolarità
dure rette si dicono _perpendicolari_ se i coefficienti angolari sono uno il reciproco del altro 
$$m_{1}=\cfrac{1}{m_{2}}\ \ \ \ \ \ \ \ \ \ m_{1}m_{2}=-1$$
o in _forma implicita_ 
$$a_{1}a_{2}-b_{1}b_{2}=0$$