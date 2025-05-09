---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Smoothing di una superfice
---
Lo **Smoothing di una [[Superfici|superfice]]** è una delle operazioni fondamentali nell'ambito dell'[[Image Processing]] e, più in generale, dell'elaborazione di superfici geometriche. Il suo obiettivo primario è quello di ridurre il **rumore** presente nei dati, preservando al contempo le informazioni significative, in particolare i dettagli strutturali rilevanti. Contrariamente all'approccio più semplice che consiste nel sopprimere le alte frequenze – spesso responsabili del rumore – esistono algoritmi avanzati in grado di mantenere queste componenti laddove rappresentano caratteristiche utili, come bordi netti o variazioni locali significative. Questi metodi permettono di rendere lisce le aree della superficie che lo richiedono, preservando al contempo i contrasti dove sono necessari.

![[IMG - Smoothing di una superfice per surface design.png]]

![[IMG - Smothing di una superfice smothing su piu scale.png]]

Lo smoothing può essere considerato un **primo passo** per l'analisi multi-scala di una superficie. In particolare, consente di separare le componenti a bassa frequenza da quelle ad alta frequenza, aprendo la strada a operazioni successive come il *detail enhancement*, l'*hole filling* o la *mesh deformation*. Agendo sulle frequenze in maniera selettiva, è possibile ottenere un controllo raffinato sull’informazione geometrica contenuta nella mesh.

![[IMG - Smothing di una superfice hole filling.png]]

Nel contesto della modellazione 3D, lo smoothing è indispensabile per operazioni di editing intuitivo e robusto della superficie. Ad esempio, nel caso della *deformazione di una mesh*, la modifica di un punto con un certo raggio di influenza deve propagarsi in modo continuo e coerente sulla superficie, senza compromettere i dettagli esistenti. Questo approccio garantisce che, durante l’interazione, si mantengano le caratteristiche salienti della geometria, come picchi o increspature localizzate, anche a seguito di modifiche sostanziali della forma.

![[IMG - Smothing di una superfice deformazione di mesh.png]]

Dal punto di vista formale, una [[Mesh|mesh]] può essere interpretata come un **segnale vettoriale** definito su una varietà bidimensionale:

$$
f : M \longrightarrow \mathbb{R}^3 \quad f(v_i) = x_i
$$

dove $x_i$ rappresenta la posizione nello spazio del vertice $v_i$ e la funzione $f$ è estesa per interpolazione lineare agli altri punti della superficie. In questa prospettiva, l’operazione di smoothing può essere letta come un **filtraggio in frequenza del segnale** $f$, analogo al filtering nel dominio delle immagini. Tale formalismo consente di trasporre molte tecniche di signal processing nel dominio geometrico, trattando la mesh come una funzione continua su un dominio bidimensionale parametrizzato localmente nello spazio tridimensionale.

L’adozione di una parametrizzazione locale della superficie rende possibile l'applicazione di operatori di smoothing compatibili con la geometria sottostante. Questo approccio risulta particolarmente potente quando si intende controllare l’effetto dell’operazione in maniera spazialmente variabile, preservando selettivamente le informazioni rilevanti in funzione del contesto locale della superficie.

![[IMG - Smoothing di una superfice diffusin flow.png]]

Il concetto di **diffusion flow** nasce dall'idea di diffondere un segnale su un dominio discreto, come nel caso delle superfici rappresentate da mesh triangolari. Questa diffusione equivale a una ridistribuzione implicita del valore associato a ogni punto verso il suo intorno locale, secondo un principio analogo all'operatore di Laplace.

![[IMG - laplacian smoothing Smoothing di una superfice.png]]

Per ciascun vertice della mesh si calcola il vettore di spostamento verso la media dei suoi vicini (umbrella operator), e si aggiorna la posizione muovendolo di una frazione di questo vettore:

$$P_{new} = P_{old} + \lambda U(P_{old})$$

dove l'operatore umbrella $U(P)$ è definito come:

$$U(P) = \frac{1}{\sum_{i} w_i} \sum_{i} w_i Q_i - P$$

Il parametro $\lambda$ regola la quantità di smoothing applicata per ogni iterazione.

![[IMG - Smoothing di una superfice umbrella operator.png]]

Questo processo iterativo elimina progressivamente le alte frequenze della geometria, rendendo la superficie sempre più regolare. Tuttavia, tale approccio porta spesso a un evidente fenomeno di **shrinking**, per cui le geometrie con curvatura positiva tendono a contrarsi verso il centro.

