---
Course: "[[Computer Grafica (CG)]]"
Subject: Computer Grafica
Area: 
Topic: 
SubTopic: 
tags:
  - CG
---

# Composizione di rotazioni 3D
---
un use-case comune è quello di _comporre piu [[Rotazioni in 3D|rotazioni]]_, per descrivere una rotazione finale. per fare ciò ci sono varie metodologie.

#### Rotazione con angoli euleriani
un modo per esprimere delle _rotazione_ come composizione di rotazioni è l utilizzo degli _angoli di euler_, per immaginarli si usa la _gimbal_, questo è composto da  3 anelli $r_{1},r_{2},r_{3}$ _concentrici_ uno collegato al altro e hanno la libertà di girare.  Ogni anello è rappresentato da un  [[Frames|frame]] $F_{1},F_{2},F_{3}$ 
Ogni _anello_ corrisponde ad un _asse_ e una rotazione del anello corrisponde a fare una rotazione attorno al corrispettivo asse.
le rotazioni sono espresse da 3 angoli $\alpha,\beta,\gamma$ dove
- $\alpha$ ad una rotazione intorno a _asse_ X chiamata _yaw_
- $\beta$ ad una rotazione intorno al _asse_ Y chiamata _pitch_
- $\gamma$ ad una rotazione intorno al _asse_ Z chiamata roll
![[IMG_0770.jpeg]]
se gli _angoli_ $\alpha=\beta=\gamma=0$ allora i [[Frames|frame]] $F_{1},F_{2},F_{3}$ coincidono con il _frame canonico_ $\mathcal{C}$.
ogni _frame_ è collegato al precedente infatti abbiamo che $$
\begin{array} \\
F_{1} & = & R_{x,\alpha}\mathcal{C} \\
F_{2} & = & R_{y,\beta}R_{x,\alpha}\mathcal{C}\\
F_{3} & = & R_{z,\gamma}R_{y,\beta}R_{x,\alpha}\mathcal{C}
\end{array}
$$quindi _applicare_ una rotazione ad una anello le applica anche a tutti i _sottostanti_ e in questo caso si parla di rotazioni _intrinseche_: ![[IMG_0771.jpeg]]
non ci fosse questa gerarchia si parlerebbe di rotazioni _estrinseche_ e ogni _frame_ sarebbe rappresentato da una rotazione direttamente sul _[[Frames|frame canonico]]_ $$\begin{array} \\
F_{1} & = & R_{x,\alpha}\mathcal{C} \\
F_{2} & = & R_{y,\beta}\mathcal{C}\\
F_{3} & = & R_{z,\gamma}\mathcal{C}
\end{array}$$
> [!info]
> gli _assi_ usati,  _ordine di applicazione della rotazione_ sui 3 assi, e rotazioni _intrinseche_ o _estrinseche_ sono __convenzioni__ 

il _mapping_ tra gli _angoli_ e la _rotazione finale_ è 
- una [[Funzioni|funzione surrigettiva]] quindi ogni _rotazione_ è raggiungibile 
- ma __non__ è una _[[Funzioni|funzione iniettiva]]_ quindi  si puo raggiungere la stessa rotazione usando diversi _angoli_
 quindi non è [[Funzioni|bigettiva]]
Una conseguenza di questo è il __gimbal lock__ che è un _caso degenere_ dove si _perde un grado di liberta_, nel senso che in questo modo muovere due assi risulta nella rotazione attorno allo stesso _asse_ . Abbiamo che
_se_ $\beta=\frac{2}{\pi}$ 
_allora_ tutti i valori di $\alpha$ e $\gamma$ tale che $\alpha=-\gamma$ danno la stessa _rotazione finale_ 

![[IMG_0758.jpeg]]
quando questo caso va preso in considerazione

#### Rotazioni con quaternioni 
un [[Quaternioni|quanternione]] $q=(0,x,y,z)$ rappresenta un _punto_ nello spazio $(x,y,z)$

