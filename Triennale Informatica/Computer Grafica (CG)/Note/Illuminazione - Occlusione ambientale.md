---
Course: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Illuminazione nella Computer Grafica]]"
SubTopic: "[[Illuminazione - Ombre]]"
---

# Illuminazione - Occlusione ambientale
---
l __ambient acclusion__ (occlusione ambientale) serve a descrivere l ombra creata dalla luce d ambiente infatti per modellizzare questa cosa siparte dal [[Illuminazione - Modello Phong|modello phong]] si cambia il parametro di modulazione del componente d ambiente in modo che dia un valore tra $0$ e $1$ dipendente da quanta geometria puo bloccare l arrivo della luce a quel punto $$
\begin{align}{}
L_{\text{tot}}(x,\omega_r) & = k_{\text{ambientMat}}L_{\text{ambient}}(x,\omega_r) +L_{\text{emmissive}}(x,\omega_r)+L_{\text{reflected}}\\
L_{\text{reflected}} & =\sum_i^n (k_{\text{diffusiveMat}}L_{\text{diffuse}}(x,\omega_i)+k_{\text{specularMat}}L_{\text{secular}}(x,\omega_i))
\end{align}$$per fare cio possiamo vedere il __componente ambientare__ come l [[Integrali|integrale]] della luce proveniente da tutto l emisfero 
_sia_ 
- $L_a(w_i)$ la quantità di [[Illuminazione - Radiometria|radianza]] proveniente dalla direzione $\omega_i$
- $IsBlocked(x,\omega_i)$ un predicato che da 1 se niente blocca quella direzione o 0 se qualcosa la blocca
_allora_ il componente di __occlusione ambientale__  $\mathcal{A}(x)$ che sostituisce il componente ambientale $$\mathcal{A}(x)=\int_{\Omega} L_a(w_i)IsBlocked(x,\omega_i) \, d\omega_i $$
per calcolare il predicato $IsBlocked$ si lanca un raggio da ogni punto in ogni direzione $\omega$ se il raggio colpisce qualcosa allora 0 altrimenti 1.
![[IMG - Illuminazione - Occlusione ambientale 1.png]]
a questo punto i valori calcolati solitamente si salvano direttamente nei [[Computer grafica - Primitive Geometriche|vertici]] o in una [[Texture|texture]]. Il problema di questa tecnica e che funziona solo per scene statiche e non funziona bene con la [[Pipeline di Rasterizazione|pipeline di renderizazione]]
![[IMG - Illuminazione - Occlusione ambientale 2.png]]
![[IMG - Illuminazione - Occlusione ambientale 3.png]]

#### Screen Space Ambient Occlusion (SSAO)
la __Screen Space Ambient Occlusion (SSAO)__ è un modo per calocalre l ambient occlusione (AO) ma si utilizza soltanto la geometria in screen space ovvero la rasterizazione della geometria vera e quindi discreta e percio una rappresentazione parziale della scena
![[IMG - Illuminazione - Occlusione ambientale 4.png]]
Il termine di ambient acclusion è calcolato come
per ogni pixel controlla quanto punti di  un insieme di punti al interno di un cercchio di raggio $r$ centrato nel pixel sono visibili.
_sia_
- $S$ l [[Insiemi Matematici|insieme]] dei punti
- $d(\cdot)$ il valore nella depth map di un punto
- $z(\cdot)$ il valore $z$ di un punto
- la [[Funzioni|funzione]] di visibilià $$V(p) = \begin{cases}
1  &  if  & z(p)<d(p) \\
0 & else 
\end{cases} $$
_allora_ il termine di occlusione è calcolato come
$$AO =1-\cfrac{1}{|S|}\sum_{p \in  S}V(P)$$

![[IMG - Illuminazione - Occlusione ambientale 5.png]]
questo potrebbe essere ottimizzato utilizzando la [[Normale di una superfice parametrica|normale  della superfice]]
![[IMG - Illuminazione - Occlusione ambientale 6.png]]

il calcolo della $AO$ puo essere espresso con la sua pipeline.
![[IMG - Illuminazione - Occlusione ambientale 7.png]]



altre teccniche
![[IMG - Illuminazione - Occlusione ambientale 8.png]]