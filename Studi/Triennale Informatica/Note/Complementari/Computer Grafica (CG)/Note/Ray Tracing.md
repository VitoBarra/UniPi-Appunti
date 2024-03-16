---
Subject: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: 
SubTopic:
---

# Ray Tracing
---
il _[[Algoritmi di renderizzazione|Ray Tracing]]_ è uno dei paradigmi di _renderizzazione_.
Osservando il funzionamento fisico della luce avremmo che i _fotoni_ che arrivano dallo spazio rimbalzano sugli oggetti e l osservatore vede quei fotoni quando e se questi raggiungono il suo occhio. 
Il _Ray Tracing_ si basa esattamente sulla simulazioni di questo fenomeno, ma invece di calcolare tutti i fotoni si calcolano solo quelli che raggiungono l _osservatore_, questo si fa per ottimizzare e evitare di calcolare fotoni che l _osservatore_ non puo vedere.
per fare ciò si _spara_ un raggio direttamente da un punto del osservazione, ovvero da un pixel, e si calcola la traiettoria del raggio, se questo colpisce una fonte di luce allora si _renderizza_ il pixel.
![[IMG_0722.jpeg]]
si denota quindi il seguente _algoritmo_
![[IMG_0725.jpeg]]
questa è una versione base che non tiene conto dei limiti che possiamo voler imporre, come ad esempio il _numero massimo di ribaldi_ o limiti _temporali_, tenendo conto di queste limitazioni si ha 
![[IMG_0726.jpeg]]

> [!tip] 
> Il primo algoritmo ignorando lo step 4 e limitando i rimbalzi ad 1, diventa l algoritmo di _ray cast_ che è un [[Algoritmo di visibilita|Algoritmo di visibilita]] 

Nel caso semplice ogni materiale è uno specchio perfetto ovvero riflette in modo _totale (tutta la luce) e speculare_ il __Raggio__, ma questo è solo un caso semplificativo.
![[IMG_0780.jpeg]]
Nel caso più generale dobbiamo considerare la _gestione delle [[Illuminazione - Ombre|ombre]]_, che sono facili da con il _ray tracing_ siccome basta seguire la seguente procedura
_se_ un _ray_ colpisce la scena allora_spara_ un raggio verso la Fonte di luce (_Shadow ray_), se questa interseca qualcosa _allora_ è un punto d _ombra_. 
![[IMG_0779.jpeg]]
i diversi angoli di _riflessione_  che insieme al aumentare il _numero massimo di rimbalzi_ aumentano la realisticità della scena ma anche il costo _[[Complessita|computazionale]]_
![[IMG_0778.jpeg]]
e i fenomeni di _difuzione_ e _refrazione_ degli oggetti traslucidi 
![[IMG_0777.jpeg]]
con il Ray Tracing e un modello di illuminazione si possono ottenere risultati come i seguenti
![[IMG_0775.jpeg]]
![[Pasted image 20240310025953.png]]

una definizione formale di __ray__ ("raggio")  è la seguente
sia 
- $o$ un punto di origine  
- $d$ un [[Vettori|vettore]] direzione normalizato  
_allora_  il __ray__ è definito come $\boldsymbol{p}=\boldsymbol{o} + t\boldsymbol{d}$ o equivalentemente 
_sia_
- $p_1$ punto di inizio  
- $p_2$ un altro punto 
_allora_   il __ray__ è definito dalla equazione parametrica $$\begin{align}
\boldsymbol{p} & =(1-t)\boldsymbol{p}_1+t\boldsymbol{p}_2 \\
\boldsymbol{p} & = \boldsymbol{p}_1+t(\boldsymbol{p}_2-\boldsymbol{p}_1)
\end{align}$$e quindi  $p_2$  determina la direzione
![[Pasted image 20240310045557.png]]


ogni raggio per essere usato deve essere "sparato" dai pixel dello schermo e per fare cio si utlizzano le seguenti considerazioni
![[Pasted image 20240310050649.png]]

_siano_
- $[0,0]\times [w,h]$ lo coordinate in pixel dello schermo
- $l,r$ dimensioni in view space 
![[Pasted image 20240310052506.png]]
_allora_ i ray Vengono generati per ogni pixel dello schermo $(i,j)$ come $$p_x=l+\cfrac{\left(\cfrac{1}{2}+i\right)}{w}(r-l)=-\cfrac{s_x}{2}+\cfrac{\left(\cfrac{1}{2}+i\right)}{w}s_x$$ con $r=-l$ e $s_x=r-l$$$p_y=b+\cfrac{\left(\cfrac{1}{2}+j\right)}{h}(r-b)=-\cfrac{s_y}{2}+\cfrac{\left(\cfrac{1}{2}+j\right)}{w}s_y$$ con $t=-b$ e $s_y=t-b$