![[IMG - Smoothing di una superfice problematica di shrinking coniglio.png]]  
![[IMG - Smoothing di una superfice shrinking toro.png]]

Per contrastare lo shrinking, viene introdotto il metodo noto come **Taubin smoothing**, che applica due passaggi successivi a ogni iterazione. Il primo passo sposta il vertice secondo il vettore laplaciano moltiplicato per un coefficiente positivo $\lambda > 0$, mentre il secondo passo lo riporta indietro lungo la direzione opposta, scalata da un coefficiente negativo $\mu < 0$:

- Per ogni iterazione:
  1. $P \leftarrow P + \lambda U(P)$  
  2. $P \leftarrow P + \mu U(P)$

L'effetto combinato consente di filtrare selettivamente il contenuto spettrale della superficie, rimuovendo il rumore ad alta frequenza e conservando le componenti a bassa frequenza.

![[IMG - Smoothing di una superfice taubin smoothing.png]]

Un ulteriore problema emerso con il diffusion flow è la **dipendenza dalla densità della tassellazione**. In una mesh non uniforme, i vertici in aree più dense si spostano più rapidamente verso la loro media locale, alterando la velocità di convergenza e l'efficacia del processo di smoothing. Per mitigare tale squilibrio, si può introdurre una pesatura in funzione della lunghezza degli spigoli:

$$U(P) = \frac{2}{\sum_i e_{ij}} \sum_i \frac{Q_i}{|e_{ij}|} - P$$


![[IMG - laplacian Smoothing problemma di velocita di convergenza dipendenza della tasselizazione.png]]

Una soluzione più avanzata prevede l’impiego della **curvatura media** come guida per il flusso di smoothing. In questo caso, lo spostamento di ogni vertice è diretto lungo la normale media, scalata da un parametro $\lambda$:

$$P_{new} = P_{old} + \lambda Hn(P_{old})$$

dove $Hn(P)$ è l’**operatore di Laplace-Beltrami**, espresso come:

$$Hn(P) = \frac{1}{4A} \sum_i (\cot \alpha_i + \cot \beta_i)(Q_i - P)$$

Questo operatore tiene conto della geometria locale, preservando in modo più accurato la forma originale della superficie durante lo smoothing.

![[IMG - Smoothing di una superfice mean curvature flow.png]]  
![[IMG - Smoothing di una superfice Laplace-Beltrami.png]]






Un approccio classico allo smoothing consiste nell’utilizzare un'integrazione numerica del tipo di Eulero per risolvere l’equazione differenziale che guida l’evoluzione del segnale $f$ sotto l’azione del **Laplaciano discreto** $L$. L’idea di base è quella di attenuare progressivamente le alte frequenze attraverso una diffusione controllata nel tempo.

L’**integrazione esplicita** di Eulero aggiorna il segnale con uno step temporale piccolo $h$, seguendo la formula iterativa:

$$
f(t + h) = f(t) + h\lambda Lf(t)
$$

dove $\lambda$ regola l’intensità dello smoothing. Questo metodo è semplice da implementare ma diventa instabile se $h$ non è sufficientemente piccolo. Per ovviare a questo limite, si può adottare una **formulazione implicita**, che consiste nella risoluzione di un sistema lineare alla forma:

$$
(I - h\lambda L)f(t + h) = f(t)
$$

In questo caso, anche per valori di $h$ più grandi si ottiene una soluzione stabile. Il sistema risultante è di grandi dimensioni, ma presenta una struttura sparsa e ben condizionata, tipica dei Laplaciani discreti su mesh triangolari, e quindi risolvibile in modo efficiente con tecniche iterative.

![[IMG - Smoothing di una superfice versione implicita e espicita.png]]

L’operazione di smoothing può anche essere interpretata come la **soluzione diretta** di un sistema lineare che minimizza l’energia associata al Laplaciano, corrispondente alla quantità di variazione locale del segnale. In questa prospettiva, non si procede per passi temporali ma si risolve direttamente un sistema che impone una diffusione ottimale. Questo approccio è particolarmente conveniente quando si desidera applicare un numero elevato di iterazioni equivalenti, poiché risulta più efficiente nel complesso, sebbene più complesso da implementare.

In entrambi i casi, lo smoothing si riconduce a un problema di risoluzione di sistemi lineari sparsi, ben noti e ben gestibili nella pratica computazionale, con strumenti consolidati nell’ambito del [[Geometric Processing]].
