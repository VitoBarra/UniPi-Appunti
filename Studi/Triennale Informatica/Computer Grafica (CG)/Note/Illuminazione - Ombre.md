---
Subject: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Illuminazione nella Computer Grafica]]"
SubTopic:
---

# Illuminazione - Ombre
---
le __ombre__ sono ciò che rendono piu realistica una scena aiutano a capire la forma di un oggetto in caso di __self-shadowing__ e danno informazione spaziali

intuitivamente un __ombra__  è una regione più scura rispetto alla regione intorno al __ombra__ stessa per via di qualche oggetto che sta bloccando l’ arrivo della luce a quella specifica regione, ovvero è una regione più scura circondata da una regione piu chiara

formalmente abbiamo che l __ombra__ è definita come :
	un punto $p$ è detto in __ombra__ rispetto ad una [[Illuminazione - Tipi di fonte di luce|fonte di luce]] se il raggio di luce che parte dalla forte verso $p$ colpisce un altro punto $p'$ prima di raggiungere $p$
Questa è una definizione geometrica e non specifica di quanto la zona deve essere piu scura infatti questa informazione  dipende dal [[Illuminazione nella Computer Grafica|modello di illuminazione]] usato
![[Pasted image 20240306061803.png]]
le __ombre__ che si formano dipendono dal [[Illuminazione - Tipi di fonte di luce|tipo fonte di luce]] che si utilizza.
il tipo di luce ad area genera effetti di area parzialmente in ombra siccome alcuni raggi che partano da quella raggiungono un altro oggetto mentre altri arrivano sulla superfice, questo fenomeno e chiamato penombra.
Questo nella realta è il caso piu comune ma è piu complesso da calcolare 
![[Pasted image 20240306063756.png]]



#### Shadow mapping
Assumendo
- [[Illuminazione nella Computer Grafica|illuminazione locale]] ovvero si permette ai fotoni di fare al massimo un rimbalzo
- i [[Illuminazione - Tipi di fonte di luce|tipi di fonte di luce]] sono solo direzionali o a punto, quindi non ad area e quindi niente penombra

lo __Shadow mapping__  è una metodologia intuitiva per calcolare le ombre. Si renderizza la scena e per ogni frammento si calcola se questo è in ombra.

