---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Machine Learning (ML)]]"
topic: nota
tags:
  - IA
---

# Modelli lineari con LMS
---
il __modello lineare__ e' un modello parametrico per il [[Concetti generali del Machine Learning|Concetti generali del Machine Learning]] viene generato con algoritmi di [[Apprendimento supervisionato|apprendimento supervisionato]] ed è generalmente il tipo di modello più semplice che si puo provare ad utilizzare per risolvere un problema.

### Univariato 
Si unica con un caso uni variato ovvero abbiamo un unico input $x$ ed un unico output $y$. abbiamo quindi una [[Funzioni|funzione]] del tipo 
$$y = h(x)= w_1x+w_0 + noise $$
dove il vettore $\mathbf{w} \in \mathbb{R}^n$ è  detti di  pesi e questi sono i parametri del modello.  

a livello geometrico  stiamo facendo un _fitting_ con una linea.
![[66B83102-B04B-45D8-805A-4445087275B3.jpeg]]
### Concetti generali 
vogliamo cercare la migliore ipotesi dove per migliore si intende quella che minimizza l errore. lo si fa variando il vettore dei pesi $w$.

$w$ sono variabili continue quindi abbiamo una spazio delle ipotesi $H$ infinito. ma possiamo utilizzare risultati classici della matematica come la [[Discesa di gradiente|discesa di gradiente]].

#### Apprendimento
l _Apprendimento_ definito come una ricerca
- _Dato_ : un Training Set  di $n$ del tipo $(x_p,y_p) \ p=1\dots n$ 
- _Trova_: $h_w(x)$ nella forma $w_1x+w_0$  che minimizza l expected loss sui dati di training
Si definisce una funzione _$Loss$_ come    

$$ Loss(h_w)= E(w)= \sum_{p=1}^n(y_p-h_w(x_p))^2 $$
questa è detta _Least mean square_ (LMS) da la media degli errori quadrati.
>[!note]- perchè si usa il quadrato
>si utilizza il quadrato per rendere i numeri positivi. in piu il quadrato- è [[Funzioni differenziabili|differenziabile]] a differenza del valore assoluto 

minimizzare la $Loss$ significa ridurre la somma  residua degli errori.

possiamo _visualizzarla_ con 
![[D91DA331-B74D-45E5-AACF-DFDC6FC1F1EC.jpeg]]

la pratica di utilizzare LMS è standard per approssimare soluzioni di sistemi sovradeterminati. ovvero dove ci sono più equazioni che incognite. 

per trovare il minimo si cerca dove il gradiente di _Loss_ è $$\frac{\partial E(w)}{\partial w_i} =0 \ \ i =1,\dots,DimInput+1$$
il +1 è per il coefficiente noto

nel caso in cui la funzione di Lost scelta si la [[last Mean Squere (LMS)|Last mean Squere]] abbiamo che questa è una funzione [[Convessità|convesa]] e quindi non ci sono limiti locali e si puo trovare una soluzione diretta.
$$w_1= \frac{\sum x_p y_p- \frac{1}{n}\sum x_p \sum y_p}{\sum x_p^2 - \frac{1}{n}(\sum x_p)^2} = \frac{Cov[x,y]}{var[x]} \ \ \ \  w_0 = \frac{1}{n}\sum y_p- w_1 \frac{1}{n}\sum x_p$$


## Gradient descent (local serach)
una [[Ricerca locale]] per cercare la funzione di $loss$ minima. si  inizia quindi con valori casuali del vettore $w$ e _iterativamente_ si segue la direzione di decrescita di $E(w)$ e quindi si ha che 
$$w_{new } = w +\eta* \Delta w$$
dove 
- $\eta$ è una costante detta _step Size_ che determina il learning rate
- $\Delta w =-$ gradiente di $E(w)$
	- il - è perché si sta cercando un minimo