#### Shadow ray
anche per lo shadow ray si presente il problema dello [[Illuminazione - Ombre#Problematiche del discreto (ACNE)|shadow ACNE]] ma anche questo puo essere risolto aggiungendo un piccolo byas.

#### Anti-aliasing
il problema del aliasing colpisce anche le ombre e questo si risolve facendo piu sampling 
![[Pasted image 20240310180637.png]] 
![[Pasted image 20240310180659.png]]

#### Approssimare la luce indiretta
per eseguire l [[Illuminazione - Equazione di Radianza|equazioni di rendering]] 

$$L_o(x,\omega_r) =L_e(x,\omega_r)+  \displaystyle\int_{\omega_i \in  \Omega}  f_r(x,\omega_i,\omega_r)L_i(x,\omega_i)(\omega_i\cdot \boldsymbol{n}) d\omega_i$$
solitamente si usa semplificare la parte da integrare considerando solo la luce diretta. 

Con il __path tracing__ si puo approssimare l integrale per avere dei risultati migliori questo si puo ottenere con la [[Integrazione numerica - Quadratura numerica|quadratura numerica]] e l [[Integrazione Monte Carlo|integrazione monte carlo]]

utilizzando il __metodo monte carlo__ si possono prendere dei campioni uniformi e random del emisfero $\Omega$ 
![[Pasted image 20240311042005.png]]
Per generare un punto si segue la seguente procedura
1. genera $p \in [-1,1]^3$
2. se $|p|>1$ vai a 1
3. calcola $r=\cfrac{p}{|p|}$
4. se $r.y<0$ allora $r=-r$
Questo sistema funziona ma ha bisogno di molti campioni mente potrebbe convergere piu velocemente se la distribuzione di come si prende i campioni è simile alla funzione che si vuole approssimare e quindi si possono attuare delle strategie chiamate __Importance sampling__ che basano il dove prendere i campioni  sulla [[Illuminazione - Proprieta di riflessione dei materiali|BRDF]].

In caso di BRDF __perfettamente speculare__ non ha senso prendere campioni al di fuori della direzione della luce riflessa $\omega_r$ ![[Pasted image 20240311044306.png]]
mentre in caso di BRDF che rappresenta una [[Superfice lambertiana|superfice lambertiana]] abbiamo che l integrale da approssimare diventa $$k\int_{\omega_i \in  \Omega}\cos \theta  L_i(x,\omega_i)d\omega _i$$ e quindi si possono scegliere i campioni usando una distribuzione [[Tringonometria|coseno]].
Per fare questa estrazione da una generica distribuzione $d$  e la sua [[Funzione di Ripartizione|funzione di ripartizione]] $CDF$ si esegue il seguente algoritmo
1. prendi in modo random è uniforme un valore $a\in [0,1]$
2. calcola $x=CDF(d)^{-1}(a)$ 
e quindi si puo eseguire sostituendo con il coseno

per fare questa estrazione in [[Coordinate Polari|coordinte polari]] 
1. Estrai l altezza dalla distribuzione coseno
2. estrai randomicamente e uniformemente un valore  per l angolo di azimuth $\phi \in [0,1]$
![[Pasted image 20240311045415.png]]



##### Costo computazionali 
per il funzionamento del algoritmo vogliamo _almeno un raggio_ per ogni _pixel_ e vogliamo controllare le intersezioni con ogni oggetto per ogni solato  e quindi il costo puo essere stimato come

_siano_   
- $n_{p}$ il numero di pixel 
- $n_{r}\geq n_{p}$ _raggi_
- $k$ il numero di _rinbalsi_
- $m$ il numero di _primitive_.
- $Int(o_{i})$  il costo del _test_ di intersezione del _raggio_ con l _oggetto_ $o_{i}$
   _allora_ il costo del algoritmo sarà $$cost(rayTracyng)= n_{p}k\sum^{m}_{i=0}Int(o_{i})$$Ci sono delle [[Strutture Dati|strutture dati]] che  fanno scendere il costo di $\sum^{m}_{i=0}Int(o_{i})$ ad una [[Complessita|complessita]] $O(\log (m))$ ma queste non sono adatte ad una scena dinamica siccome in quel caso si deve aggiungere il costo del _update_ della _struttura dati_.

Le _primitive_ possono essere qualsiasi geometrica con cui si puo fare il test di intersezione.




##### Next Event Estimation (NEE)
ogni raggio parte dal punto di vista e rimbalza finche non raggiunge una superfice emissiva o una fonte di luce.

![[Pasted image 20240310181120.png]]
da solo pero non basta per creare un rendering. infatti il ray tracing si usa assieme ad un modello di illuminazione.

nel caso di NEE con l apporossimazzione della luce indiretta la luce diretta va pesata con $\cos \theta$ mentre la luce indiretta no siccome è gia considerato usando l __importance sampling__
![[Pasted image 20240311045939.png]]



#### Quanti rimbalzi
scegliere il numero di rimbalzi che deve fare un raggio è importe per rendere la scena realistica, piu questi sono piu la scena sembrera realistica ma allo stesso tempo piu sara costosa da renderizare.
![[Pasted image 20240311050352.png]]

un modo per limitare il numero di rimbalzi  è il metodo a __roulette russa__ ovvero ad ogni rimbalzo fai il prossimo con [[Definizione di Probabilita|Probabilita]] $1-p$ e se il raggio viene generato la sua contribuzione viene scalata di $\cfrac{1}{1-p}$
![[Pasted image 20240311050706.png]]
in questo modo si avrà che con  $p=0$  si avra rimbalzi infiniti e  $p=1$ nessun rimbalzo
scegliere $p$ significa fare un trade-off tra velocita e qualità

un buon criterio e quella della __contribuzione della luce residuo__ ovvero si stima di quanto la luce viene assorbita ad ogni rimbalzo e si sceglie un valore di $p$ che permette abbastanza rimbalzi da tenere la luce rimanente abbastanza alto, quindi si evitano $p$ che fanno troppi rimbalzi siccome la luce alla fine verrebbe comunque scalato per un numero molto piccolo

>[!example]
>Supponiamo che una parte $\cfrac{1}{2}$ della luce venga assorbita ad ogni rimbalzo. Dopo 8 rimbalzi, la parte rimanente della luce è $\cfrac{1}{2^8} \approx 0,0039$.
>Se generiamo un altro raggio e colpisce una superficie emissiva, il suo contributo
>verrà comunque ridimensionato di 0,0039 quindi  possiamo permetterci di approssimare