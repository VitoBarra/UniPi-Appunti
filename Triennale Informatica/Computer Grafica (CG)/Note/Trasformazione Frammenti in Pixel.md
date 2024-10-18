---
Course: "[[Computer Grafica (CG)]]"
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


#### Problematiche e ottimizzazioni
alcune problematiche e ottimizzazione di questa fase
- [[Blending di colore]]
- [[Aliasing e Anti-Aliasing]]
- [[Back Face Culling]]
- [[Clipping di Frammenti nascosti]]