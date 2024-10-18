---
Course: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Illuminazione nella Computer Grafica]]"
SubTopic: "[[Illuminazione - Modelli avanzati]]"
---

# Illuminazione - Modello Cook-Torrance
---
il modello di __illuminazione  Cook-Torrance__ è un modello per di [[Illuminazione nella Computer Grafica|illuminazione locale]] basato sulla fisica e quindi deve rispettare la [[Legge di conservazione del energia|legge di conservazione dell energia]]. 


Si basa sul assunzione che le superfici siano fatte da microsfacetature che si comportano come [[Illuminazione - Interazione della luce con la materia#Luce Riflessa|specchi perfetti]]
![[Pasted image 20240305222003.png]]

Per la direzione di refrazione questo modello segue la __[[Illuminazione - Interazione della luce con la materia#Luce Riflessa|legge di snell]]__ mentre per la luce che viene emessa si ha che$$L_r=L_p\cfrac{DGF}{(\boldsymbol{N}\cdot \boldsymbol{L})(\boldsymbol{N}\cdot \boldsymbol{V})}$$
dove $D$ gestisce l assunzione delle micro-sfaccettature. è detto fattore di _roughness_ ed è modellizzato come la distribuzione di Spizzichino-Beckmann $$D=\cfrac{1}{m^2\cos ^4\alpha}e^{\cfrac{-\tan \alpha}{m}}$$
con $\alpha=\arccos(\boldsymbol{N}\cdot \boldsymbol{H})$ e $m$ la media dello slope delle-microsfaccetture
![[Pasted image 20240305222310.png]]
 $G$ è un termine geometrico che considera l effetto di __masking__ $G_1$e l effetto di __self-shadowing__ $G_2$che riducono la [[Illuminazione - Radiometria|radianza]] finale. e viene calcolato come $$\begin{array}{}
G_1 & = & \cfrac{2(\boldsymbol{N}\cdot \boldsymbol{H})(\boldsymbol{N}\cdot\boldsymbol{V})}{(\boldsymbol{V}\cdot\boldsymbol{H})}
 \\ 
G_2 & = & \cfrac{(\boldsymbol{N}\cdot\boldsymbol{H})(\boldsymbol{N}\cdot\boldsymbol{L})}{(\boldsymbol{V}\cdot\boldsymbol{H})}
 \\
G & = & \min(1,G_1,G_2)
\end{array}
$$![[Pasted image 20240305220338.png]]

$F$ prende in considerazione la __legge di fresnel__ per la riflessione, questo oltre che dal materiale dipende dalla [[Fisica - Onde|lunghezza d onda]] e anche togliendo questa dipendenza si resa con $$F=\cfrac{1}{2}\cfrac{(g-c)^2}{(g+c)^2}\left[1+\cfrac{(c(g+c)-1)^2}{(c(g-c)+1)^2}\right]$$dove $c=\sqrt{ \boldsymbol{V} \cdot \boldsymbol{H} },g=\sqrt{ c^2+\eta^2-1 }$ con $\eta$ l [[Illuminazione - Materiali|indice di rifrazione]] 
![[Pasted image 20240305223535.png]]
![[Pasted image 20240305224711.png]]
essendo molto costosa da calcolare solitamente viene approssimata con l __approssimazione di Schlick__ $$\begin{array}{}
\rho & = & \left(\cfrac{\eta_1-\eta_2}{\eta_1+\eta_2}\right)^2 
 \\

F & = & \rho(1-\rho)(1-\boldsymbol{N}\cdot\boldsymbol{L})^5
\end{array}
$$