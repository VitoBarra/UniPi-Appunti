---
Course: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Illuminazione nella Computer Grafica]]"
SubTopic:
---

# Illuminazione - Radiometria
---
la __Radiometria__ racchiude alcune unita di misura utili per formalizzare come rappresentiamo la luce, questo ci permette di formalizzare l [[Illuminazione nella Computer Grafica|illuminazione di una scena sintetica]] 



### Radiant flux
i __Radiang flux__ o solo __flux__  $\Phi$ misurano la quantità di [[Fisica - Onde|luce]] ([[Fisica - Energia|energia]] quindi misurata in __Joule__) passante (sia in entrata che in uscita) per un aria o per un volume per unita di tempo misurato in __Watt__ ($W=J/s$)

Questa unita di misura da sola non basta a specificare la luminosità di una superfice siccome non ci da nessun informazione su:
- In che Direzione la luce sta arrivando sulla superfice o andando via dalla superfice 
- Distinzione tra l energia in entrata o in uscita 
- non dipende dalla dimensione della superfice, 
	- con flux fisso una superfice piu ampia apparirà meno luminosa rispetto ad una piu piccola.
- non distingue se il passaggio di energia è uniforme o ha aree che sono preferite rispetto ad altre


###  Irradiance e exitance (Radiosita)
l __Irradiance e exitance__ (avvolte espresso chiamate anche __Radiosità incidente__ e __Radiosità uscente__) sono una misura di _Densità di area_ per __flux__ ovvero specificano quanta di __flux__ che passa per una area unitaria. Si Utilizzano due termini siccome si distingue tra _flux_ entranti e uscenti
- __Irradiance__: Misura la quantità di luce _entrante_ o anche detta _incidente_
- __Exitance__: Misura la quantità di luce _uscente_ 
__Irradiance e exitance__ sono espressi come la quantità di __flux__ che passa per una superfice sufficientemente piccola anche infinitesimale e considerando superfici con flusso di __flux__ non-uniforme si definiscono la [[Funzioni|funzione]] dipendente dalla posizione sulla superfice $x$ $$E(x)=\cfrac{d\Phi(x)}{dA}$$e nel caso il flusso sia uniforme sul area abbiamo che la formula diventi $$E=\cfrac{\Phi}{A}$$ la sua unita di misura è il __Watt su metro quadro__ ($W/m^2$)

dalla definizione si puo ricavare la relazione con il __flux__ come $$d\Phi = E\ dA$$
![[Pasted image 20240227045938.png]]
#### Intensita di luce
l __Intensità di luce__ è una una misura di _Densità di direzione_ per __flux__ ovvero la quantità di flux per __Angolo solido__($\omega$) (espresso in [[Steradianti|Steradianti]]), Questo ci specifica quanti __flux__ passano per una data area in una certa direzione.
l __Intensità di luce__ è espressa come una funzione dipendente dalla direzione$$I(\omega)=\cfrac{d\Phi(\omega)}{d\omega}$$e la sua unita di misura è Watt su steradianti ($W/Sr$)
![[Pasted image 20240227052928.png]]
dalla definizione di [[Steradianti#angolo solido|angolo solito]] sappiamo che l angolo solito totale che prende tutta la sfera di raggio $r$ misura $4\pi$ Steradianti, di conseguenza possiamo dire che l __intensità__ di un emettitore di luce a punto che emette $\Phi$ __flux__  in modo uniforme è $I=\cfrac{\Phi}{4\pi}$

#### Radianza
la __Radianza__ è una una misura doppia di _Densità di Area e direzione_ per __flux__, Questa misura il flusso di radiazioni da una superfice per unita di __area proiettata__ e per unita di [[Steradianti|angolo solido]] per la direzione del flusso.
l __Aria proiettata__ deve esserlo sulla direzione del flusso di __flux__ e la stessa area proiettata si puo riferire a quantità di area vera diversa a seconda del orientamento della superfice 
sia $\theta$ l angolo tra la direzione $w$ e la [[Normale di una superfice|normale della superfice]]
la __Radianza__ puo essere espressa come $$L(\omega)=\cfrac{d^2\Phi}{dA_{\bot}d\omega}=\cfrac{d^2\Phi}{dA\cos \theta\  d\omega}$$
l unita di misura della radianza è il Watt su metro quadrato su steradiante ($\cfrac{W}{m^2\ Sr}$)
![[Pasted image 20240227052901.png]]

calcolando l integrale della __Radianza__ su tutta l semisfera si ottiene la __irradiance__ ovvero tutta la __Radianza__ che proviene da tutte le direzioni.$$E= \int_\Omega L(\omega) \cos \theta\, dw $$


#### Tavola riassuntiva
![[Pasted image 20240227040849.png]]