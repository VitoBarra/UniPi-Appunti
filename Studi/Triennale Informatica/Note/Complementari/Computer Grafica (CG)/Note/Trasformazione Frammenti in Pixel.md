---
Subject: "[[Computer Grafica (CG)]]"
Area: 
topic: 
SubTopic: 
tags:
  - CG
---

# Trasformazione Frammenti in Pixel
---
una volta fatta la [[Trasformare da Vertici a Frammenti (Rasterizazione)|trasformazione da vertici a frammenti]] avremo dei  __frammenti__ che sono dei pixel quindi il colore arricchiti con dei valori aggiuntivi.
Per ogni frammento si dovranno fare le  [[Pipeline di Rasterizazione|per-fragment operation]].

#### Discard Test
In ordine di esecuzione sono


__Scissor Test__: serve per scrivere in un rettangolo specifico nello schermo creando uno schermo nello schermo. Tutti i frammenti al di fuori di quel rettangolo vengono ignoranti e quindi si puo scrivere in quel rettangolo senza toccare ciò che e' fuori.
![[Pasted image 20240216133044.png]] 
Questo é utile siccome ci sono molti casi dove si vorrebbe cambiare un pezzo di UI o far partire un semplice animazione e si vuole evitare di ridisegnare l intera scena, cosa non necessaria se questa non e' cambiata

__Stentcil Test__: lo Stentcil test é un test su un buffer che ci permette di ignorare alcuni frammenti, Questo puo essere utile quando alcune parti dello schermo sono fisse e si vuole mascherare tutto quello che occuperebbe lo stesso posto perché verrebbero comunque coperti da un altro oggetto, in questo modo si evita di sprecare computazione su pixel che verranno comunque sicuramente buttati.
![[Pasted image 20240216133959.png]]
Per fare cio si usa lo __Stencil buffer__ che é  un buffer di $1$ e $0$ , se c é  un 1 si ignorano i frammenti delle coordinate corrispondenti.


__Depth Test__: si utilizza lo Z-buffer per cancellare gli oggetti coperti.
![[Pasted image 20240216134035.png]]

![[Pasted image 20240216135855.png]]


#### Blending
Se un frammento passa tutti i __discard test__ allora possono succedere due cose, 
- sostituisce interamente il colore gia presente sul buffer 
- contribuisce al colore finale ovvero fa "blending" di colore

Il blending deve essere abilitato e permette di mischiare due colori, questo puo essere utile per modellare superfici non completamente opache.

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

#### Problematiche e ottimizazioni
alcune problematiche e ottimizazione di questa fase
- [[Aliasing e  Anti-Aliasing]]
- [[Back Face Culling]]
- [[Clipping di Frammenti nascosti]]