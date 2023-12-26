---
type: nota
course: Analisi
topic: 
tags:
  - Analisi
Parent MOC: "[[Analisi]]"
---
# Quaternioni
---
I _quaternioni_ sono un _estensione_ dei [[Numeri complessi|numeri complessi]] con altre due parti _immaginarie_
sono quindi della forma
$$a_{w}+\boldsymbol{i}a_{x}+\boldsymbol{j}a_{y}+\boldsymbol{k}a_{z}$$
dove $\boldsymbol{i}a_{x},\boldsymbol{j}a_{y},\boldsymbol{k}d_{z}$ sono la parte _immaginaria_, spesso abbreviato come $$a=(a_{w},\boldsymbol{a})$$

l [[Operazioni algebriche|operazione]] di _addizione_ funziona per componenti $$a+b=\begin{bmatrix}
a_{w}+b_{w} \\
\boldsymbol{i}(a_{x}+b_{x}) \\
\boldsymbol{j}(a_{y}+b_{y}) \\
\boldsymbol{k}(a_{z}+b_{z})
\end{bmatrix}
$$

Vale la seguente equazione
$$\boldsymbol{i}^{2}=\boldsymbol{j}^{2}=\boldsymbol{k}^{2}=\boldsymbol{ijk}=-1$$
da cui l [[Operazioni algebriche|operazione]] della  _moltiplicazione_ non è [[Proprietà del operazioni-Commutatività|commutativa]] e quindi valgono le seguenti e uguaglianze $$\begin{array}{}
\boldsymbol{ij}=  & \boldsymbol{k} & &  \boldsymbol{ik}= & - \boldsymbol{j}\\
\boldsymbol{jk}= &  \boldsymbol{i}& &  \boldsymbol{kj}= & - \boldsymbol{i}\\
\boldsymbol{ki}= &  \boldsymbol{j}& &  \boldsymbol{ji}= & - \boldsymbol{k}\\

\end{array}$$
![[IMG_0764.jpeg]]
e quindi  si ga che $$ab=\begin{bmatrix}
a_{w}b_{w}-\boldsymbol{a}\cdot \boldsymbol{b} \\
	a_{w}\boldsymbol{b}+b_{w}\boldsymbol{a}+\boldsymbol{a}\times\boldsymbol{b}
\end{bmatrix}$$

dove l [[Elemento Neutro o identita di un operazione|indentita]] è $\boldsymbol{1}=(1,0,0,0)$ 

l [[Elemento inverso di un operazione|inverso]] è l elemento $$a^{-1}=\frac{1}{\|a\|^{2}}(a_{w},-\boldsymbol{a})$$
il _coniugato_ di un _quaternione_ è
$$\overline{\boldsymbol{q}}=(a_{w},-\boldsymbol a)$$

la _magniduto_ di un quaternione è definita come $$\|a\|=\sqrt{  a_{w}^{2}+a_{x}^2+a_y^2+a_z^2}$$

