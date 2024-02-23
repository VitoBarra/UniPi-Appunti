---
Subject: "[[Computer Grafica (CG)]]"
Area: 
topic: 
SubTopic: 
tags:
  - CG
---


# Color Space Relativi
---
mentre i [[Color Space Assoluti standard|color space assoluti]] rappresentano tutti i colori possibili questi non tengono conto di come _riprodurli fisicamente_ tramite un dispositivo, per fare ciò si usano i _Color Space Relativi_ che sono dei [[Color Space|color space]] che dipendono dal dispositivo e contengono solo un _sottoinsieme_ dei colori percettibili, l area dei colori che sono possibili in output da un dato dispositivo è chiamato _Gamut_.    questi sono mappati sul _diagramma cromatico_ del _CIEXYZ_
![[IMG_0712.jpeg]]
 ogni diverso _gamut_ prende calori primari diversi rappresentati dai vertici e i colori raggiungibili sono diversi e rappresentati in modo diverso in ogni _color space_.

##### Conversione tra Gamut
si puo sempre passare da un _gamut_ al altro finché il sistema di riferimento è fissato. 
infatti fissata la rapresentazione _[[Color Space Assoluti standard|CIEXYZ]]_ che è assoluta si puo prima convertire i valori di un _color space relativo_ al  _color space assoluto_ per poi riconvertire nel nuovo _color space relativo_ che si basa sullo stesso _color space assoluto_   



#### HSL e HSV
Alcuni _color space relativi_ comunemente usati sono l _Hue Saturation lightness_ (_HSL_) e _Hue Saturation Value_ (_HSV_) che cercano di dare un senso piu intuitivo al modo di rappresentare i colori.
infatti  
- lo _Hue_ rappresenta il colore base indicato _gradi_
- _Saturation_ rappresenta la “_densita di colore_” 
- _Lightness_ rappresenta la lucentezza del colore
- _Value_ rappresenta un altro valore di lucentezza.
![[IMG_0717.jpeg]]

##### Conversione sRGB to HSL/HSV
sono riportate le formule di conversione tra il [[Color Space|Color Space]] _sRGB_ al Color Space _HSL/GSV_

_sia_ $M=\max\{R,G,B\}$ , $m=\min\{R,G,B\}$ e $\Delta=M-m$ 
_allora_ la regola conversione per _HSL_ segue come
$$
\begin{array}{}
H & = & \begin{cases}
  undefined  & if &  \Delta =0 \\
  60°\left( \frac{G-B}{\Delta} \right)  & if  & M=R \\
60°\left( \frac{B-R}{\Delta} \right)+ 120°  & if  & M=G \\
60°\left( \frac{R-G}{\Delta} \right) + 240°  & if  & M=B 
\end{cases}  \\ 
S & = & \begin{cases}
0 & if & \Delta=0 \\
\cfrac{\Delta}{1-|2L-1|} &  else & s\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \
\end{cases} \\
L & = & \cfrac{M+m}{2} \\
 \\
\end{array}
$$
mentre per la conversione in _HSV_ si ha $$\begin{array}{}
S & = & \begin{cases}
0  & if & \Delta=0 \\
\cfrac{\Delta}{V} & else  & 
\end{cases} \\
V & = & M
\end{array}$$
mentre l _hue_ $(H)$ resta uguale.

#### CIELab
Il _CIElab_ è un [[Color Space|color space]] _relativo_ sviluppato dalla _CIE_ e le coordinate di questo Color space sono solitamente indicate con $L^{*}$ che indica la _lucentezza_ e. $a^{*} , b^{*}$  indicano la cromaticità del colore.
In questo sistema la distanza tra due colori è espressa dalla formula della _distanza euclidea_ $$\Delta Lab=\sqrt{ (L_1^*-L_2^*)^{2}+ (a_{1}^*-a_{2}^*)^{2}+(b_{1}^*-b_{2}^*)^{2}}$$e due _colori distanti_ con questa metrica sono effettivamente colori percepiti come diversi e due _colori vicini_ sono percepiti come lo stesso colore o simile, questo non necessariamente succede in altri [[Color Space|Color Space]]


##### Conversione CIRXYZ to CIELab
_siano_ $X_{n},Y_{n},Z_{n}$ dei fattori di normalizzazione dipendenti dagli [[Rappresentazione di colori - illuminanti|Rappresentazione di colori - illuminanti]]
_allora_ le formule di conversione sono$$
\begin{array}
L^{*} & = & 116f(X/X_{n})-16 \\
a^{*} & = & 500f(X/X_{n})-f(Y/Y_{n}) \\
b^{*} & = & 200f(Y/Y_{n})-f(Z/Z_{n})
\end{array}
$$
dove $$f(x)=\begin{cases}
	\sqrt[3]{ x }  &  x>0.008856 \\
7.787037x +0.137931& else 
\end{cases}$$
