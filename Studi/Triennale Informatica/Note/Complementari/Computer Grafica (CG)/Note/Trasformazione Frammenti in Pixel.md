---
Subject: "[[Computer Grafica (CG)]]"
Area: 
topic: 
SubTopic: 
tags:
  - CG
---

# Trasformazione Frammenti in Pixel
---
una volta fatta la [[Trasformare da Vertici a Frammenti (Rasterizazione)|trasformazione da vertici a frammenti]] avremo dei  __frammenti__ che sono dei pixel quindi il colore arricchiti con dei valori aggiuntivi.
Per ogni frammento si dovranno fare le  [[Pipeline di Rasterizazione|per-fragment operation]].

#### Discard Test
In ordine di esecuzione sono


__Scissor Test__: serve per scrivere in un rettangolo specifico nello schermo creando uno schermo nello schermo. Tutti i frammenti al di fuori di quel rettangolo vengono ignoranti e quindi si puo scrivere in quel rettangolo senza toccare ciò che e' fuori.
![[Pasted image 20240216133044.png]] 
Questo é utile siccome ci sono molti casi dove si vorrebbe cambiare un pezzo di UI o far partire un semplice animazione e si vuole evitare di ridisegnare l intera scena, cosa non necessaria se questa non e' cambiata

__Stentcil Test__: lo Stentcil test é un test su un buffer che ci permette di ignorare alcuni frammenti, Questo puo essere utile quando alcune parti dello schermo sono fisse e si vuole mascherare tutto quello che occuperebbe lo stesso posto perché verrebbero comunque coperti da un altro oggetto, in questo modo si evita di sprecare computazione su pixel che verranno comunque sicuramente buttati.
![[Pasted image 20240216133959.png]]
Per fare cio si usa lo __Stencil buffer__ che é  un buffer di $1$ e $0$ , se c é  un 1 si ignorano i frammenti delle coordinate corrispondenti.


__Depth Test__: si utilizza lo Z-buffer per cancellare gli oggetti coperti.
![[Pasted image 20240216134035.png]]

![[Pasted image 20240216135855.png]]


#### Blending
Se un frammento passa tutti i __discard test__ allora possono succedere due cose, 
- sostituisce interamente il colore gia presente sul buffer 
- contribuisce al colore finale ovvero fa "blending" di colore

Il blending deve essere abilitato e permette di mischiare due colori, questo puo essere utile per modellare superfici non completamente opache.

Sia 
- $s=[s_R,s_G,s_B,s_{\alpha}]^T$ il [[Color Space|colore]] del frammento detto __source__ 
- $d=[d_R,d_G,d_B,d_{\alpha}]^T$ il [[Color Space|colore]] gia sul buffer detto __destinazione__ 
- $\boldsymbol{b},\boldsymbol{c}$ dei __Fattori di blending__
allora il colore risultante e' una [[Combinazioni Lineari|combinazione lineare]] dei due $$d'= 
\underbrace{ \begin{bmatrix}
b_R \\b_G \\b_B \\b_{\alpha}
\end{bmatrix} }_{ b }
\begin{bmatrix}
s_R \\s_G \\s_B \\s_{\alpha}
\end{bmatrix}
+
\underbrace{ \begin{bmatrix}
c_R \\c_G \\c_B \\c_{\alpha}
\end{bmatrix} }_{ c }
\begin{bmatrix}
d_R \\d_G \\d_B \\d_{\alpha}
\end{bmatrix}$$
i fattori $b,c$ possono essere variati per implementare diversi effetti.
![[Pasted image 20240216140058.png]]

###### Superfici trasparenti
L utilizzo piu comune per il blending é  l utilizzo per modellare superfici trasparenti.
si renderanno le primitive __Back-to-Front__ e ogni volta che si renderizza una superfice trasparenti si fa __blending__ per calcolare il contributo dei colori gia presenti  utilizzando l __alpha channel__ per discriminare quanto "colore" passa $$b'= 
\underbrace{ \boldsymbol{\begin{bmatrix}
s_{\alpha} \\s_{\alpha} \\s_{\alpha} \\s_{\alpha}
\end{bmatrix} } }_{ b }
\begin{bmatrix}
s_R \\s_G \\s_B \\s_{\alpha}
\end{bmatrix}
+
\underbrace{ \begin{bmatrix} 
1-s_{\alpha}\\1-s_{\alpha} \\1-s_{\alpha} \\1-s_{\alpha}
\end{bmatrix}  }_{ c }
\begin{bmatrix}
d_R \\d_G \\d_B \\d_{\alpha}
\end{bmatrix}
$$
l alpha della colore di destinazione non é mai usato, questo funziona perché é gia sul buffer quindi sarà gia stato applicato

### Aliasing e  Anti-Aliasing
con il nome __Aliasing__ ci si riferisce al fatto che siccome stiamo approssimando una rappresentazione in coordinate reali con delle coordinate discrete puo succedere che segmenti diversi possono essere mappati negli stessi pixel, infatti una data lineea puo essere mappata dai infiniti segmenti, e senza una conoscenza a priori non possiamo sapere a quale segmenti la linea si riferisce.
![[Pasted image 20240216143210.png]]
L effetto visivo di cio e' l avere delle linee dentellate chhe non danno l effetto di essere un effettiva linea ma ci sono delle tecniche dette di __anti-aliasing__ che mitigano questo effetto. 
![[Pasted image 20240216143230.png]]


