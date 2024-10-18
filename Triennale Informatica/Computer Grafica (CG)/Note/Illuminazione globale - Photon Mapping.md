---
Course: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Illuminazione globale]]"
SubTopic:
---

# Illuminazione globale - Photon Mapping
---
Il __photon mapping__ è una metodologia per l [[Illuminazione globale|illuminazione globale]] Serve per riuscire a mostrare la __Causitche__ 
![[IMG_1124 1 1.jpeg]]
si basa sul fare samplings  dei raggio partendo da una [[Illuminazione - Tipi di fonte di luce|sorgente di luce]] e una caustica e dove molti raggio si accumulano   

l algoritmo si divide in due fasi
1. __emit__ dei fotoni dalla sorgente di luce e tieni traccia del percorso, ogni volta che colpisce un superfice non speculare perde una parte di energia fino a raggiunge un Threshold o un numero massimo di salti.
2. __Gather__: fai un passo di ray-tracing, prendi i fotoni nel vicinato del punto colpito e calcola la radinza




Il __photon mapping__ rappresenta i __[[Illuminazione - Radiometria|flux]]__ uscente da una [[Illuminazione - Tipi di fonte di luce|sorgente di luce]], quindi sotto l assunzione che i fotoni siano distribuiti uniformemente sulle superfici di uscita  dalle sorgenti, se si emettono $n$ fotoni  e il __flux__ totale è $P_l$ allora il flux rappresentato da ogni fotone è $P_F= \cfrac{p_l}{n}$ 
![[IMG_1126 1 1.jpeg]] 

per emetterei i fotoni si segue il seguente algoritmo, In caso di sfera
1. genera $d \in [-1,1]^3$
2. se $|d|>1$ va al passo $1$
3. normalizza $r=\cfrac{d}{|d|}$
mentre in caso di emisfero si esegue anche
4. se $r.y<0$ allora $r=-r$



Per ottimizzare l emissione dei fotoni è usare una __projection map__ che salva se per ogni direzione i fotoni colpiranno o no la scena, il flux dei fotoni non lanciati deve essere sottratto dal totale.
![[IMG_1127 1 1.jpeg]]

il percorso dei fotoni possono fare 3 cose
- specular reflection/reflaction (S)
- Diffido reflection (D)
- Assorbimento (A)  
![[IMG_1128 1 1.jpeg]]
i fotonisono conservati in una struttura dati 3D  in una mappa chiamata __Photon map__.
Questi possono essere di 2 tipi
- __Custic photon map__ ogni fotone che colpisce una superficie speculare e poi una diffusiva viene salvato in questo tipo 
- __Global photon map__: per ogni fotone colpisce una superficie diffusiva
i fotoni che colpiscono una superficie e rimbalzano non sono salvati 
![[IMG_1130 1 1.jpeg]]
![[IMG_1129 1 1.jpeg]]
per conservare un fotone è conservato come la posizione, la direzione di arrivo e la potenza del fotone  (in __flux__) 
![[IMG_1131 1 1.jpeg]]
un immagine renderizzata con ray tracing e i corrispondenti fotoni nella __photon map__
![[IMG_1132 1 1.jpeg]]

Il passo di  __Gatering__ consiste nel  utilizzare  i fotoni conservati per ogni posizione $p$ e direzione $\omega$ di vista per stimare la [[Illuminazione - Radiometria|radianza]]  e siccome abbiamo piu informazioni salvate possiamo utilizzare [[Illuminazione - Proprieta di riflessione dei materiali#Funzione di distribuzione Riflettanza bidirezionale (BRDF)|BRDF]] piu complessi
![[IMG_1133 1 1.jpeg]]

Quindi per calcolare la radianza si parte dalla [[Illuminazione - Equazione di Radianza|equazioni di rendering]] 
$$L_r(x,\omega )=\int_{\omega_i \in  \Omega}  f_r(x,\omega_i,\omega_r)L_i(x,\omega_i)(\omega_i\cdot \boldsymbol{n})\, d\omega_i $$ i fotoni non sono salvati in radianza ma in __flux__ e ricordando che $L=\cfrac{d^2\Phi}{dA\cos \theta d\omega}$ e sostituendo si ottiene $$
\begin{align}
L_r(x,\omega_r ) & =  \displaystyle\int_{\omega_i \in  \Omega}  f_r(x,\omega_i,\omega_r)\cfrac{d^2\Phi(x,\omega_i)}{dA\cancel{ \cos \theta } d\cancel{ \omega_i }}\cancel{ (\omega_i\cdot \boldsymbol{n}) }\, \cancel{ d\omega_i } \\
 & =  \displaystyle \int_{\omega_i \in  \Omega}  f_r(x,\omega_i,\omega_r) \cfrac{d^2\Phi_i(x,\omega_i)}{dA}
\end{align}
$$
e contando i fotoni disponibili possiamo approssimare come  $$L_r(x,\omega_r ) \approx \sum^n_{p=1}f_r(x,\omega_p,\omega_r ) \cfrac{\Delta\Phi_p(x,\omega_r)}{\Delta A}$$

Per scegliere i fotoni ci si basa sul assunzione che i fotono siano su una superfice piatta ma non sempre questo è vero siccome usare una sfera potrebbe includere degli angoli  
per migliorare la situazione si puo appiattire la sfera verso la  normale fino a fenderla un cerchio.

Per trovare velocemente i fotoni si può usare una struttura dati spaziale come [[Ray Tracing - Intersezioni#kd-tree|kd-tree]]
![[IMG_1134 1 1.jpeg]]


### Denoising
Il __denoising__ e la tecnica di eliminazione del rumore generato dai __ray__
![[IMG_1136 1 1.jpeg]]
si utilizza __bilateral filter__ che è un attenzione del [[Filtering|blure gaussiano]]
$$BF[I]_p=\cfrac{1}{W_p}\sum_{p \in \mathcal{S}} G_{\sigma_s}(\| \boldsymbol{p}-\boldsymbol{q} \|)G_{\sigma_r}(|I_p-I_q|)I_q$$
![[IMG_1135 1 1.jpeg]]