### Gradient descent univariato
$$
\begin{array}{}
\boldsymbol w_{new} = \boldsymbol w + \eta *\Delta  \boldsymbol w \\
\Delta w_0 = -\frac{\partial E(\boldsymbol w)}{\partial w_0} = 2(y-h_w(x)) \\
\Delta w_1 = -\frac{\partial E(\boldsymbol w)}{\partial w_1} = 2(y-h_w(x))x 
\end{array}
$$
intuitivamente questo procedimento è una _correzione degli errori_ detta “_delta rule_” che cambia $w$ proporzionalmente al errore
- $target - output =err =0$ nessuna correzione 
- $output>target (y-h)<0$ (outuput troppo alto)
	- $\Delta w_0$ negativo __then__ riduci $w_0$
	- __if__($input x>0$) $\Delta w_1$ negative __then__ reduce $w_1$
	- __else__ incrementa $w_1$
- $output>target \rightarrow (y-h)>0$
	- sda


## Gestione di più esempi
si possono gestire più $n$ pattern in due modi 
- _epoca_: si aspetta di avere una certa quantità di dati e si calcola la discesa in _batch_ (linea blu)
	- spostamento più stabile verso un minimo
- _Online_: si ricalcola per ogni nuovo patter $p$ (discensa di gradiente stocastica) (linee verdi e viola)
	- più veloce ma richiede step $\eta$ più piccolo
![[3BC840EA-37CF-4EEC-9C6D-C3EBCCF55566.jpeg]]

## Multi-Variabili
si analizza il caso in cui si utlizza un vettore di input  $\boldsymbol x$  e un vettore di pesi $\boldsymbol w$ 
$$ \boldsymbol w^T \boldsymbol x +w_0 =w_0+w_1x_1 + \dots+w_nx_n = w_0+ \sum^n_{i=1}w_ix_i $$
convenzionalmente si aggiunge un elemento un $1$ al inizio  al vettore $\boldsymbol x$ per poter scrivere 
$$\boldsymbol  w^T\boldsymbol x = \boldsymbol x^T\boldsymbol w$$
$$ \begin{array} 
\boldsymbol x^T = [1,x_1,\dots,x_n] \\
\boldsymbol w^T = [w_0,w_1,\dots,w_n]
\end {array}$$
##### interpretazione geometrica caso 2 variabili
![[B713A224-B169-4617-8A81-4FF5C80BA9CA.jpeg]]


#### Apprendimento multi variabile
l _Apprendimento_ definito come una ricerca
- _Dato_ : un Training Set  di $n$ del tipo $(x_p,y_p) \ p=1\dots n$ 
- _Trova_: il vettore $\boldsymbol w$  che minimizza l expected loss sui dati di training
Si definisce una funzione _$Loss$_ come    
$$ Loss (\boldsymbol w) =E(\boldsymbol w)= \sum_{p=1}^n(y_p-h(\boldsymbol x_p))^2 = \|\boldsymbol  y-\boldsymbol X\boldsymbol w\|_2 $$
dove 
- $h(\boldsymbol x_p) = \boldsymbol x_p^T \boldsymbol w = \sum^n_{i=0}x_{p,i}w_i$
- $\|\cdot\|$ è la [[Norme Matriciali e Norme Vettoriali|norma due]]
### Gradied descent multi-variabile
$$
 \boldsymbol w_{new} = \boldsymbol w + \eta \Delta  \boldsymbol w 
$$dove ogni componente è valutato come
$$ 
\begin{array}{}
\Delta w_i =& -\cfrac{\partial E(\boldsymbol w)}{\partial w_i} &=
\\& \cfrac{\sum^\ell_{p=1}(y_p-h_{\boldsymbol w}(x))}{{\partial w_i}} &=\\
&\cfrac{\sum^\ell_{p=1}(y_p-\boldsymbol x^T\boldsymbol w)}{\partial w_i}&=\\
&-(-2\sum^\ell_{p=1}(y_p-\boldsymbol x^T\boldsymbol w)x_{p,i}) &= \\
&2\sum^\ell_{p=1}(y_p-\boldsymbol x^T\boldsymbol w)x_{p,i}&\\