##### Area averaging thecnique
si interseca una retta di spessore $1$ con i pixel e poi si utilizza l area di intersezione per decidere quanto l intensita del [[Color Space|colore]] deve essere altra, se solo meta del pixel e coperto dal poligono allora l intensita sara ridotta della meta, e cosi via.
calcolare l intersezione pero richiede molte  operazioni floating point e  questo bisognerebbe evitarlo.

##### Super sampling anti aliasing (SSAA)
la tecnica di Anti-Aliasing di super Sampling consiste nel renderizare la scena in un framebuffer piu grande e poi fare l average per calcolare il valore vero da mettere nel framebuffer della dimensione giusta.
![[Pasted image 20240216143243.png]]
Questo funziona ma costa molto in memoria infatti, se si usa un sample $n \times n$ costerà $n^2$ volte la memoria che sarebbe servita normalmente

##### Multi sampling anti-Aliasing (MSAA)
per ogni pixel si utilizzano piu "sample" ovvero piu punti dello stesso pixel oltre al centro, se almeno un punto e' coperto dalla primitiva allora il framento si attiva con un intensita del colore proporzionale al numero di sample coperti
![[Pasted image 20240216143254.png]]
questo richiede solo piu memoria per il depth buffer e lo stencill buffer.


#### Back Face Culling
nei casi in cui la scena e' fatta di mash chiuse e non si puo "entrare" nelle mesh possiamo evitare di renderizare le __back face__, ovvero le facie la cui normale punta nella direzione opposta al osservatore.
![[Pasted image 20240216145801.png]]

Per identificare una __back face__ si calcola la norma.
sia $\boldsymbol{p}_0,\boldsymbol{p}_1,\boldsymbol{p}_2$ un triangolo proiettato nel __near plane__
allora calcolando la norma suoi punti proiettati $\boldsymbol{p}_{0_{xy}},\boldsymbol{p}_{1_{xy}},\boldsymbol{p}_{2_{xy}}$  calcolata come $$N=(\boldsymbol{p}_{1_{xy}}-\boldsymbol{p}_{0_{xy}})
\times (\boldsymbol{p}_{2_{xy}}-\boldsymbol{p}_{0_{xy}})$$
- Se positiva allora __front face__
- se negativa __back Face__

![[Pasted image 20240216150116.png]]
e questo calcolo e' fatto prima della [[Trasformare da Vertici a Frammenti (Rasterizazione)]]
![[Pasted image 20240216150054.png]]
la mesh non deve essere necessariamente chiusa, ma deve smembrarlo. un terreno non e' una mesh chiusa ma se non possiamo andare sotto e' come se lo fosse
![[Pasted image 20240216150906.png]]

#### Clipping
Non ha senso Renderizare parti che non sono nel view Frostum, quindi si fa cplipping delle parti che sono al difuori
![[Pasted image 20240216151115.png]]


##### Cohen-Sutherland
il rettangolo di clip é  definito come l intersezione di 4 piani allineati.
questo divide il piano in 9 quadranti. e ogni quadrante é  marcato con un codice a 4 bit.
a questo punto basta generare questo codice per ogni coordinata
![[Pasted image 20240216151523.png]]
un test puo generare il Bit Code dove $R(p)=b_{+y}(p)b_{-y}(p)b_{+x}(p)b_{-x}(p)$ dove $$\begin{array}{}
b_{+x}(\boldsymbol{p}) = \begin{cases}
1  &  \boldsymbol{p}_x>x_{max} \\
0 & \boldsymbol{p}_x \leq x_{max} 
\end{cases} & b_{-x}(\boldsymbol{p}) = \begin{cases}
1  &  \boldsymbol{p}_x<x_{min} \\
0 & \boldsymbol{p}_x \geq x_{min} 
\end{cases}  \\

b_{+y}(\boldsymbol{p}) = \begin{cases}
1  &  \boldsymbol{p}_y>y_{max} \\
0 & \boldsymbol{p}_y \leq y_{max} 
\end{cases} & b_{-y}(\boldsymbol{p}) = \begin{cases}
1  &  \boldsymbol{p}_y<y_{min} \\
0 & \boldsymbol{p}_y \geq y_{min} 
\end{cases}
\end{array} 
$$
questo bit code ci permette di scrivere  un test di discar 
1. $R(\boldsymbol{p}_0)\ \land \ R(\boldsymbol{p}_1) \not =0 \implies$ nessun tagli da fare, il segmento é furi dal area.
2.  $R(\boldsymbol{p}_0)\ \lor \ R(\boldsymbol{p}_1)  =0 \implies$ nessun tagli da fare, il segmento é  interamente nel area
se entrambi falliscono si calcola l intersezione con l area e si mantiene solo dove interseca

##### Liang-Barsky
per fare clipping si usa l equazione parametrica
$$s(t)=\boldsymbol{p}_0=t(\boldsymbol{p}_1-\boldsymbol{p}_0)=\boldsymbol{p}_0+t\boldsymbol{v}$$ e si utilizzano i punti di intersezione tra la linea e il piano
$$(\boldsymbol{p}_0-\boldsymbol{v}t)_x=x_{min} \implies t =\frac{x_{min}-p_{0_x}}{\boldsymbol{v}_x}$$
![[Pasted image 20240216151552.png]]