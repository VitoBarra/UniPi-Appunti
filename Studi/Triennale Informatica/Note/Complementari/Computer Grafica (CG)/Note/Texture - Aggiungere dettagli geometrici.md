---
Subject: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Texture Mapping]]"
SubTopic:
---

# Texture - Aggiungere dettagli geometrici
---
si puo usare utilizzare delle [[Texture|Texture]] per aggiungere dettagli geometrici agli oggetti senza pero cambiarne davvero la geometria.


![[Pasted image 20240302055351.png]]

#### Displace map
o __displacement map__ è una [[Texture|texture]] a singolo canale e rappresenta un  altezza, Ogni valore viene interpretato come di quanto la superfice corrispondente deve essere spostata seguendo la [[Normale di una superfice|normale]]. per ogni texel c è bisogno di un nuovo [[Computer grafica - Primitive Geometriche|vertice]] 
questo ha bisogno di essere fatto nella [[Pipeline di Rasterizazione|pipeline di rasterizazione]]
![[Pasted image 20240302061214.png]]
#### Bump map
una __Bump map__ è una [[Texture|texture]] a singolo canale e rappresenta un altezza, ogni valore viene usato per interpretare l altezza della superfice e la [[Normale di una superfice|normale]] viene calcolata come se la superfice fosse a quel altezza ma non la effettivamente sposta.
Ogni valore è nel range 0.0 e 1.0 e viene mappato ad un range specificato dal utente
![[Pasted image 20240302060303.png]]
![[Pasted image 20240302060315.png]]

#### Normal Map
una __normal map__ è una [[Texture|texture]] a 3 canali uno per ogni [[Rappresentazione di colori|colore]] RGB, ogni valore contiene il valore di una [[Normale di una superfice|normale]] come se fosse calcolata ad un altezza diversa rispetto alla geometria originale. 
Questo ci permette di utilizzare questa nuova normale al posto di quella originale per mostrare gli effetti di [[Illuminazione nella Computer Grafica|luci]] che desideriamo

Questo pero puo riscontrare dei problemi: Un raggio colpirà un punto della superfice dalla geometria base che non corrisponde a quella della geometria originale, oppure potrebbe intersecare la geometria originale ma mancare la geometria base. 
![[Pasted image 20240302061229.png]]
Questo è un problema di parallase e dipende da quanto è lontano la geometria base dal punti di vista e dal [[Angoli|angolo]] tra il raggio di vista e la geometria base  

#### Parallax Map
una __Parallax map__ è un miglioria della __normale map__ emula l effetto di parallasse. è una [[Texture|texture]] a 1 canali che contiene un  l altezza. Quanto il ray view colpisce un punto e viene restituito punto in texture space a questo viene applicato un offset che dipende dal altezza in modo da stimare il valore corretto dell effettiva geometria
_sia_
- $u$ il punto mappato in texture space
- $h(u)$ il valore di altezza in texture space nel punto $u$
_allora_ il valore effettivamente restituito è $$u_0=u+\cfrac{h(u)}{V_z}V_x$$
![[Pasted image 20240302062933.png]]
Questa funziona bene in casi in cui
- le altezze non cambiano troppo velocemente  M,/\on si è in casi di "Grazing angles" in quel caso l approssimazione si allontana troppo+09.

![[Pasted image 20240302055008.png]]


#### Tangent Space
Una __normal map__ puo essere definita in __Object space__ ovvero nel [[Frames|frame di riferimento]] del oggetto, se cosi definita pero la normal map non puo essere riutilizzata in altri contesti siccome è sta prodotta pensando anche a dove le norme dovessero andare
![[Pasted image 20240302080831.png]]
un modo per poter applicare la __normal map__ a tutte le possibili superfici è l utilizzo di __tanget space__.
un __tange space__ è un altro [[Frames|frame]], e per calcolarlo si procede come
_sia_
- $t$ un punto della texture
- $f(\cdot)$ una funzione che mappa da texture a oggetto
- $p = f(t)$ un punto 
_allora_ il __tangent frame per [[Superfici implicite|superfici analitiche]]__ $T_f$ con origine  $p$  è costruito come$$\begin{array}{}
	\boldsymbol{u}_{os}= \cfrac{\partial f}{\partial u}(t) \\