\end{array}
$$
 e si ha quindi che 
 
 $$\Delta \boldsymbol W = - \frac{\partial E(\boldsymbol w)}{\partial \boldsymbol w} = 
 \begin{bmatrix}
 -  \cfrac{\partial E(w)}{\partial w_2} \\
 -  \cfrac{\partial E(w)}{\partial w_1} \\
  \vdots \\
 - \cfrac{\partial E(w)}{\partial w_n} \\ 
 \end{bmatrix} =
 \begin{bmatrix}
 \Delta w_1 \\
   \Delta w_2 \\
  \vdots \\
  \Delta w_3 \\ 
 \end{bmatrix} 
 $$
 si puo lavorare su uno spazio multi dimensionale senza la necessita di visualizzarlo
 _nota_: qui viene omesso il $w_0$


### Algoritmo
1. inizia con un vettore $\boldsymbol w_{initial}$ e fissa $\eta$ con $0<\eta<1$ 
2. computa $\Delta \boldsymbol w = -\Delta E(\boldsymbol w) = - \cfrac{\partial E(\boldsymbol w)}{\partial \boldsymbol w}$ 
3. computa $\boldsymbol w_{new} = \boldsymbol w+\eta\Delta \boldsymbol w$  
4. ripeti dal passo 2 finche $\boldsymbol w$ converge o $E(\boldsymbol w)$ è _sufficientemente piccolo_   

- $\cfrac{\Delta w}{l}:$ least mean squeres
- _batch version_ : epoche di $\ell$ dati
- _stocastica/on-line versione_: aggiorna $\boldsymbol w$ ad ogni pattern $p$
- $\eta$ = _learning rate\step size_ gestisce il compromesso tra velocita e stabilita
	- può essere lentamente ridotto a 0 come in [[Ricerca Tempra simulata| ricerca a tempra simulata]]

## Example
![[E09B2FF5-EA90-441A-ACFF-24A453C658DD.jpeg]]
_learning curves_: mostrano come l errore decresce con gradient descent nelle iterazioni 


### vantaggi dei modelli lineari 
se questo modello è applicabile ha molti vantaggi 
- è molto semplice
- tutte le informazioni sui dati sono in $\boldsymbol w$
- facile da interpretare 
- i dati perturbati sono permessi
### limitazione del modello lineare
non riesce a gestire problemi più complessi che solitamente non hanno una natura lineare 
![[42E911EA-F4B3-488E-8FCF-A04D54C72CD7.jpeg]]
per gestire questi casi si utilizzano espressioni con dei termini non lineari preservando per la _linearità_ dal modello. ci troviamo in una situazione di _underfittig_
### Relazioni non lineari 
notiamo che in $h_{\boldsymbol w}(\boldsymbol x)= \boldsymbol w^T\cdot \boldsymbol x$ la parte a cui si riferisce il termine _lineare_ non è ai valori di input ma ai coefficienti di regressione $\boldsymbol w$

detto cio si puo espandere il modello  con una relazione non lineare tra input e output. possiamo quindi scrivere 
$$h_{\boldsymbol w}(\boldsymbol x)=w_0+w_1x+w_2x^2+\dots+w_mx^m = \sum^m_{j=0}w_jx^j$$

### Linear basis expansion - generalizzazione
possiamo espandere questo concetto delle relazioni non lineari con qualsiasi tipo di funzione 
$$h_{\boldsymbol w}(\boldsymbol x)= \sum^K_{k=0}w_k\phi_k(\boldsymbol x)$$
dove $\phi_k: \mathbb{R}^n\rightarrow \mathbb{R}$ è una funzione per ogni indice $k$ dove $K>n$ è il numero di parametri  
esempi di  $\phi_k$
- _polinomiale_ : $\phi_k = x^2_j$ or $x_jx_i$ ro $\dots$
- _trasformazioni nonlineari_:
	- _input singolo_:  $\phi_k = log(x_j)$ or $root(x_j)$ ro $\dots$
	- _input vettoriale_ : $\phi_k = \|\boldsymbol x\|$



