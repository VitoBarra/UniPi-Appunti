---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Algoritmo di Remeshing semplificazione -  Collapse
---
Gli algoritmi di **Colapsing** sono [[Meshing e il Remeshing|algoritmi di remeshing]]  di [[Remeshing - Semplificazione|semplificazione]].
Si vuole risolvere il problema di semplificazione di  [[Mesh Poligonali|mesh]] formulato come
**Sia** una [[Mesh Poligonali|mesh]]  $M = (V, F)$
**Obiettivo:** Trovare $M' = (V', F')$ tale che:
  - $|V'| = n < |V|$ e la distanza $\| M - M' \|$ sia minima, 
  oppure 
  - $\| M - M' \| < \epsilon$ e $|V'|$ sia minimo.

per fare ciò questo algoritmo usa un approccio [[Algoritmi greedy|gready]], ovvero fa piccole modifiche locali che alzano il meno possibile la distorsione. 


solitamente si usa la versione con gli edge che ha parte combinatoria facile e geometrica leggermente piu difficile, mentre quelli con la faccia meno.



Sono solitamente di 3 tipi
- **Remove vertex**: si elimina un *vertice* dalla mesh e si collega i vertici che erano collegati a quel vertice ad un nuovo vertice. generalmente questo tende a togliere 2 facce
	- Questo algoritmo ha una parte geometrica semplice siccome non vanno spostati vertici ma quella combinatoria è difficile da scegliere correttamente in quanto non non c è un solo modo di scegliere come collegare i vertici   
- **edge Collaps**: Si collassano i vertici collegati ad un solo edge in un unico vertice in questo modo si eliminano due facce, 
	- combinatoriamente basta collegare i vertici connessi ai vertici che vengono cancellati al nuovo vertice, geometricamente va scelto la posizione del nuovo vertice il che va fatto con criterio per non perdere i dettagli  
- **face Collapse**: si collassano i 3 vertici di una faccia in un singolo vertice, simile al edge collapse ma rimuove 4 [[Simplex (Simplesso)|faccie]] anche 2.
![[IMG - Algoritmo gready.png]]
Generalmente di questi 3 algoritmi viene scelto l'**edge collapse** dove pero oltre a collassare i vertici su vuole anche migliorare la mesh e cio si puo fare introducendo altre operazioni come 
- l **edge split**: si aggiunge un vertice a meta del edge e  lo si collega anche ad altri vertici in modo che 2 facce diventino  4.
- **edge swap**: si inverte un edge.
![[IMG - Algoritmo di semplificazione gready mesh optimization.png]]

Per guidare queste operazioni si utilizza una funzione di **energia** che valuta la **Fitness** geometrica e la **Compattezza**.$$
E(M) = E_{\text{dist}}(M) + E_{\text{rep}}(M) + E_{\text{spring}}(M)
$$Dove 
- $E_{\text{dist}}$: somma delle distanze quadrate dei punti originali da $M$.
- $E_{\text{rep}}$: fattore proporzionale al numero di vertici in $M$.
- $E_{\text{spring}}$: somma delle lunghezze degli edge.

l algoritmo minimizza questa funzione in modo greedy,


L algoritmo di **edge collapse** puo portare in casi in cui la [[Mesh Poligonali|mesh]] diventa non [[Manifolds|manifold]]  ad esempio:
![[IMG - algoritmo gready per la semplificazione casi non manifold.png]]
ovvero abbiamo una mesh tubolare su cui si collassa un edge e si ottiene una strozzatura che rende la mesh non [[Manifolds|manifold]]. 

Per evitare queste situazioni si utilizzano delle condizioni che garantiscono che fare l operazione non genera situazioni non manifold

la **link condition** 
- $\Sigma$ sia un $2$-[[complesso simpliciale|complesso simpliciale]] senza [[Mesh Poligonali|bordo]], $\Sigma'$ si ottiene collassando l'arco $e = (\alpha \beta)$
- $\operatorname{Lk}(\sigma)$ è l'insieme di tutte le facce delle co-face di $\sigma$ disgiunti da $\sigma$.
allora $\Sigma$ e $\Sigma'$ sono [[Complesso simpliciale|omeomorfe]] $\iff$ $LK(\alpha) \cap Lk(\beta)=Lk(\alpha \beta)$

