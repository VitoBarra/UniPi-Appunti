---
Course: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Illuminazione nella Computer Grafica]]"
SubTopic:
---

# Illuminazione - Modello Phong
---
il __modello Phong__ è un modello per di [[Illuminazione nella Computer Grafica|illuminazione locale]], è derivata empiricamente ed è piu semplice da collare rispetto al [[Illuminazione - Equazione di Radianza|equazione di irradianza]].

il __modello Phong__ è definito astrattamente come
_sia_
- $k_{\text{ambientMat}},k_{\text{diffusiveMat}},k_{\text{specularMat}},k_{\text{emmissiveMat}}$ dei coefficienti dipendenti dalle proprietà del [[Illuminazione - Materiali|materiale]] che controllano il colore e le [[Illuminazione - Proprieta di riflessione dei materiali|proprieta di riflesso del materiale]] 
$$
\begin{align}{}
L_{\text{tot}} & =L_{\text{reflected}} +k_{\text{emmissiveMat}}\\
L_{\text{reflected}} & =k_{\text{ambientMat}}L_{\text{ambient}}+k_{\text{diffusiveMat}}L_{\text{diffuse}}+k_{\text{specularMat}}L_{\text{specular}}
\end{align}
$$
Questo __modello Phong__ non prende in considerazione la visibilità della luce e utilizza solo [[Illuminazione - Tipi di fonte di luce|luce direzionale]] 

#### Componente Ambientale
il componente ambientale $L_{\text{ambient}}$ è un componente che approssima tutto ciò che puo venire dal ambiente circostante, come ad esempio rimbalzi dal altre superfici, senza pero calcolarlo davvero ma aggiungendo una piccola costante indipendentemente dalla situazione che dovrebbe emulare la luce che viene da tutte le direzioni.
è definita come 
_sia_
- $L_{\text{incident}}=[R_L,G_L,B_L]$ il [[Rappresentazione di colori|colore]] della luce incidente
- $[R_M,G_M,B_M]$ il [[Rappresentazione di colori|colore]] ambientale di un [[Illuminazione - Materiali|materiale]]
_allora_ $$L_{\text{ambient}}=L_{\text{incident}}
\begin{bmatrix}
R_M\\G_M\\B_M
\end{bmatrix}$$
![[Pasted image 20240229220346.png]]

#### Componente Diffusivo
il __componente diffusivo__ del modello Phong $L_{\text{diffuse}}$ è identico a quello del [[Illuminazione - Interazione della luce con la materia#Luce Diffusa|modello lambertiano]] e quindi 
_sia_
- $L_{\text{incident}}=[R_L,G_L,B_L]$ il [[Rappresentazione di colori|colore]] della luce incidente
- $\boldsymbol{L}=\omega_i$ la direzione della luce
- $N$ la [[Normalizzazione di schemi relazionali|normale]]
- $\theta$ è l [[Angoli|angolo]] tra $\boldsymbol{L}$ e $\boldsymbol{N}$
_allora_ il __componente diffusivo__ è definito come  $$L_{\text{diffuse}} = L_{\text{incident}}\cos \theta$$e quindi per la relazione [[Prodotto scalare euclideo (Dot product)|coseno-dotpuduct]] si ha $$L_{\text{diffuse}} = L_{\text{incident}}(\boldsymbol{L}\cdot \boldsymbol{N})$$![[Pasted image 20240229211241.png]]
![[Pasted image 20240229211259.png]]
#### Componente Speculare
l __componente speculare__ del modello Phong $L_{\text{specular}}$ è identico a quello del [[Illuminazione - Interazione della luce con la materia#Luce Diffusa|modello lambetaniano]] e quindi 
_sia_
- $L_{\text{incident}}=[R_L,G_L,B_L]$ il [[Rappresentazione di colori|colore]] della luce incidente
- $\boldsymbol{V}$ è la direzione di vista
- $\boldsymbol{R}$ la [[Illuminazione - Interazione della luce con la materia#Luce Riflessa|direzione di riflessione]]
- $\alpha$ è l [[Angoli|angolo]] tra $\boldsymbol{R}$ e $\boldsymbol{V}$
_allora_ il __componente diffusivo__ è definito come  $$L_{\text{specular}} = L_{\text{incident}}(\cos \alpha)^{n_s}$$e quindi per la relazione [[Prodotto scalare euclideo (Dot product)|coseno-dotpuduct]] si ha $$\cos \alpha = \boldsymbol{R} \cdot \boldsymbol{V}$$![[Pasted image 20240229211157.png]]
![[Pasted image 20240229211209.png]]

L esponente $n_n$ controlla la __glossines__  (o __shinies__) della superficie, ovvero quanto è concentrato il riflesso. 
![[Pasted image 20240229210014.png]]
e fa variare il cose come 
![[Pasted image 20240229211125.png]]

######  Variante Phong-Blinn
una variante di questo modello chiamata __Phong-Blinn__ cambia il modo di calcolare $\cos \alpha$ ottenendo risultati simili ma risparmiando la computazione di $\boldsymbol{R}$, 
_sia_
- $\boldsymbol{N}$ la [[Normale di una superfice parametrica|normale]]
- $\boldsymbol{L}$ la direzione della luce incidente 
- $\boldsymbol{V}$ la direzione di vista
- $\boldsymbol{H}$ un [[Vettori|vettore]] tale che $\boldsymbol{H}=\cfrac{L+V}{\| L+V \|}$ detto __halfway__
_allora_ con il modello __Blinn-Phong__ si calcola $$\cos \alpha = \boldsymbol{N} \cdot \boldsymbol{H}$$ 
questo funziona siccome il vettore $\boldsymbol{R}$ è quasi uguale a $\boldsymbol{V}$ se $\boldsymbol{N}$ è quasi la media $\boldsymbol{H}$ tra $\boldsymbol{V}$ e $\boldsymbol{L}$ 
![[Pasted image 20240229210848.png]]
questo modello funziona meglio in casi dove il vettore della riflessione crea un angolo di 90 gradi con la direzione di vista, infatti in questo caso una parte della luce rifleassa viene moltiplicata per 0 creando artefatti come quelli nel immagine a sinistra che vengono correti con questo modello
![[Pasted image 20240430054704.png]]
l uno svantaggio e che in generale non è da esattamente gli stessi risultati, infatti l angolo con il vettore halfway è generalmente piu corto e per compensare di deve alzare il valore del esponente che controlla la __glossines__ moltiplicando dalle 2 alle 4 quello che si userebbe per __Phong__

l esempio ha esponente 8 per Phong e 32 per Blinn-Phong 
![[Pasted image 20240430055019.png]]


### Modello Blinn-Phong con piu luci
l effetto della luce totale è una somma di tutta la luce nella scena e quindi il modello che considera $n$ luci diventa naturalmente $$
\begin{align}{}
L_{\text{tot}} & = k_{\text{ambientMat}}L_{\text{ambient}} +k_{\text{emmissiveMat}}+L_{\text{reflected}}\\
L_{\text{reflected}} & =\sum_i^n (k_{\text{diffusiveMat}}L_{\text{diffuse}}+k_{\text{specularMat}}L_{\text{secular}})
\end{align}
$$

un esempio del effetto del modello è il seguente in ordine, Solo ambiente, solo diffusione, solo riflesso e il totale.
![[Pasted image 20240229210132.png]]

Alcuni esempi di materiali
![[Pasted image 20240229231212.png]]