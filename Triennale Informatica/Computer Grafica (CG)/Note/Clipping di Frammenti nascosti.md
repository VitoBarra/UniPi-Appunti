---
Course: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Pipeline di Rasterizazione]]"
SubTopic: "[[Trasformazione Frammenti in Pixel]]"
---

# Clipping di Frammenti nascosti
---
nella fase della [[Pipeline di Rasterizazione|pipeline di rasterizazione]] di  [[Trasformazione Frammenti in Pixel|trasformazione di frammenti in pixel]] con __clipping__ ci siferisce al fatto che è uno spreco di risorse renderizare parti che non sono nel [[Trasformare da Vertici a Frammenti (Rasterizazione)|view Frostum]], quindi si tagliano delle parti che sono al difuori di questo
![[Pasted image 20240216151115.png]]


##### Cohen-Sutherland
il rettangolo di clip é  definito come l intersezione di 4 half-space, ovvero di spazzi divisi da un piano
i 4 piani dividono l intero piano il piano in 9 quadranti. e ogni quadrante é marcato con un codice a 4 bit
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
\end{array} $$ ovvero esprimono se il punto è nel lato positivo del half-space.
Se sia $p_1$ che $p_0$ risultano nel lato positivo dello stesso  half-space allora il piano che lo definisce è detto piano di separazione e il segmento  è sicuramente fuori dal l’aria   

$R(\boldsymbol{p})$ ci permette di scrivere un test di discar infatti abbiamo che per controllare se un segmento definito dai due end point  $\boldsymbol{p}_0$ e $\boldsymbol{p}_{1}$, con $\&$ l  __and bitwise__ e $|$ l __or bitwise__  si ha che 
1. $R(\boldsymbol{p}_0)\ \& \ R(\boldsymbol{p}_1) \not =0 \implies$ nessun tagli da fare, il segmento é furi dal area.
2. $R(\boldsymbol{p}_0)\ | \ R(\boldsymbol{p}_1)  =0 \implies$ nessun tagli da fare, il segmento é  interamente nel area
se entrambi falliscono significa che il segmento non è totalmente nel area e nessuno dei piani è di separazione, di conseguenza si calcola l intersezione con un piano so sostituisce  l endo point con il punto di intersezione e si riesegue il test 



##### Liang-Barsky
per fare __clipping__ si usa l [[Curve parametriche||equazione parametrica]]
$$s(t)=\boldsymbol{p}_0=t(\boldsymbol{p}_1-\boldsymbol{p}_0)=\boldsymbol{p}_0+t\boldsymbol{v}$$ con $t\in [0,1]$e si calcolano i punti di intersezione  tra la linea e uno dei piani che definire il clip volume  come
$$(\boldsymbol{p}_0-\boldsymbol{v}t)_x=x_{min} \implies t =\frac{x_{min}-p_{0_x}}{\boldsymbol{v}_x}$$
Ora sostituendo $t$ nella definizione possiamo trovare tutti i punti di intersezione per tutti i piani.

seguendo un segmento sulla direzione $v$ si ha che si possono incontrare in ordine corescente rispetto a $t$  i punti di intersezione con i piani. 
I punti di intersezione possono essere di __exit__ o di __entry__ del clipping volume, Infatti seguendo l ordine di incontro dei punti si ha che 
-  se la $x$ dei punti unterseca un  piano __verticale__ e si passa da un half-space positivo ad un half-space negativo si ha un __entery__ altrimenti un __exit__
-  se la $y$ dei punti unterseca un piano __orizontale__  e si passa da un half-space positivo ad un half-space negativo si ha un __entery__ altrimenti un __exit__
![[Pasted image 20240216151552.png]]
A questo punto per controllare se un segmento è nel clip volume si prendo due valori del parametro $t$ $$\begin{array}{}
t_{min} & = & \max(0,t_{\text{Largest entry}}) \\
t_{max}  & = & \min(1,t_{\text{Smalest exit}})
\end{array}$$ in questo modo sarà mantenuto solo il segmento con $t \in [t_{min},t_{max}]$  o equivalentemente si ha che $\boldsymbol{p}_0=s(t_{min})$ e $\boldsymbol{p}_1 =s(t_{max})$ 
e se sia ha che $t_{min}>t_{max}$ allora non ci sono intersezioni  