\boldsymbol{v}_{os}= \cfrac{\partial f}{\partial v}(t) \\
\boldsymbol{n}_{os}= u_{os} \times v_{os}
\end{array}$$in questo modo stiamo costruendo un frame che ha gli assi $X$,$Y$ in un piano tangente alla superfice e l asse $Z$ che \corrisponde alla [[Normale di una superfice|normale]] 
![[Pasted image 20240302080857.png]]
![[Pasted image 20240319020707.png]]
e a questo punto si puo mappare da texture space ad object space come $$\boldsymbol{p}_{os}=T_f \ \boldsymbol{p}_{ts}$$


##### Calcolare il Tanget Frame di una mesh
Per calcolare il __tangent frame__ per [[Mesh Poligonali|mesh poligonali]] si usa la seguente formula
_sia_
- $v_0,v_1,v_2$ dei punti in object space
- $V_f$ un [[Frames|frame]] con $v_0$ come origine e $v_1-v_0$ e $v_2-v_0$ come assi
- $t_0,t_1,t_2$ dei punti in __Texture space__
- $I_f$ un [[Frames|Frames]] con $t_0$ come origine e $t_1-t_0$ e $t_2-t_0$ come assi
allora possiamo calcolare  l asse $\boldsymbol{u}_{os}$ del __tange frame__ come [[Interpolazione di vertici - Coordinate Baricentriche|coordinata baricentrica]] come $$
\boldsymbol{u}_{os}   = normalize(u_1(\boldsymbol{v}_1-\boldsymbol{v}_0)+u_2(\boldsymbol{v}_2-\boldsymbol{v}_0)) $$
con 
$$\begin{align}
u_1  & = \cfrac{(t_0+\boldsymbol{u})-t_0) \times \boldsymbol{t}_{20}}{\boldsymbol{t}_{10}\times \boldsymbol{t}_{20}}=\cfrac{\boldsymbol{u} \times \boldsymbol{t}_{20}}{\boldsymbol{t}_{10} \times \boldsymbol{t}_{20}}=\cfrac{[1,0]^T\times \boldsymbol{t}_{20}}{\boldsymbol{t}_{10}\times \boldsymbol{t}_{20}}=\cfrac{t_{20_v}}{\boldsymbol{t}_{10}\times \boldsymbol{t}_{20}} \\
u_2  & =\cfrac{\boldsymbol{t}_{10}\times((t_0+u)-t_0)}{\boldsymbol{t}_{10}\times \boldsymbol{t}_{20}}=\cfrac{\boldsymbol{t}_{10}\times \boldsymbol{u}}{\boldsymbol{t}_{10}\times \boldsymbol{t}_{20}} =\cfrac{\boldsymbol{t}_{10}\times [1,0]^T}{\boldsymbol{t}_{10}\times \boldsymbol{t}_{20}}=\cfrac{-t_{10_u}}{t_{10}\times t_{20}}
\end{align}$$
quindi $$\begin{align}
u_1   & =\cfrac{t_{20_v}}{\boldsymbol{t}_{10}\times \boldsymbol{t}_{20}} \\
u_2   & =\cfrac{-t_{10_u}}{t_{10}\times t_{20}}
\end{align}$$

![[Pasted image 20240302085513.png]]
nello stesso modo si puo calcolare $\boldsymbol{v}_{os}$ oppure si puo calcolare con il [[Prodotto Vettoriale (Cross product)|Cross product]] come $$\boldsymbol{v}_{os}=\boldsymbol{n} \times \boldsymbol{u}_{os}$$