Per eseguire efficientemente questo test si utilizza una seconda camera oltre a quella per [[Trasformare da Vertici a Frammenti (Rasterizazione)|rendeirzzare sullo schermo]] posizionata sulla luce e quindi chiamata __Light camera__, si renderizza la scena dalla __Light camera__ e si utilizza il [[Rimozione di Superfici Nascoste#Z-Buffer|depth buffer]] per capire se un oggetto è visibile, se lo è allora significa che non ci sono ostacoli e di conseguenza è illuminata e non in ombra. successivamente si usa questa informazione nel seguente __algoritmo di shadow mapping__
1. \[__Shadow Pass__\] renderizza la scena dalla __light camera__ e conserva lo z-buffer
2. \[__Lighting Pass__\] renderizza la scena dalla camera di vista e per ogni frammento proietta il punto $p$ corrispondente sulla __light camera__, a questo si puo controllare lo z-buffer e vale che $z_p<d_p\implies$ in ombra, dove
	- $z_p$ è il valore conservato nello z-buffer della cella corrispondente alla proiezione di $p$  
	- $d_p$ è la $z$ del punto  $p$ rispetto alla __light camera__  
in pratica con la __Light Camera__ si crea un modo per decidere se considerare un frammento in ombra o meno  
![[Pasted image 20240306061842.png]]
#### Modellare i tipi di luce
Per utilizzare lo __Shadow Mapping__ bisogna modellizzare i [[Illuminazione - Tipi di fonte di luce|tipi di luce]] con un tipo di [[Proiettare una scena 3D in 2D#Proiezioni|camera]] adatto per riempire correttamente lo z-buffer. Bisogna anche fre in modo che il view Volume della camera corrisponda con la luce che ci interessa modellare


##### Directional light
la __luce direzionale__ viene modellizzata con una __[[Proiettare una scena 3D in 2D#Proiezioni|telecamera ortogonale]]__ e per fare in modo da prendere solo gli oggetti che ci interessano si precede come segue
_sia_ $d$ la direzione della luce
_allora_ 
1. crea un [[Frames|frame]]  $F$ prendendo come origine la luce e impostando $z=-d$ e generando gli altri due col l algoritmo di generazione di [[Frames|frame]] 
2. calcolare il __axis aligned bounding box__ (AABB)
	- in modo preciso [[Applicazione lineare - Proiezione|proiettando]] vertici della geometrica sugli assi del [[Frames|frame]] $F$
	- in modo approssimato proiettando i vertici del AABB della scena in word space  
![[Pasted image 20240308014009.png]]


##### luce a punto o  luce posizionale
la __luce a punto__ viene modellizzata con una __[[Proiettare una scena 3D in 2D#Proiezione prospettica|telecamera prospettica]]__ e per fare in modo da prendere solo gli oggetti che ci interessano si precede come segue
_sia_ $d$ la direzione della luce
_allora_ 
1. crea un [[Frames|frame]]  $F$ prendendo come origine la luce e impostando $z=-d$ e generando gli altri due col l algoritmo di generazione di [[Frames|frame]] 
2. proietta i vertici sul asse $z$ e setta il near plane $n$
3.  proietta i [[Computer grafica - Primitive Geometriche|vertici]] sul near plane (che è parallelo al asse XY)
![[Pasted image 20240308015209.png]]

#### Problematiche del discreto (ACNE)
lo __Shadow mapping__ in teoria funziona in pratica l aritmetica [[Aritmetica di Macchina|finita dei calcolatori]] infatti preso il valore nello z-buffer della luce $z_p$ e il valore $z$ del  frammento $d_p$ abbiamo che in un mondo ideale le uniche due condizione possibili sono $z_p>d_p$ e $z_p=d_p$ ma essendo un aritmetica finita si avrà per via degli arrotondamenti possa succedere anche che $z_p<d_p$
![[Pasted image 20240308021034.png]]
in pratica questo significa che la scena verrà rindirizzata con dei comportamenti di alcune zone che sembrano assegnate a ombra randomicamente per fenomeni di __Self-Shadowing__, questo problema è conosciuto come __Surface ACNE__


##### Soluzione: Bias
Per risolvere il problema del __surface ACNE__ si aggiunge un termine $\varepsilon$ chiamato __bias__ a $z_p$ in modo da dare un vantaggio verso l essere illuminato.
e la codizione diventa $z_p+\varepsilon>d_p$ allora frammento illuminato
![[Pasted image 20240308021649.png]]
questo risolve buona parte dei problemi dove l ombra è dove non dovrebbe esserci ma aggiunge qualche caso dove alcune parti che dovrebbero essere in ombra risultano illuminati, solitamente pero questo è un effetto meno notabile e considerato un buon trade-off.


$\varepsilon$ va scelto con cautela non esiste un valore universalmente giusto infatti va scelto abbastanza alto da rimuovere il __self-shadowing__ ma non troppo da creare altri artefatti come il seguente  
![[Pasted image 20240308022558.png]]
in particolare si puo vedere come piu è alto lo slope di una mesh in camera space peggio questo effetto è pronunciato.
![[Pasted image 20240308023049.png]]
si puo quindi scegliere un $\varepsilon$ che dipende da questo slope e allora si avra che
_sia_
- $n$ la [[Normale di una superfice|normale della superfice]]
- $L$ la direzione della luce
- $\cdot$ è il [[Prodotto scalare euclideo (Dot product)|Dot product]]
- $\alpha,min\_\varepsilon,max\_\varepsilon$ fattori arbitrari di fine tuning
_allora_ vale che $$\varepsilon=\text{clamp}(\alpha \tan (\arccos(n\cdot L)),min\_\varepsilon,max\_\varepsilon)$$![[Pasted image 20240306065133.png]]


##### Soluzione: Geometria chiusa
Per risolvere il problema del __surface ACNE__ solo nel caso speciale in cui le [[Mesh Poligonali#Classificazione mesh|geometrie siano chiuse]] si puo  renderizare nello __Shadow pass__ solo le [[Trasformazione Frammenti in Pixel#Back Face Culling|back faces]].
![[Pasted image 20240308023836.png]]
questo elimina completamente il problema del __surface ACNE__ ma genera l effetto opposto ovvero adesso puo capitare che le  back Face siano classificate come illuminate incorrettamente.
La soluzione a questo problema è facile basta calcolare la norma della superfice e se questo va lontana dalla direzione della luce allora è in ombra 