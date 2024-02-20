---
Course: "[[Computer Grafica (CG)]]"
Subject: Computer Grafica
Area: 
Topic: 
SubTopic: 
tags:
  - CG
---

# Trasformare da Vertici a Frammenti (Rasterizazione)
---
Il Processo di trasformazione da geometria in pixel (Rasterizazione) avviene fatto sulla __View Port__ ovvero dopo che la geometria in __[[Proiettare una scena sullo schermo#World Space|word space]]__ viene mappata sul View Port,
quindi questo processo avviene dopo che la geometria viene [[Proiettare una scena sullo schermo|proiettata sullo schermo]] 

Siccome la __View Port__ ha Coordinate _discrete_ si pone il problema di scegliere quali frammenti della geometria (che e' espressa in spazzi continui) devono essere effettivamente disegnati sulla __View Port__


Questo processo e' detto di "Rasterizazione" delle [[Computer grafica - Primitive geometriche|primitive geometriche]]
### Rasterizazione delle primitive
Rasterizazione dei punti
![[IMG_0784.jpeg]]

Rasterizazione delle _linee_
l Algoritmo di _renderizzazione_ di una linea passante da due punti dipende dallo _slope_ della [[Retta|retta]] ovvero dal suo _coefficiente angolare_ calcolato come$$m=\frac{y_{1}-y_{0}}{x_{1}-x_{0}}$$
e vale che $$\begin{cases} 
\begin{cases}
y=y_{0}+m(x-x_{0})  \\
x =x+1
\end{cases} & if & m \in  [-1,1]\\
\begin{cases}
x=x_{0}+\frac{1}{m}(y-y_{0})\\
y=y+1
\end{cases} & else
\end{cases}$$dove gli $=$ sono assegnamenti. 
L algoritmo garantisce che  tutti i pixel della _linea_ sono _adiacenti_
![[IMG_0783.jpeg]]
![[IMG_0782.jpeg]]


### Eliminazione di Superfici non visibili
Se la scena ha molto primitive e' probabile che possa succedere che non tutte siano visibili contemporaneamente e questo puo succedere per 3 ragioni:
1. __occlusion culling__: sono interamente o parzialmente occluse da un altra primitiva
	 - Serve un algoritmo di __Hidden surface removal__ (HSR) che ci permette di evitare di rasterizzare le superfici coperte
2. __Frustum culling__: Sono totalmente fuori dal Frustum 
	- Si evita completa di rasterizzarle 
3. __clipping__: Sono solo parzialmente al interno del frustum
	- Si deve rasterizzare solo la parte al interno del frustum
![[Pasted image 20240214020332.png]]
#### Hidden Surface Removal (HSR)
Un algoritmo di questo tipo serve a rimuovere le superfici di primitive che sono coperte da altre primitive.

##### Algoritmo del pittore 
l Idea di base e' quella di disegnare a partire dal oggetto piu lontano in modo che gli oggetti piu vicini re-scrivano i pixel degli oggetti piu vicini.
Serve un modo per ordinare gli oggetti in ordine "Back-to-Front" ovvero dal piu distante al piu vicini. 
Questo si calcolando la distanza tra l osservatore e il baricentro del triangolo 
![[Pasted image 20240214022109.png]]
Il problema di questo algoritmo e che il baricentro non e' una misura corretta siccome se il baricentro di $A$ e' piu vicino al osservatore rispetto al baricentro di $B$ non significa che tutta la primitiva $A$ sia piu vicina al osservatore rispetto a tutta la primitiva $B$

##### Depth Sort
Il __Depth Sort__ e un [[Algoritmi|algoritmo]] di Hidden Surface Removal (HSR) che utilizza le idee di base del __algoritmo del pittore__ la differenza sta nel modo di ordinare le primitive.

per ordinare le primitive si cercano dei __[[Linearmente Separabili|Piani di separazione]]__ tra le primitive.
Se esiste un piano di separazione allora possiamo concludere che le primitive dal un lato del piano sono piu vicine o piu lontane rispetto a quelle del altro lato.

Ci sono diversi casi da considerare, Siano $A$ e $B$ due primitive vogliamo cercare i piani di separazione
1. Se  $A$ e $B$ non hanno _punti di sovrapposizione_ sul [[Applicazione lineare - Proiezione|proiezione]] sul asse $z$ allora esiste sempre un piano tra i due parallelo agli assi $xy$ e con $z$ tra $A$ e $B$. Quindi l ordinamento e' triviale
2. se $A$ e $B$ hanno _punti di sovrapposizione_ sul [[Applicazione lineare - Proiezione|proiezione]] sul asse $z$ ma non sulla proiezione o su $x$ o su $y$, allora si possono sempre trovare di _piani di separazione_ paralleli a $x$ o a $y$  siccome anche se sono alla stessa distanza questi non interferiscono l uno con l altro. Non c e' bisogno di fare sort
3.  se $A$ e $B$ si cercano i _piani di separazione_, Se il ViewPoint e la primitiva $A$ (o $B$) sono sullo stesso lato del piano allora la primitiva $A$ (o $B$) e' piu vicina
	- Se le primitive sono [[Convessità|poligoni convessi]] che non intersecano allora esiste sempre un __piano di separazione__ che passa per una primitiva
![[Pasted image 20240214022806.png]]
Non sempre si puo trovare un ordine corretto, esisto dei casi in cui le primitive devono essere clippate per essere ordinate correttamente. questo succede quando
1. Ci sono intersezioni
2. Ci sono cicli nel ordinamento
![[Pasted image 20240214023309.png]]


l algoritmo dipende dal punto di osservazione (ViewPoint) e quindi  le [[Strutture Dati|strutture dati]] usate per efficientare questo algoritmo devono essere aggiornate allo spostamento del __ViewPoint__ 


>[!Warning]-
>Questo Algoritmo deve essere eseguito prima di mandare le primitive nella [[Pipeline di Rasterizazione|Pipeline di Rasterizazione]] quindi nella CPU, ma le coordinate dei vertici in __view space__ si sanno solo dopo la trasformazione cosa che avviene GPU nella pipeline 
>![[Pasted image 20240214031348.png]]

#### Z-Buffer
utilizzare lo __z-Buffer__ e' lo standard defacto per l __hidden surface removal_ (HSR)_.

Durante la rasterizazione si scrive su un buffer i valori della $z$ che normalmente andrebbero ignorati. Questi vengono poi usati successivamente per decidere la distanza dal osservatore di ogni singolo pixel.


il buffer viene inizializzato alla distanza massima visibile ovvero al __far plane__ e siccome questo processo avviene nel [[Proiettare una scena sullo schermo|NDC]] abbiamo che $z=1$ e poi si sovrascrive per ogni pixel il valore piu piccolo.

l algoritmo segue come 
```pseudo
	\begin{algorithm}
	\caption{hidden surface Removal}
	\begin{algorithmic}
	\Function{ZbuufferAlgorithm}{}
		\For{$\boldsymbol{each} \ i,j$} 
			\State Zbuffer[$i,j$] = 1.0
	    \EndFor
		\For{$\boldsymbol{each}$ primitive $pr$}
			\For{$\boldsymbol{each}$ pixel $(i,j)$ covered by pr}
				\If{Z[i,j] < Zbuffer[i,j]}
					\State ZBuffer[i,j]=Z[i,j]
				\EndIf
			\EndFor
		\EndFor
    \EndFunction
	\end{algorithmic}
	\end{algorithm}
```
I vantaggio di questo alogirtmo e' che e' molto semplice e siccome le primitive sono processate per pixel e' altamento paralelizabili, siccome questi sono indipendenti.

![[Pasted image 20240214031511.png]]![[Pasted image 20240214031546.png]]


![[Pasted image 20240214031628.png]]


##### Precisione del Z-Buffer e Z-Fighting
la tecnica dello Z-Buffer soffre del problema della granularità con cui si indica la capacita di distinguere valori diversi di $z$
Infatti puo succedere che nel processo di proiezione e rasterizazione si perdano le razioni di profondità tra due valori, ovvero puo succedere che due valori $z_a$ e $z_b$ con $z_a<z_b$ vengano mappati nello stesso valore nello Z-buffer, questo avviene per via del [[Aritmetica di Macchina|aritmetica di machina]] che e' finita e introduce imprecisioni.

lo Z-buffer mantiene i suoi valori con una rappresentazione in __fixed precision__ ovvero la precisione e' definita a priori e, presi due valori consecutivi $a$ e $b$ si ha che $$|a-b| =\epsilon \ \ \forall a,b$$dove $\epsilon$ e' detta __precisione__  e rappresenta la loro distanza tra due valori consecutivi. 
sia $k$ il numero di bit per valore del buffer abbiamo che ogni valore e' salvato come intero nel range $[0,2^k-1]$  e per fare in modo che lo Z-buffer rappresenti solo valori tra $[0,1]$ si divide per $\cfrac{1}{2^k-1}$ e si ha che la __precisione dello Z-buffer__ e' proprio $\epsilon =\cfrac{1}{2^k-1}$      


La coordinata $z$ di un vertice in [[Proiettare una scena sullo schermo#View Volume|View space]] e' rappresentata con un __[[Rappresentazione in base di numeri reali|floating point]]__, questa viene mappata in  [[Proiettare una scena sullo schermo#View Volume|Normalized Device Coordinate]] che hanno range $[-1,1]$  e poi viene a sua volta mappata nei valori dello Z-buffer che hanno range $[0,1]$, Si definisce la funzione che opera questo mapping come $$f(z): View \ space \to Depth \ buffer \ space$$
questa e' diversa nei casi di [[Proiettare una scena sullo schermo#Proiezione ortografica|proiezione ortografica]] $$f_o(z)=\frac{1}{2}\left( \frac{-2}{f-n}-\frac{f+n}{f-n}+1 \right)$$e [[Proiettare una scena sullo schermo#Proiezione prospettica|proiezione prospettica]] 
$$f_p(z)=\frac{1}{2}\left( \frac{f+n}{f-n}-\frac{2fn}{z(f-n)}+1 \right)=\frac{1}{2}\left( \frac{f+n}{f-n}+1 \right)-\frac{fn}{z(f-n)}$$
  
la funzione $f_o(z)$  e' della forma $az+b$ ovvero e' il mapping e' uno scaling e una traslazione e quindi e' un [[Equazioni Lineari e Lineari omogenee|mapping lineare]] 
la funzione $f_p(z)$ e' della forma $\cfrac{a}{z}+b$ ovvero il mapping e' proporzionale a $\cfrac{1}{z}$ il che la rende non lineare.



Siccome La coordinata $z$ di un vertice in [[Proiettare una scena sullo schermo#View Volume|View space]] e' rappresentata con un __[[Insieme dei numeri di macchina|floating point]]__ si avrà che coordinate vicino lo zero consecutive avranno una distanza l una dal latra molto piccola che potrebbe essere inferiore alla precisione $\epsilon$ dello Z-buffer e quindi quei valori di $z$ diversi tra loro verranno mappati nello stesso valore nello Z-buffer. Questo fenomeno e' chiamato __Z-Fighting__
nel caso della proiezione prospettica non essendo un mapping lineare questo fenomeno e' ancora di piu accentuato e si avrà che il $30\%$ delle coordinate in [[Proiettare una scena sullo schermo#View Volume|View space]] occuperà l $80\%$ dei valori dello Z-buffer, in pratica la capacita di discernere tra due coordinate $z$ diverse degrada al crescere di $z$   
  ![[Pasted image 20240215150753.png]]
  l effetto grafico di questo e' il seguente 
  ![[Pasted image 20240215032403.png]]
![[Pasted image 20240215032412.png]]

###### Soluzione allo z-Fighting
una soluzione e usare piu piani near e far
![[Pasted image 20240215185633.png]]

o fare del offset dei poligoni per far "vincere" la primitiva che ci interessa
![[Pasted image 20240216005229.png]]