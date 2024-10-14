---
Subject: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Trasformazione Frammenti in Pixel]]"
SubTopic:
---

# Blending di colore
---
Se in [[Trasformazione Frammenti in Pixel|fase di trasformazione da frammento a pixel]] un frammento passa tutti i __discard test__ allora possono succedere due cose, 
- sostituisce interamente il colore gia presente sul buffer 
- contribuisce al colore finale ovvero fa "blending" di colore

Il __blending__  e permette di mischiare due colori, questo puo essere utile per modellare superfici non completamente opache.

Sia 
- $s=[s_R,s_G,s_B,s_{\alpha}]^T$ il [[Color Space|colore]] del frammento detto __source__ 
- $d=[d_R,d_G,d_B,d_{\alpha}]^T$ il [[Color Space|colore]] gia sul buffer detto __destinazione__ 
- $\boldsymbol{b},\boldsymbol{c}$ dei __Fattori di blending__
allora il colore risultante e' una [[Combinazioni Lineari|combinazione lineare]] dei due $$d'= 
\underbrace{ \begin{bmatrix}
b_R \\b_G \\b_B \\b_{\alpha}
\end{bmatrix} }_{ b }
\begin{bmatrix}
s_R \\s_G \\s_B \\s_{\alpha}
\end{bmatrix}
+
\underbrace{ \begin{bmatrix}
c_R \\c_G \\c_B \\c_{\alpha}
\end{bmatrix} }_{ c }
\begin{bmatrix}
d_R \\d_G \\d_B \\d_{\alpha}
\end{bmatrix}$$
i fattori $b,c$ possono essere variati per implementare diversi effetti.
![[Pasted image 20240216140058.png]]

>[!tip]
>in __OpenGL__ il __Blending__ deve essere abilitato tramite il comando glEnable(GL_BLEND)


###### Superfici trasparenti
L utilizzo piu comune per il blending é  l utilizzo per modellare superfici trasparenti.
si renderanno le primitive __Back-to-Front__ e ogni volta che si renderizza una superfice trasparenti si fa __blending__ per calcolare il contributo dei colori gia presenti  utilizzando l __alpha channel__ per discriminare quanto "colore" passa $$b'= 
\underbrace{ \boldsymbol{\begin{bmatrix}
s_{\alpha} \\s_{\alpha} \\s_{\alpha} \\s_{\alpha}
\end{bmatrix} } }_{ b }
\begin{bmatrix}
s_R \\s_G \\s_B \\s_{\alpha}
\end{bmatrix}
+
\underbrace{ \begin{bmatrix} 
1-s_{\alpha}\\1-s_{\alpha} \\1-s_{\alpha} \\1-s_{\alpha}
\end{bmatrix}  }_{ c }
\begin{bmatrix}
d_R \\d_G \\d_B \\d_{\alpha}
\end{bmatrix}
$$
l alpha della colore di destinazione non é mai usato, questo funziona perché é gia sul buffer quindi sarà gia stato applicato
