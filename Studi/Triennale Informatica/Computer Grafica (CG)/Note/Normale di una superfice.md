---
Course: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Illuminazione nella Computer Grafica]]"
SubTopic:
---

# Normale di una superfice
---
_Sia_
- $S$ una [[Superfici|superfice]]
- $\boldsymbol{p}$ un punto della superfice $S$
- $P$ il piano tangente alla superfice $S$ al punto $\boldsymbol{p}$
allora la __normale__ al punto $\boldsymbol{p}$ è un [[Vettori|vettore]] unitario $\boldsymbol{n}_p$ [[Rette perpendicolari|perpendicolare]] a $P$



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
$$fare questa trasformazione  non è sempre necessario, nei casi in cui la [[Trasformazioni Geometriche|trasformazione affine]] 
- preserva __lunghezze e [[Angoli|angoli]]__ non serve fare la trasformazione
- preserva gli __[[Angoli|angoli]]__ ma NON le lunghezze non serve fare la trasformazione ma bisogna normalizzare il risultato
![[Pasted image 20240228061926.png]]

