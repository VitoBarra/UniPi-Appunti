---
Course: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Illuminazione nella Computer Grafica]]"
SubTopic:
---

# Normale di una superfice parametrica
---
La **normale** di una [[Superfici|superficie]] è un [[Vettori|vettore]] perpendicolare ad un punto su di una [[Superfici|superficie]], formalmente si ha che:  
Sia  
- $S$ una [[Superfici|superficie]] 2-[[Manifolds (Varieta)|manifold]] $\subset \mathbb{R}^3$  
- $S(u,v): \mathbb{R}^2 \to \mathbb{R}^3$ una [[Superfici parametriche|parametrizzazione]] dello spazio 3D  
- $\mathbf{p} = S(u,v)$ un punto sulla superficie  
- $\mathbf{x}_u, \mathbf{x}_v$ i due [[vettori|vettori]] in corrispondenza di $\mathbf{p}$ nello [[Spazio Tangente (Tangent space)|spazio tangente]], che definiscono il piano tangente $P$ in $\mathbf{p}$  
allora la __normale__ in $\mathbf{p}$ è definita come $$\mathbf{n}_p = \cfrac{\mathbf{x}_n \times \mathbf{x}_v}{\|\mathbf{x}_u\times \mathbf{x}_v\|}$$ dove $\times$ è il [[Prodotto Vettoriale (Cross product)|prodotto vettoriale]].  $\mathbf{n}_p$ è un [[Vettori|vettore]] unitario [[Vettori Ortogonali|ortogonale]] al piano tangente $P$
![[IMG - Normale di una superfice.png]]

Esistono però dei casi limite in cui questa definizione non è applicabile, ossia quando  $$
\mathbf{x}_u \times \mathbf{x}_v = \mathbf{0},
$$cioè i due vettori tangenti sono [[Dipendenza Lineare|linearmente dipendenti]]. In tali punti il piano tangente non è ben definito e la normale non esiste. 
un esempio è il bordo di un cilindro:
![[IMG - caso limite definizione normale in superfice parametrica.png]]











#### Trasformazioni della normale
_sia_
- $p$ un punto
- $u$ un vettore tangente a $p$
- $n$ la __normale__ al punto $p$
allora i due vettori $n$ e $u$ sono [[Vettori Ortonormali|ortonormali]] e quindi vale che $$\boldsymbol{n}^T\boldsymbol{u}=0$$
siccome le  [[Trasformazioni Lineari Geometriche|trasformazione affine]]  in generiche non preservano angoli e lunghezze non è garantito che applicando una [[Trasformazioni Lineari Geometriche|trasformazione affine]] $M$  si abbia che $$(M\boldsymbol{n})^T(M\boldsymbol{u})=0$$e quindi la norma andrebbe trasformata in modo da mantenerla perpendicolare alla superfice trasformata. Questo si ottiene con i seguenti passi logici $$\begin{align}

\boldsymbol{n}^T\boldsymbol{u}  =0 \implies &   \boldsymbol{n}^TM^{-1}M\boldsymbol{u}  =0 \\
\implies  &  (\boldsymbol{n}^TM^{-1})(M\boldsymbol{u})  =0
\end{align}
$$ e quindi la nuova normale $n'$ è calcolata come $$
\begin{align}
n{'}^{T}=(\boldsymbol{n}^TM^{-1})  &  \implies \boldsymbol{n}'=(\boldsymbol{n}^TM^{-1})^T \\
 & \implies \boldsymbol{n}'=M^{-1^T}\boldsymbol{n}
\end{align}
$$fare questa trasformazione  non è sempre necessario, nei casi in cui la [[Trasformazioni Lineari Geometriche||trasformazione affine]] 
- preserva __lunghezze e [[Angoli|angoli]]__ non serve fare la trasformazione
- preserva gli __[[Angoli|angoli]]__ ma NON le lunghezze non serve fare la trasformazione ma bisogna normalizzare il risultato
![[Pasted image 20240228061926.png]]

