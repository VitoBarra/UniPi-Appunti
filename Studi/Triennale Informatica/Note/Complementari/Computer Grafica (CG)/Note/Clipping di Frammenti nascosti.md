---
Subject: "[[Computer Grafica (CG)]]"
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