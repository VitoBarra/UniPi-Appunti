---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Machine Learning (ML)]]"
topic: nota
tags:
  - IA
---
# Modelli lineari con LMS
---
il __modello lineare__ e' un [[Modelli di machine learning parametrici|modello parametrico]] per il [[Concetti generali del Machine Learning|Macchine learning]]. 
Viene generato con algoritmi di [[Algoritmi di apprendimento supervisionato|apprendimento supervisionato]] ed è generalmente il tipo di modello più semplice che si può provare ad utilizzare per risolvere un problema.

Per __modello lineare__ si intende lineare nei parametri e non nel input. 

### Modello lineare uni variato 
il modello più semplice di __modello lineare__ è quello uni-variato dove abbiamo un unico input $x$ ed un unico output $y$.

__Sia__
- $x$ l' input del modello
- $w_0,w_1 \in \mathbb{R}$ parametri del modello, detti pesi
__allora__ il __modello lineare__ è definito dalla [[Funzioni|funzione]] che rappresenta una [[Retta|retta]]  
$$y = h_w(x)= w_1x+w_0$$
Questo __modello__ ha uno [[Algoritmi di apprendimento supervisionato|spazio delle ipotesi]]  $\mathcal{H}$ di dimensione infinita questo siccome $w_0,w_1$ sono parametri in continuo e si possono quindi esprimere infinite $h_w$ diverse.

Vogliamo cercare l'ipotesi che riesce ad approssimare meglio i dati che si hanno e per fare ciò dobbiamo variare i pesi $w_0,w_1$.

dal punti di vista geometrico stiamo facendo __fitting__ dei dati con una retta
![[66B83102-B04B-45D8-805A-4445087275B3.jpeg]]

l'[[Algoritmi di Machine Learning|algoritmo di learning]] per questo modello è definito come minimizzazione di una certa [[Algoritmi di apprendimento supervisionato|funzione di Loss]]. In questo caso utilizza la  __[[last Mean Squere (LMS)|Least mean square]]__ (LMS)  ovvero la media degli errori quadrati 
l'algoritmo segue quindi come: 
__Sia__
- $TR$ un __Training Set__  di $\ell$  esempi 
- $Loss(h_w)$ la funzione di loss definita come$$Loss(h_w)= E(w)= \sum_{p=1}^\ell(y_p-h_w(x_p))^2=\sum_{p=1}^\ell(y_p-w_1x_p-w_0)^2 $$
__Trova__ $h_w(x)$ che minimizza la funzione di $Loss$ sui dati nel  $TR$

si utilizza l LMS perché Il quadrato rende tutti gli errori, ovvero $y_p-h_w(x_p)$, positivi e perché è anche funzione [[Funzioni differenziabili|differenziabile]] 

in questo caso minimizzare la $Loss$  significa ridurre la somma residua degli errori e possiamo _visualizzarla_ con 
![[D91DA331-B74D-45E5-AACF-DFDC6FC1F1EC.jpeg]]

>[!tip]-
> la pratica di utilizzare LMS è standard per approssimare soluzioni di sistemi sovradeterminati. ovvero dove ci sono più equazioni che incognite. 

Per trovare la $Loss$ minima c è bisogno di cambiare i valori dei parametri $w_0,w_1$ e i valori ottimi possono essere trovato  ponendo  $$\frac{\partial E(w)}{\partial w_1} =0 \ \ \frac{\partial E(w)}{\partial w_0} =0$$ovvero facendo la classica ricerca dei [[Massimi e minimi|minimi]] del [[Analisi|analisi]]. 
In questo caso la funzione di $Loss$ è la  [[last Mean Squere (LMS)|Last mean Squere]] che è essendo [[Convessità|convessa]] ci garantisce che __se__ esiste un minimo questo è unico ed è quello globale.  
![[Pasted image 20241119224228.png]]
In questo caso specifico la soluzione può anche essere calcolata direttamente come 
$$w_1= \frac{\sum x_p y_p- \frac{1}{n}\sum x_p \sum y_p}{\sum x_p^2 - \frac{1}{n}(\sum x_p)^2} = \frac{Cov[x,y]}{var[x]} \ \ \ \  w_0 = \frac{1}{n}\sum y_p- w_1 \frac{1}{n}\sum x_p$$
e questa è esattamente la [[Retta di regressione|retta di regressione]] infatti nel pratico stiamo facendo la stessa cosa che fa la retta di regressione.