- _PRO_: è piu espressivo puo esprimere relazioni piu complicate
una buona flessibilità ci permette di dare una buona approssimazione della funzione che cerchiamo 
![[AC48AB1A-F82F-401F-8B56-89876D800471.jpeg]]
- _CONS_: con una larga base di funzioni abbiamo bisogno di metodi per tenere sotto controllo la _complessità_ del modello
troppa flessibilità ci puo portare al fenomeno di _[[Overfitting e Underfiting|overfitting]]_: ovvero si i dati di training abbiamo ridotto a 0. errore ma testando su dati casuali avremmo predizione sbagliate e quindi una bassa _accuracy_
- é molto suscettibile a errori poco perturbati
![[DA592E39-BE09-4F38-B38F-265D19B9C9BF.jpeg]]

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



### Classificazione Binaria
lo stesso modello puo essere usato per la _classificazione_. come prima utilizziamo $\boldsymbol w^T \boldsymbol x$
Geometricamente possiamo vedere la classificazione come un _Iperpiano_

![[D83C8A5E-E4F9-46AD-BDF1-F31C5018F693.jpeg]]
![[F17F5BAE-D1D4-4EF9-8A3B-4BE196FB84FA.jpeg]]
possiamo decidere della classificazione con delle funzioni  utilizzando le _linear threshold unit (LTU)_
$$\begin{array}{}
h(x) = 
\begin{cases}
	1 & if & \boldsymbol w^t \boldsymbol x +w_0 \geq 0  \\ 
	0 & & otherwise
\end{cases} & 
	\begin{array}{}[0,1] \\
	\text{output range}
	\end{array}\\
h(x)= sign (\boldsymbol w^t \boldsymbol x+w_0) & \begin{array}{}[-1,1] \\
\text{output range}
\end{array}

\end{array}
$$
$w_0$ è detto _trashold_ infatti per enfatizzare si può riscrivere la prima _LTU_ come $\boldsymbol w^t \boldsymbol x  \geq -w_0$ 

#### Apprendimento
l _Apprendimento_ definito come una ricerca
- _Dato_ : un Training Set  di $n$ del tipo $(x_p,y_p) \ p=1\dots n$ 
- _Trova_: $h_w(x)$ nella forma $\boldsymbol w$  che minimizza l expected loss sui dati di training
Si definisce una funzione _$Loss$_ come    

$$E(w)= \sum_{p=1}^n(y_p-\boldsymbol x_p^T \boldsymbol w)^2= \|\boldsymbol y-\boldsymbol X\boldsymbol w \|^2 $$
anche in questo caso possiamo usare l algoritmo di _[[#Gradient descent (local serach)|Gradient descent]]_.
l algoritmo puo essere visto come una regola di correzione. se un elemento viene mal classificato si aumentano o diminuiscono i parametri proporzionalmente a $\eta$ 
![[D71CEA55-0B20-46D7-8E28-A7C2F04F3877.jpeg]]
da qui si può espandere con cui che vale nel caso di regressione. quindi si puo utilizzare la [[#Linear basis expansion - generalizzazione| linear basis expansion]]

### Limitazioni 
il confine di decisione da soluzioni esatte solo nei casi i cui i dati siano [[Linearmente Separabili|lineramente separabili]]
![[E0A08BCF-3CA8-42A6-A2F5-076F046AC0AA.jpeg]]
il primo caso e linearmente separabile il secondo _no_

![[F81A15DB-EA14-4C7D-A57B-E0C4601243E8.jpeg]]


### Classificazione multi classe
![[66B634CA-4C7D-40AD-8320-4B2AB892CA13.jpeg]]
![[61A57F54-70BA-4C19-8A62-440555104DD0.jpeg]]