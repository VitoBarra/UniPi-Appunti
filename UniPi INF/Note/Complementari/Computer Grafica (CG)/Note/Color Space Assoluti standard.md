---
type: nota
course: Computer grafica
topic: 
tags:
  - CG
Parent MOC: "[[Computer Grafica (CG)]]"
---


# Color Space Assoluti standard
---
#### Color space CIE  
i _Color Space_ _CIE RGB_ e successivamente _CIE XYZ_ sono nati per essere _sistemi standard_ che sono _indipendenti_ dal device e si basano sui fenomeni fisici e sulla percezione umana. sono quindi _Color Space Assoluti_ .
Si basano su dati empirici presi da un esperimento, questo consiste nel chiedere a degli osservatori di cambiare i valori di luce di 3 lampade  _blu_ , _rossa_ e  _verde_ per riuscire ricreare un altro colore a lui mostrato che è ”_puro_” ovvero generato da una luce che emette la specifica frequenza del colore e non è una combinazione di piu luci
![[IMG_0716.png]]
questo esperimento ha generato le seguenti _color matching function_, che sono le funzioni di come la luce delle lampade cambia in base al colore che si vuole ricreare, indicato nelle ascisse con la lunghezza d onda $\lambda$   
![[IMG_0713.png]]
dove la funzione  _rosso_ $\overline{r}(\lambda)$ ha una parte _negativa_ siccome certe colori non sono raggiungibili tramite la sola composizione delle tre luci ma lo sono invece aggiungendo del rosso al colore che si vuole raggiungere, quindi matematicamente “_sottraendolo_”

E quindi data la funzione di _Power spectrum distribution_ $I(\lambda)$ si possono definire i colori come $$\begin{array}{}
 R  & = &\displaystyle  \int I(\lambda)\overline{r}(\lambda)  \, dx \\
G  & = &\displaystyle  \int I(\lambda)\overline{g}(\lambda)  \, dx \\
 B & = &\displaystyle  \int I(\lambda)\overline{b}(\lambda)  \, dx
\end{array}$$
##### CIR XYZ
dal modello _CIE  RGB_ è stato poi derivato  il modello _CIE XYZ_ che rende tutte le funzioni positive e mappa i colori direttamente sul piano cartesiano 3D.
Cosi facendo le funzioni risultanti sono le seguenti
![[IMG_0714.png]]
e per passare da un _sistema_ al altro si ha la formula $$\begin{bmatrix}
X \\ Y \\ Z
\end{bmatrix} =\begin{bmatrix}
0. 4887180 & 0.3106803 & 0.2006017\\ 0.1762044 & 0.8129847 & 0.0108109 \\ 0.0000000 & 0.0102048 & 0.9897952
\end{bmatrix}\begin{bmatrix}
R \\ G \\ B
\end{bmatrix}$$
e da una versione _normalizzata_ si possono definire le _coordinate cromatiche_ avendo 
$$\begin{array}{}
x=\cfrac{X}{X+Y+Z} \\ y =\cfrac{Y}{X+Y+Z}\\ z =\cfrac{Z}{X+Y+Z} 
\end{array}$$
e con questa _normalizzazione_ abbiamo che $x+y+z=1$ di conseguenza bastano solo due valori per _descrivere_ un colore e il terzo è deducibile dai primi due, infatti si ha $z=1-x-y$ 
![[IMG_0711.png]]

##### CIE xyY
siccome bastano solo due coordiante per specificare un dato colore si comunemente utilizza il sistema _CIE xyY_ che è quindi rapresentabile in 2D e la $Y$ rappresenta l _illuminazione_, presa in considerazione abbiamo in totale una figura 3D 
per tornare al _CIR XYZ_ si usano le formule $$\begin{array}{}
X & = & \cfrac{Y}{y}x \\
Z & = & \cfrac{Y}{y}(1-x-y)
\end{array}$$
