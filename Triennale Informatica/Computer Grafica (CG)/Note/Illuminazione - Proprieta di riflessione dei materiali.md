---
Course: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Illuminazione nella Computer Grafica]]"
SubTopic:
---

# Illuminazione - Proprieta di riflessione dei materiali
---
la __proprietà di riflessione dei [[Illuminazione - Materiali|materiali]] __ è necessaria siccome si utilizza assieme alla __luce incedente__ per calcolare la __[[Illuminazione - Radiometria#Radianza|radianza]] riflessa__.

ci sono vari modi per specificare questa proprietà 
#### Riflettanza
la __Riflettanza__ o anche detta __Riflettanza emisferica di superfice__ è un modo per specificare la proprietà di riflessione di un [[Illuminazione - Materiali|materiale]] ed è definita come
_sia_
- $\Phi_r$ la quantità di __[[Illuminazione - Radiometria#Radiant flux|flux]]__ riflessi (o $E_r$ la [[Illuminazione - Radiometria#Irradiance e exitance|exitance]])
- $\Phi_i$ la quantità di __[[Illuminazione - Radiometria#Radiant flux|flux]]__ incidenti (o $E_r$ la [[Illuminazione - Radiometria#Irradiance e exitance|irradiance]])
_allora_ la __Riflettanza__ è definita in due modi equivalenti come $$\rho=\cfrac{\Phi_r}{\Phi_i}=\cfrac{E_r}{E_i}$$questa definizione non dipende dalla direzione del flusso e non la prende in considerazione quindi entrambi le quantità si riferisco a tutto il flux entrante o uscente da tutte le direzioni e quindi utile solo per [[Illuminazione - Interazione della luce con la materia#Luce riflessa|riflesso uniforme]]


#### Riflettanza emisferica direzionale
la __Riflettanza emisferica direzionale__ è un modo per specificare la proprietà di riflessione di un [[Illuminazione - Materiali|materiale]] ed è un estensione della __riflettanza__ che dipende dalla direzione. è definita come
_sia_
- $E_r$ la [[Illuminazione - Radiometria#Irradiance e exitance|exitance]]
- $E_r$ la [[Illuminazione - Radiometria#Irradiance e exitance|irradiance]]
- $\omega_i$ la direzione del flusso di luce incidente
_allora_ la __Riflettanza emisferica direzionale___ è definita come [[Funzioni|funziona]] della direzione $w_i$ $$\rho(\omega_i)=\cfrac{E_r}{E_i(\omega_i)}$$con questa definizione introduce la dipendenza con la luce incidente ma non ci dice ancora nulla sulla luce in uscita infatti $E_r$ si riferisce a tutta la luce riflessa e non dipende dalla direzione in cui stiamo guardando la superfice del [[Illuminazione - Materiali|materiale]] quindi si puo usare solo per [[Superfice lambertiana|Superfici lambertiane]]


#### Funzione di distribuzione Riflettanza bidirezionale (BRDF)
la __Funzione di Riflettanza bidirezionale__ o __BRDF__ (Bidirectional Reflctance Distribution Function) è un modo per specificare la proprietà di riflessione di un [[Illuminazione - Materiali|materiale]] ed è un estensione della __Riflettanza emisferica direzionale__ che ci permette di prendere in considerazione la direzione di riflessione della luce.
_sia_
- $\omega_i$ direzione della luce incidente
- $\omega_e$ direzione della luce riflessa
- $L(\cdot)$ funzione di [[Illuminazione - Radiometria#Radianza|radianza]] dipendente dalla direzione
- $E_i(\cdot)$ funzione di [[Illuminazione - Radiometria#Irradiance e exitance|irradianza]] dipendente dalla direzione
_allora_ la __BRDF__ è definita come funzione a due variabili$$f_r(\omega_i,\omega _r)=\cfrac{dL(\omega_r)}{dE_i(\omega_i)}$$ e sfruttando la relazione $$E(\omega)=L(\omega)\cos \theta \ d\omega$$con $\theta$ l angolo tra la direzione d incidenza e la [[Normale di una superfice parametrica|normale]]
 possiamo riscrivere la definizione in termini di $L$ come $$f_r(\omega_i,\omega _r)=\cfrac{dL(\omega_r)}{L(\omega_i)\cos \theta_i \ d\omega_i}$$ le direzioni possono essere specificate come angolo di inclinazione $\theta$ e angolo di azimuth $\phi$ e quindi le direzione sono funzioni di spazzi angolare e vale che $$f(\theta_i,\phi_i,\theta_r,\phi_r)=f_r(\omega_i,\omega_r)$$![[Pasted image 20240228033438.png]]



##### BRDF per superfici con riflessi Lambertaniani
utilizzando le definizioni di __BRDF__ , __riflettanza emisferica bidirezionale__ e __riflettanza__ si puo ricavare la relazione tra questi $$
\begin{array}{} 
\rho(w_i) & = & \displaystyle\cfrac{\int_{\omega_r\in  \Omega} L(\omega_r)\cos \theta_r \, d\omega }{E(\omega_i)} \\
 & = & \displaystyle\cfrac{\cancel{ E(\omega_i) }\int_{\omega_r\in \Omega} f_r(\omega_i,\omega_r)\cos \theta_r \, d\omega }{\cancel{ E(\omega_i) }} \\
 & = & \displaystyle\int_{\omega_r\in \Omega} f_r(\omega_i,\omega_r)\cos \theta_r \, d\omega 
\end{array}
$$nel caso di  [[Superfice lambertiana| superfici Lambertiane]], ovvero esattamente ciò che modella la __riflettanza__ $\rho$ abbiamo che BRDF è uguale qualunque siano le direzioni scelte infatti vale $f_r(\omega_i,\omega_r)=f_r=costante$ e di conseguenza abbiamo che $$
\begin{array}{}
\rho=\rho(w_i) & =  & \displaystyle\int_{\omega_r\in \Omega} f_r(\omega_i,\omega_r)\cos \theta_r \, d\omega \\
 & = &f_r  \displaystyle\int_{\omega_r\in \Omega} \cos \theta_r \, d\omega  & =  & f_r\pi  
\end{array}$$e quindi $$f_r=\cfrac{\rho}{\pi}$$

##### BRDF per superfici con riflessi speculari
invece nel caso di superfici con riflessi [[Illuminazione - Interazione della luce con la materia#Luce Speculare|totalemente speculari]] si avra che questo tipo di superfice è governata dalla __legge di fresnel__ definita come
_sia_ 
- $R(\omega)$ la funzione di frestern
- $\theta_i$ e gli [[Angoli|angoli]] tra luce incidente e [[Normale di una superfice parametrica|normale]]
- $\theta_r$ l [[Angoli|angoli]] tra luce riflessa e [[Normale di una superfice parametrica|normale]] 
_allora_$$L(w_r)=\begin{cases}
R(\omega_i)L(\omega_i) &  if  & \theta_i=\theta_r \\
0 & else
\end{cases}$$e quindi la BRDF è una funzione delta mono dimensionele.



#### Proprietà
la [[Fisica- Luce|luce]]  è una forma di [[Fisica - Energia|energia]] e quindi  tutte le funzioni che esprimono la capacita di riflettere devono obbedire alla [[Legge di conservazione del energia|legge di conservazione del energia]]