![[IMG - Condizione per mantenere la manifoldnes per algoritmi gredy di semplificazione di mesh.png]]
in questo esempio il $Lk(\alpha)$ sono tutti i triangoli che incidono su $\alpha$ e si escludono le facce di questi triangolo che incidono direttamente su $\alpha$ in questo modo resta solo un contorno. ripentendo per $\beta$ si ottiene un altro contorno, l intersezione dei due contorni coincide con del edge $Lk(\alpha \beta)$ 

![[IMG - link condition caso in cui non regge.png]]
in questo caso invece la condizione non regge e quindi collassare l edge genera una condizione non [[Manifolds|manifond]], in particolare in questo caso collassare l edge porta ad avere due facce sovrapposte.

La definizione della condizione si puo estendere ai casi in cui la mesh ha dei bordi e questo si puo fare aggiungendo un punto virtuale che è connesso ad con un edge ogni vertice sul bordi.
![[IMG - Semplificazione vertice dimmy per condizione di semplificazione.png]]




Valutazione del errore:
Uno dei problemi è la valutazione de errore che via via che la mesh viene semplificata diventa sempre piu costosa perche bisognerà andare a confrontare la nuova faccia con una porzione sempre piu grande della mesh originale.


Geometricamente si ha che si deve scegliere dove mettere in nuovo edge 
- usando la media: si hanno risultati molto mediocri: ![[IMG - Semplificazione vertice medio.png]]
- usando la mediano si hanno risultati migliori ma conunquen non adatta:![[IMG - scelta verticie Mediano.png]]
- Usando la distanza quadratica: ![[IMG - quadratic error minimization.png]]

confrontandoli vediamo che :![[IMG - Semplificazione Comparison.png]]

Per fare la versione quadratica invece della distanza di hausdof si usa una distanza quadratica che ha viene calcolata dalla punto che si scegliere alla distanza del piano.
Nel contesto della semplificazione di mesh 3D, ogni piano può essere rappresentato con un'equazione del tipo $n^T \mathbf{v} + d = 0$, dove $n$ è il vettore normale al piano e $d$ una costante. La distanza quadrata di un punto $\mathbf{x}$ dal piano è data da:$$ D(\mathbf{x}) = \mathbf{x}^T (nn^T) \mathbf{x} + 2d n^T \mathbf{x} + d^2$$Questa espressione può essere scritta come una forma quadratica, ossia un *quadric*, nella forma $Q = (A, \mathbf{b}, c)$ dove $A = nn^T$, $\mathbf{b} = dn$, e $c = d^2$. Allora la funzione quadratica associata è:$$Q(\mathbf{x}) = \mathbf{x}^T A \mathbf{x} + 2 \mathbf{b}^T \mathbf{x} + c$$Una proprietà utile è che la somma delle distanze quadrate da un insieme di piani è ancora un quadrica, ovvero si possono sommare i vari $(A, \mathbf{b}, c)$ corrispondenti.

Per stimare l’errore nella semplificazione, ad ogni vertice $v$ si associa un quadrica $Q_v$ che rappresenta la somma delle distanze quadrate da tutti i piani delle facce incidenti in $v$. Quando si considera il collasso di un arco $e = (v, w)$, l’errore risultante può essere valutato usando $Q_w(v)$, ovvero la funzione quadratica associata a $Q_w$ valutata nel punto $v$.

Dopo il collasso, il nuovo quadrica associato al vertice rimanente è semplicemente la somma:$$Q_v = Q_v + Q_w$$
Questo approccio è alla base del metodo di semplificazione delle mesh tramite *Quadric Error Metrics*, dove l’obiettivo è minimizzare la somma degli errori introdotti dai collassi degli spigoli.




Ci sono ulteriori varianti che permettono di ottenere mesh migliori dal punto di vista del numero di triangoli in parti che hanno piu dettagli 
![[IMG - Edge collaps penalizazione forme brutte.png]]
e altre ancora per evitare triangoli con altra valenza (numero di facce che incidono su un vertice) 
![[IMG - Edge collaps miglioaramento per la valenza.png]]