un altro approccio è il __Gradient descent__ ovvero una [[Ricerca locale]] per cercare il minimo della funzione di $Loss$  in modo iterativo. 
Si inizia con valori casuali del vettore $w$ e __iterativamente__ si segue la direzione di decrescita di $E(w)$ e questa è indicata con $\Delta\mathbf{w} = -\cfrac{\partial E(\mathbf{w})}{\partial \mathbf{w}}$ a quindi si ha che 
$$w_{new } = w -\eta\Delta\mathbf{w}$$
dove $\eta$ è una costante detta __Learning rate__ che determina la velocita con cui ci si sposta nella direzione di decrescita.
Si puo calcolare $\Delta \mathbf{w}$ come:
$$\begin{array}{}
\Delta w_0 = -\cfrac{\partial E(\boldsymbol w)}{\partial w_0} = 2(y-h_w(x)) \\
\Delta w_1 = -\cfrac{\partial E(\boldsymbol w)}{\partial w_1} = 2(y-h_w(x))x 
\end{array}
$$
intuitivamente questo procedimento è una _correzione degli errori_

> [!info]- delta Rule (vai a capire perché è qui, probabilmente è sbagliata)
> detta “_delta rule_” che cambia $w$ proporzionalmente al errore
>- $target - output =err =0$ nessuna correzione
>- $output>target (y-h)<0$ (outuput troppo alto)
>	- $\Delta w_0$ negativo __then__ riduci $w_0$
>	- __if__($input x>0$) $\Delta w_1$ negative __then__ reduce $w_1$
>	- __else__ incrementa $w_1$
>- $output>target \rightarrow (y-h)>0$
>	- sda

##  Modello lineare Multi-Variabili
Per i modelli __lineari multi variati__ si ha che li input non è una singola variabile ma un [[Vettori|vettore]]  $\boldsymbol x \in \mathbb{R}^n$ il modello assegna ad ogni input un certo peso tramite in vettore $\mathbf{w} \in \mathbb{R}^n$ , per poter esprimere il bias $w_0$ per convenzione viene aggiunto un $1$ come primo elemento al vettore di input $\mathbf{x}$  ottenendo quindi:$$ \begin{flalign} 
\mathbf{x}^T &= [1,x_1,\dots,x_n] \\
\mathbf{w}^T &= [w_0,w_1,\dots,w_n]\\
\mathbf{w}^T\mathbf{x} &= \mathbf{x}^T\mathbf{w}
\end {flalign}$$
in questo modo il modello è definito semplicemente dal [[Prodotto Scalare|inner poduct]] dei due vettori$$  \mathbf{w}^T \mathbf{x} =w_0+w_1x_1 + \dots+w_nx_n = \sum^n_{i=1}w_ix_i $$con $n=2$ l interpretazione geometrica è semplice è un piano che ne interseca un altro formando una retta ovvero l ipotesi $h_{\mathbf{w}}$ del modello lineare.
![[B713A224-B169-4617-8A81-4FF5C80BA9CA.jpeg]]
In generale immaginarlo per $n>2$ è difficile ma il concetto di intersezione per generare una retta resta ma c è bisogno di usare gli iperpiani.



l'[[Algoritmi di Machine Learning|algoritmo di learning]] per questo modello come per la versione con una variabile è definito come minimizzazione di una certa [[Algoritmi di apprendimento supervisionato|funzione di Loss]]. In questo caso utilizza la  __[[last Mean Squere (LMS)|Least mean square]]__ (LMS)  ovvero la media degli errori quadrati 
l'algoritmo segue quindi come: 
__Sia__
- $TR$ un __Training Set__  di $\ell$  esempi 
- $\|\cdot\|_2$ è la [[Norme Matriciali e Norme Vettoriali|norma due]]
- $\mathbf{x}_p \in \mathbb{R}^n$ è l input composto da $n$ feature
- $X \in \mathbb{R}^{\ell \times n}$ è la matrice che rappresenta tutto il training set
- $Loss(h_w)$ la funzione di loss definita come$$Loss(h_w)= E(w)= \sum_{p=1}^\ell(y_p-h_w(x_p))^2 = \sum_{p=1}^\ell(y_p-\mathbf{x}_p^T\mathbf{w})^2= \|\mathbf{y}-\mathbf{X}\mathbf{w}\|_2$$
__Trova__ $h_w(x)$ che minimizza la funzione di $Loss$ sui dati nel  $TR$


