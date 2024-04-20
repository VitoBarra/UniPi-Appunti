---
Subject: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Texture Mapping]]"
SubTopic:
---

# Texture - Environment mapping
---
con __Environment Mapping__ ci si riferisce al fatto di mostrare ambiente lontano circostante su una superfice 3D,  una un tipo di [[Texture Mapping|Texture Mapping]] e si utilizzano la [[Texture|texture]] per rappresentare ciò che è un immagine del ambiente.

Con l assunzione che l ambiente è infinitamente lontano  si hanno due tipi di __Environment mapping__


#### Mapping su sfere

![[Pasted image 20240302050910.png]]
![[Pasted image 20240302050925.png]]


#### Mapping su cubi
Immaginando di piazzare un cubo attorno a tutta la scena e facendo foto a tutti i 6 lati abbiamo rappresentato tutto l ambiente.

il cubo puo essere disposto come texture su 6 quadrati
![[Pasted image 20240302050955.png]]
per calcolare il mapping si utilizza la seguente formula
_sia_
- $R_{max}= \max (|R_x|,|R_y|,|R_z|)$ la componente piu grande
- $R_1$ e $R_2$ le due componenti rimanenti$$\begin{array}{}
s=\cfrac{1}{2}\cfrac{R_1}{R_{max}+1} \\
t =\cfrac{1}{2}\cfrac{R_2}{R_{max}+1}
\end{array}$$