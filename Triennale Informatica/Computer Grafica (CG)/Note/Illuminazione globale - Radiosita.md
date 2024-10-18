---
Course: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Illuminazione nella Computer Grafica]]"
SubTopic: "[[Illuminazione globale]]"
---

# Illuminazione globale - Radyosity
---
La tecnica della __radiosita__ è una tecnica di [[Illuminazione globale|illuminazione globale]] che serve ad approssimare la luce ambientare in caso di superfici diffusive, ovvero ad approssimare l integrale dell [[Illuminazione - Equazione di Radianza|equitazione di rendering]]


Si basa su due assunzioni
- La scena si puo dividere in piccole patch
- i pezzi sono piatti e [[Superfice lambertiana|totalmente diffusive]] 

![[IMG_1118 1 1.jpeg]]
la quantità di luce è calcolata in [[Illuminazione - Radiometria#Irradiance e exitance|radiosita]]  siccome questa non dipende dalla direzione. infatti ognuna di queste patch è considerato come un emettitore di [[Illuminazione - Tipi di fonte di luce|luce ad area]] 
- primaria: se il pezzo originale viene da un effettiva sorgente
- secondaria: se riflette la luce arrivata dagli altri patchs. 
ma anche come un receiver. Serve quindi calcolare la quantità di flux che va da un pazzo ad un altro.


#### Form factor
Il form factor esprime la quantità di __[[Illuminazione - Radiometria]]__ che va da un __patch__ $j$ ad una __patch__ $i$  

 Partendo dal equazione della [[Illuminazione - Tipi di fonte di luce|luce ad area]] si arriva a dire quando flux in un singolo punto $x$ arriva da $j$  $$\Phi_x=\cfrac{\Phi_J}{A_j}\int _{A_j}\cfrac{\cos \theta_x \cos \theta_y}{\pi r^2}V(x,y) \, dA_j$$ con  $$V(x,y)=
 \begin{cases}
1  & if  \text{ x is visible from } y \\
0  & altrimenti
\end{cases}$$ una funzione di visibilità. 

Per calcolare tutta l area che arriva sulla path bisogna integrare e quindi $$\Phi_j=\cfrac{\Phi_j}{A_j}\int_{A_i}  \int_{A_j} \cfrac{\cos \theta_x \cos \theta_y}{\pi r^2}V(x,y)   \, dA_j  \, dA_i $$ e con un passo si ottiene il rapporto tra il flux in arrivo al area $A_i$ e il flux che parte dal area $A_j$  e questo è indicato come
$$F_{j \to i}=\cfrac{\Phi_j}{\Phi_j}=\cfrac{1}{A_j}\int_{A_i}  \int_{A_j} \cfrac{\cos \theta_x \cos \theta_y}{\pi r^2}V(x,y)   \, dA_j  \, dA_i$$
e vale la relazione $$F_{j\to i}A_j = F_{i \to j}A_i$$ 
#### Radiosity
Con il __form factor__ possiamo scrivere che il flux sulla superficie $i$ si puo calcolare come 
_sia_
- $\Phi^e_i$ la parte emissiva
- $\rho$ l albedo del materiale [[Superfice lambertiana|diffusivo]]
- $F_{j\to i}$ il form factor 
_allora_
$$\Phi_i =\Phi^e_i + \rho_i\sum^n_{i=0}F_{j \to i}\Phi_j$$
e puo essere riscritto in termi di [[Illuminazione - Radiometria#Irradiance e exitance (Radiosita)|radianza]] usando la relazione $E=\cfrac{\Phi}{A}$ valida nel caso in cui il flusso di flux sia omogenno e usando la relazione $\cfrac{F_{j \to i}}{A_i}=\cfrac{F_{i \to j}}{A_j}$ e quindi vale $$E_i=E_i^e + \rho_i\sum^n_{i=0}F_{i \to j}E_j$$

e questa puo essere riscritta come [[Sistemi lineari e lineari omogenei|Sistemi lineari]] in forma matriciale considerando $\boldsymbol{MA}=\boldsymbol{B}$ con $\boldsymbol{A}$ le incognite $E_i$ e $\boldsymbol{B}$ la componente emissiva $E^e_i$. Si vuole trovare la soluzione $\boldsymbol{A} = \boldsymbol{M}^{-1}\boldsymbol{B}$    ma siccome la matrice puoi essere molto grande anche per scene molto semplici e quindi si utilizzano [[Metodi Iterativi per soluzioni di sistemi lineari|metodo iterativi]] per trovare la soluzione  ad esempio [[Metodo di  gauss-seidel (metodo di spostamento simultanei)|Metodo di  gauss-seidel]]
![[IMG_1120 1 1.jpeg]]


#####  Rendering
Si calcola per ogni patch ra __radiosità__ e si scrive nel vertice la media della __radiosità__ dei triangoli che condividono quel vertice.

Successivamente si interpola tra i vertici per calcolare la radiosità corretta, Cosi facendo stiamo facendo [[Illuminazione - Shading|Graud shading]]
![[IMG_1123 1 1.jpeg]]


#### Contro
- Ha bisogno di una tasselizazione completa  che non sempre è banale da fare
	- questa è anche fatta a priori quindi non si tasselizare di piu una zona dove sarebbe utile a dare risultati miglior
- La tasselizazione influenza il risultato finale 
- è output Insensitive ovvero non dipende da dove lo guardiamo e dobbiamo risolvere l intero problema