Anche in questo caso esiste una soluzione diretta ottenibile ponendo il gradiente a $0$ ovvero $$\cfrac{\partial E(\mathbf{w})}{\partial \mathbf{w}}=0$$e sapendo che $$\cfrac{\partial E(\mathbf{w})}{\partial w_j}=-2\sum^\ell_{p=1}x_{p,j}(y_p-\mathbf{x}_p^T\mathbf{w})  = 0\ \ \ \ \forall j =0\dots n$$ da cui riscrivendo sotto forma matriciale otteniamo che  $$\cfrac{\partial E(\mathbf{w})}{\partial w_j}=-2\mathbf{X}^T_j(\mathbf{y}-\mathbf{X}\mathbf{w})=0$$e considerando tutto il vettore $\mathbf{w}$ si ha che $$\cfrac{\partial E(\mathbf{w})}{\partial \mathbf{w}}=-2\mathbf{X}^T(\mathbf{y}-\mathbf{X}\mathbf{w})=0$$ e da qui semplificando si arriva all' __[[Equazione normale|equazione normale]]__$$(\mathbf{X}^T\mathbf{X})\mathbf{w}=\mathbf{X}^T\mathbf{y}$$ e si ha che __se__ $(\mathbf{X}^T\mathbf{X})$ risulta [[Matrice inversa|invertibile]] allora la soluzione è __unica__ ed è data da $$\mathbf{w}=(\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T\mathbf{y} =\mathbf{X}^+\mathbf{y}$$ dove $\mathbf{X}^+$ è detta [[Moore-Penrose pseudoinversa|Moore-Penrose pseudoinversa]] che esiste anche se $\mathbf{X}$ non è [[Matrice inversa|invertibile]]  __altrimenti__ le soluzioni sono infinite e si puo scegliere $\mathbf{w}= \arg_\mathbf{w}\min  \|\mathbf{w}\|$. 

Per motivi di efficienza questa equazione puo essere risolta direttamente tramite [[Singular Value Decomposition (SVD)|Singular Value Decomposition]] che ci dice che$$\mathbf{X}=\mathbf{U}\mathbf{\Sigma}\mathbf{V}^T\implies \mathbf{X}^+=\mathbf{V}\mathbf{\Sigma}^+\mathbf{U}^T$$ dove 
- $\mathbf{U} \in \mathbb{R}^{\ell \times \ell}$ è una [[Matrici ortogonali e ortonormali|matrice ortogonale]] e le sue colonne __vettori singolare sinistri__
- $\mathbf{\Sigma} \in \mathbb{R}^{\ell \times n}$ è una [[Matrici quadrate|matrice diagonale]] e $\mathbf{\Sigma}^+$ la stessa matrice dove ogni valore non $0$ è sostituita con il reciproco
- $\mathbf{V} \in \mathbb{R}^{n\times n}$ è una [[Matrici ortogonali e ortonormali|matrice ortogonale]] e le sue colonne __vettori singolare destri__
 


Mentre l' approccio [[Ricerca locale|locale]] con __Gradient descent__ utilizza il gradiente per muoversi verso il minimo seguendo la regola di aggiornamento$$
 \boldsymbol w_{new} = \boldsymbol w + \eta \Delta  \boldsymbol w 
$$dove $\eta$ è il __learning rate__ e $\nabla \mathbf{w} = -\cfrac{\partial E(\boldsymbol w)}{\partial \mathbf{w}}$ e ogni  del gradiente componente è valutato come
$$ 
\begin{array}{}
\Delta w_i  
&=& \cfrac{\partial E(\boldsymbol w)}{\partial w_i}  
&=&
\cfrac{\partial\sum^\ell_{p=1}(y_p-h_{\boldsymbol w}(x))}{{\partial w_i}} &=\\  
&=& 
\cfrac{\partial\sum^\ell_{p=1}(y_p-\boldsymbol x^T\boldsymbol w)}{\partial w_i} 
&=&
-2\sum^\ell_{p=1}(y_p-\boldsymbol x^T\boldsymbol w)x_{p,i} &= \\
&=& -2\sum^\ell_{p=1}(y_p-\boldsymbol x^T\boldsymbol w)x_{p,i}&\\
\end{array}
$$
 e si ha quindi mettendo assieme si ha che$$\Delta \mathbf{w} = - \frac{\partial E(\mathbf{w})}{\partial \boldsymbol w} = 
 \begin{bmatrix}
 -  \cfrac{\partial E(\mathbf{w})}{\partial w_0} \\
 -  \cfrac{\partial E(\mathbf{w})}{\partial w_1} \\
  \vdots \\
 - \cfrac{\partial E(\mathbf{w})}{\partial w_n} \\ 
 \end{bmatrix} =
 \begin{bmatrix}
 \Delta w_0 \\
   \Delta w_1 \\
  \vdots \\
  \Delta w_n \\ 
 \end{bmatrix} 
 $$