considerando il _[[Quaternioni|quaternione]]_ _unitario_ $$q=\left( \cos \frac{\alpha}{2} ,\sin \frac{\alpha}{2}\boldsymbol{r}\right)$$ con $\|\boldsymbol{r}\|=1$ questo rappresenta un rotazione di tipo [[Rotazioni in 3D#Rotazione intorno ad un asse approccio geometrico|asse-angolo]]  dove i parametri $\boldsymbol{r}$ e $\alpha$ sono i parametri.

 un [[Quaternioni|quaternione]] _puro_ fatto come $\boldsymbol{p}=(0,p_{x},p_{y},p_{z})$ puo interpretato come un _punto_ in posizione  $p_{x},p_{y},p_{z}$   ed essendo un _quaternione_ puo essere moltiplicato con il _quaternione unitario_ per _ruotare_ un _punto_ attorno al asse $r$ usando la seguente formula $$\mathbf{p}’=q\mathbf{p}q^{-1}$$

Questa formula va _dimostrata_ e con i seguenti passaggi $$\begin{array}{}
 & q\mathbf{p}q^{-1}    \\
 = & \left( \cos \frac{\alpha}{2},\sin \frac{\alpha}{2}\boldsymbol{r} \right)(0,\boldsymbol{p})\left( \cos \frac{\alpha}{2},-\sin \frac{\alpha}{2}\boldsymbol{r} \right) \\
  = & \left( \cos \frac{\alpha}{2},\sin \frac{\alpha}{2}\boldsymbol{r} \right)\left( \sin \frac{\alpha}{2}(\boldsymbol{p}\cdot\boldsymbol{r}),\cos \frac{\alpha}{2}\boldsymbol{p}-\sin \frac{\alpha}{2}(\boldsymbol{p}\times\boldsymbol{r}) \right) \\
  = & \left( 0,\left( \cos ^{2} \frac{\alpha}{2} -\sin^{2} \frac{\alpha}{2}\right)\boldsymbol{p}+2\sin^{2} \frac{\alpha}{2}\boldsymbol{r}(\boldsymbol{p}\cdot\boldsymbol{r}) +2\sin \frac{\alpha}{2}\cos \frac{\alpha}{2}(\boldsymbol{p}\times\boldsymbol{r})\right)
\end{array}
$$ e _applicando le seguenti_ [[Formule Trigronometriche|formule trigonometriche]]  $$\begin{array}{}
\cos^{2}\frac{\alpha}{2}-\sin ^{2}\frac{\alpha}{2}=\cos \alpha \\
2\sin ^{2} \frac{\alpha}{2}=(1-\cos \alpha) \\
2\cos \frac{\alpha}{2}\sin  \frac{\alpha}{2}=\sin \alpha
\end{array}$$
ottieniamo la tesi.


con i [[Quaternioni|quaternioni]] possiamo concatenare piu rotazioni siccome moltiplicare piu _quaternioni unitario_ che (rappresentano una rotazione) restituisce un _quaternione unitario_ che corrisponde alla rotazione voluta.
_Infatti_ si ha che 
_siano_$$
\begin{array}
\boldsymbol{q}=\boldsymbol{q}_4\boldsymbol{q}_3\boldsymbol{q}_2\boldsymbol{q}_1 \\
\boldsymbol{\overline{q}}=\boldsymbol{\overline{q}}_1\boldsymbol{\overline{q}}_2\boldsymbol{\overline{q}}_3\boldsymbol{\overline{q}}_4
\end{array}
$$
_allora_ le due espressioni $$\begin{array}{}
\boldsymbol{ q}\mathbf{p}\boldsymbol{ \overline{q}}
 \\ \\
\boldsymbol{q}_4\boldsymbol{q}_3\boldsymbol{q}_2\boldsymbol{q}_1 \mathbf{p}\boldsymbol{\overline{q}}_1\boldsymbol{\overline{q}}_2\boldsymbol{\overline{q}}_3\boldsymbol{\overline{q}}_4
\end{array}$$rappresentano la stessa rotazione


##### Conversione ad altri sistemi
_Conversine_ rotazione [[Rotazioni in 3D|angolo-asse]]$$\begin{array}{}
\alpha=2\arctan(a_{w},\boldsymbol{a}) \\
\boldsymbol{r}= \frac{\boldsymbol{a}}{\|\boldsymbol{a}\|}
\end{array}$$
_Conversine_ con Matrici di rotazione
![[IMG_0785.jpeg]]

##### Vantaggi
i [[Quaternioni|Quaternioni]]  si usano nelle rotazioni siccome sono
- _più veloci da moltiplicare_ siccome hanno meno [[Rappresentazione in base di numeri reali|floating point]] della [[Prodotto tra matrici|moltiplicazione tra matrici]] 
- Quindi anche  piu [[Tipi di Errore nel calcolo numerico|stabili numericamente]] 
- Sono ottimi per l [[Interpolazione di Rotazioni|Interpolazione tra rotazioni]]
- possono essere convertiti ad altri _sistemi di rotazione_
sono pero più difficili da _capire_.
 



