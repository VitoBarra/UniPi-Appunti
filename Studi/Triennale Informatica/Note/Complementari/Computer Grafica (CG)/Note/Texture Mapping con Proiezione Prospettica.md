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
![[Pasted image 20240301070153.png]]
