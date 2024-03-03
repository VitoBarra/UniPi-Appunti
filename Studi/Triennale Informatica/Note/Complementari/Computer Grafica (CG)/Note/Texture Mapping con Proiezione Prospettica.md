---
Subject: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Texture Mapping]]"
SubTopic:
---

# Texture Mapping con Proiezione Prospettica
---
con la [[Proiettare una scena 3D in 2D|proiezione prospettica]] che NON è una [[Trasformazioni Geometriche affini|trasformazione affine]] abbiamo che gli attributi sui vertici che mantengono le coordinate in __texture space__ verranno mappati correttamente ma siccome una trasformazione non affine non preserva le distanza tra punti l'[[Interpolazione Lineare|interpolazione lineare]] tra questi generanno degli artefatti con il  [[Texture Mapping|texture mapping]]
![[Pasted image 20240301070104.png]]
![[Pasted image 20240301070119.png]]
per risolvere questi problema si utilizza l __interpolazione iperbolica__

_sia_
- $d$ la distanza tra l origine è il projection plane
allora $$p'=
\begin{pmatrix}
\alpha'a'+\beta'b \\1
\end{pmatrix}=
\begin{pmatrix}
\alpha'\cfrac{a}{a_z/d}+\beta'\cfrac{b}{b_z/d} \\1
\end{pmatrix}=
\begin{pmatrix}
\cfrac{\alpha'}{w_a}a+\cfrac{\beta'}{w_b}b \\1
\end{pmatrix}$$
e utilizzando il fatto delle [[Coordinate omogenee|coordinate omogeene]] che $$\begin{bmatrix}
a \\ 1
\end{bmatrix} =
\begin{bmatrix}
\lambda a \\ \lambda
\end{bmatrix}  \ \ \ \ \forall \lambda \not=0$$ e quindi possiamo moltiplicare per qualsiasi cosa e in particolare possiamo scegleire $\cfrac{1}{\cfrac{\alpha'}{w_a}+\cfrac{\beta'}{w_b}}$ ottenendo $$
p'=
\begin{pmatrix}
\cfrac{\alpha}{w_a}a+\cfrac{\beta'}{w_b}b \\1
\end{pmatrix}

\cfrac{1}{\cfrac{\alpha'}{w_a}+\cfrac{\beta'}{w_b}}=

\begin{pmatrix}
\cfrac{\cfrac{\alpha}{w_a}}{\cfrac{\alpha'}{w_a}+\cfrac{\beta'}{w_b}}a+\cfrac{\cfrac{\beta'}{w_b}}{\cfrac{\alpha'}{w_a}+\cfrac{\beta'}{w_b}}b\\ \\
\cfrac{1}{\cfrac{\alpha'}{w_a}+\cfrac{\beta'}{w_b}}
\end{pmatrix}$$
le parti che moltiplicano $a$ e $b$ sommano sempre ad 1 e quindi sono [[Interpolazione di vertici - Coordinate Baricentriche|coordinate baricentriche]] e vale che $$t_{p'}=\cfrac{\alpha'\cfrac{t_a}{w_a}+\beta'\cfrac{t_b}{w_b}}{\alpha'\cfrac{1}{w_a}+\beta'\cfrac{1}{w_b}}$$
rappresneta la giusta coordinata in __texture space__ e un altro modo per esprimerlo è $$t_{p'}=\alpha'\begin{bmatrix}
t_a\\1
\end{bmatrix}+\beta'
\begin{bmatrix}
t_b \\ 1
\end{bmatrix}= \alpha'\begin{bmatrix}
t_a/w_a \\ 1/w_a
\end{bmatrix}+
\beta'\begin{bmatrix}
t_b/w_b \\ 1/w_b
\end{bmatrix}$$
![[Pasted image 20240302022226.png]]
segue l estensione 3D come
$$t_{p'}=\cfrac{\alpha' \cfrac{t_a}{w_a}+\beta'\cfrac{t_b}{w_b}+\gamma \cfrac{t_c}{w_c}}{\alpha' \cfrac{1}{w_a}+\beta' \cfrac{1}{w_b}+\gamma' \cfrac{1}{w_c}}$$