![[Pasted image 20241120020901.png]]

Da cui si può derivare il seguente algoritmo di learning
1. inizia con un vettore $\boldsymbol w_{initial}$ e fissa $\eta$ con $0<\eta<1$ 
2. computa $\Delta \boldsymbol w = -\Delta E(\boldsymbol w) = - \cfrac{\partial E(\boldsymbol w)}{\partial \boldsymbol w}$ 
3. computa $\boldsymbol w_{new} = \boldsymbol w+\eta\Delta \boldsymbol w$  
4. ripeti dal passo 2 finche $\boldsymbol w$ converge o $E(\boldsymbol w)$ è _sufficientemente piccolo_   

il  __learning rate\step size__ $\eta$ gestisce il compromesso tra velocita e stabilita e può essere lentamente ridotto a 0 come in [[Ricerca Tempra simulata| ricerca a tempra simulata]]

Plottando l'errore che cambia con le varie iterazioni possiamo osservare 3 tipi di curve principali dipendenti principalmente dal iperparamentro $\eta$
![[E09B2FF5-EA90-441A-ACFF-24A453C658DD.jpeg]]
si ha infatti che
- con $\eta$ "giusto": si ottiene la __rossa__ dove c è una veloce convergenza e la curva è stabile
- con $\eta$  troppo piccolo: si ottiene la curva __verde__ dove la convergenza è molto lenta
- con $\eta$  troppo grande: si ottiene la curva __blu__ dove l'errore è instabile e non c è convergenza 


### limitazione del modello lineare
non riesce a gestire problemi più complessi che solitamente non hanno una natura lineare 
![[42E911EA-F4B3-488E-8FCF-A04D54C72CD7.jpeg]]
per gestire questi casi si utilizzano espressioni con dei termini non lineari preservando per la _linearità_ dal modello. ci troviamo in una situazione di __underfittig__


## Regolarizzazione
per gestire il problema della troppa complessità si utilizzano dei metodi di regolarizzazione 

il generale si segue il concetto che una funzione più semplici probabilmente è quella più adatta. un istanza del _[[rasoio di Occam|rasoio di Occam]]_

### Tikhonov regulation (ridge regression)
quindi si _penalizzano_ modelli molto complessi ridefinendo la funzione $loss$
$$Loss(h_{\boldsymbol w}) = \sum^n_{p=1}(y-h_{\boldsymbol w}(\boldsymbol x))^2 + \lambda \|\boldsymbol w\|^2$$
dove $\lambda$ è chiamato _coefficiente di regolarizzazione_
cosi facendo si penalizzano modelli con troppi parametri siccome il numero di parlamentari aumenta il valore di $\|\cdot\|$. il peso di questo incremento è regolato con $\lambda$
da questo si deriva  
$$ \boldsymbol w_{new}=\boldsymbol w+\eta \Delta w -2\lambda \boldsymbol w$$
>[!tip]- passaggi
>$$\begin{array}{}
>	w_{i_{new}} = w_i -\left(\eta\frac{\partial E(\boldsymbol w)}{\partial w_1}+\lambda \frac{\sum_iw_i^2}{\partial w_i}\right) = \\
>	w_i-\left(\eta\frac{\partial E(\boldsymbol w)}{\partial w_i}+2\lambda w_i\right) = \\
>	\boldsymbol w_{new} + \boldsymbol w + \eta\Delta \boldsymbol w -2 \lambda \boldsymbol w
> \end{array}
>$$


![[699010A3-BDF9-4731-A7A6-95035CE746BE.jpeg]]
![[979A48FD-374F-4C66-9375-3193E3A68437.jpeg]]
![[6F9AE7B2-61F8-4881-9ADC-58CC7A779FC6.jpeg]]
![[BC07443A-5E21-4529-98B5-ADA899DFBF02.jpeg]]
![[57D9815C-9DA5-4A1B-85E7-26709932D31A.jpeg]]






## Bias induttivo

- __Bias di linguaggio__: Il modello ha lo spazio del ipotesi $\mathcal{H}$ lo spazio delle __funzioni lineari__. 
- __Bias di ricerca__: La ricerca delle soluzioni è guidata dall'obiettivo di minimizzare l'errore tramite il criterio dei minimi quadrati (Least Squares).  