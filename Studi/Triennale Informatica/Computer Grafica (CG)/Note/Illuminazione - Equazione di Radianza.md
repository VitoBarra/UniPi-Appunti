---
Subject: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Illuminazione nella Computer Grafica]]"
SubTopic:
---

# Illuminazione - Equazione di Radianza
---
per mostrare la luce su una scena sintetica abbiamo bisogno di calcolare la [[Illuminazione - Radiometria#Radianza|radianza]] di ogni superfice vista da un pixel quindi per ogni direzione di vista

la [[Illuminazione - Radiometria#Radianza|radianza]] dipende dalle [[Illuminazione - Proprieta di riflessione dei materiali|proprieta riflettenti del materiale]] espressi con la BRDF e dalla luce incidete. Considerando il fatto che nella realta la luce arriva da tutte le direzione abbiamo che la funzione per calcolare la radianza è
_sia_
- $\Omega$ l'emisfera attorno al oggetto
- $\omega_r$ la direzione  di riflessione 
- $\omega_i$ la direzione di luce incidente
- $x$ il punto del oggetto che si sta guardando
- $f_r(\omega_i,\omega_r)$ la [[Illuminazione - Proprieta di riflessione dei materiali#Funzione di distribuzione Riflettanza bidirezionale (BRDF)|BRDF]] del [[Illuminazione - Materiali|materiale]]
- $E_i(\cdot)$ l [[Illuminazione - Radiometria#Irradiance e exitance|irradianza]] proveniente da una direzione 
_allora_ l __equazione di radianza__ o __rendering__ è $$ \begin{align}

L_r(x,\omega_r) & =  \displaystyle\int_{\omega_i \in  \Omega}dL_r(x,\omega_r) \, d\omega_i \\
 & =   \displaystyle\int_{\omega_i \in  \Omega}  f_r(x,\omega_i,\omega_r)E_i(x,\omega_i)\, d\omega_i\\
 & =  \displaystyle\int_{\omega_i \in  \Omega}  f_r(x,\omega_i,\omega_r)L_i(x,\omega_i)\cos \theta_i\, d\omega_i   \\
& =  \displaystyle\int_{\omega_i \in  \Omega}  f_r(x,\omega_i,\omega_r)L_i(x,\omega_i)(\omega_i\cdot \boldsymbol{n})\, d\omega_i 
\end{align}
$$
Generalizzando per includere anche la __radianza__ proveniente da un emettitore e $\omega_o=\omega_r$ si avrà che $$L(x,\omega_o) =L_e(x,\omega_o)+L_r(x,\omega_o)$$
dove $L_e$ rappresenta la radianza proveniente da un emettitore e $L_r$ la radianza perveniente da un riflesso.

Questa equazione è fisicamente accurata


#### Approssimare l Equazione di Radianza
L __equazione di radianza__ puo produrre risultati molto realistici ma è molto costosa da calcolare e quindi non adatta a rendering __real time__.
Si puo calcolare un approssimazione di questa equazione.

invece di calcolare la luce ambientale $L_i(x,\omega_i)$ questa si puo semplificare e discretizzare.
- si semplifica:  considera che la luce riceve la stessa luce in ogni suo punto, quindi si puo ignorare il parametro $x$
- si discretizza: considerando solo alcune direzioni $\omega_1,\dots ,\omega _n$ della luce incidente e non tutte.
in questo modo possimo di usare
- se non ci interessa il colore $n$ costanti di luce $L_i$
- se ci interessa il colore: utili $[L_i^R \ L_i^G \ L_i^B]^T$ e quindi la formula diventa $$L_r(x,\omega_i,\omega_r)=\displaystyle\sum_{i=0}^{n-1}  f_r(x,\omega_i,\omega_r)\begin{bmatrix}
L_i^R \\ L_i^G \\ L_i^B
\end{bmatrix}(\omega_i\cdot \boldsymbol{n})$$
invece di calcolare il riflesso dipendente dalle [[Illuminazione - Proprieta di riflessione dei materiali|proprita del materiale]] $f_r(x,\omega_i,\omega_r)$ si possono semplificare i materiali considerandoli tutti [[Superfice lambertiana|puramente diffusivi]] anche detti __materiali lambertiani__ in questo modo il valore di $f_r(x,\omega_i,\omega_r)$ è sempre costante 
- se non ci interessa diventa una costante $B_x$ chiamata __albedo__ del punto $x$  
- se ci interessano diventa  3 valori $[D_x^R,D_x^G,D_x^B]^T$ detti __colori diffusivi__.
e quindi la funzione diventa $$L_r=
\begin{bmatrix}
D_x^R \\ D_x^G \\ D_i^B
\end{bmatrix}
\displaystyle\sum_{i=0}^{n-1}  
\begin{bmatrix}
L_i^R \\ L_i^G \\ L_i^B
\end{bmatrix}
(\omega_i\cdot \boldsymbol{n})$$
questo approssimazione è molto semplice ma puo generare solo risultati poco interessanti.

