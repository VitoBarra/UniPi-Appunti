


# Lecture 2024-09-23

Rappresentazione DI forme 3D : rappresentare la forma geometrica della superficie assunzione forte in quando no è l unico modo per rappresentare una forma in 3D

Un altra idea è usare la densità del volume, LA TAC fa quello


Un’altra idea è la semplice visualizzazione del apparenza. 


Un idea di “visualizzo solo l apparenza” :  una moneta senza struttura 3D ma con i dati per gestire la luce in modo da poterla parametrizzare con la direzione della luce.



Nel corso rappresentare la forma della superficie che è la modalità canonica 





Una superficie: una spazio e 2D 





Un simplex è un inviluppo convesso di un certo numero di pianti 
0- simplex : 1 punto
3-simplex : 4 punti alla piramide   



ogni sotto insieme proprio di un simplesso è un faccia proprio del simlesso


un simplicial coplex semplifica le è una collezione di simplessi
il grado di un complesso è il massimo grado di un suo sotto simplesso

un complesso sempliciale è massimo se ttutte i suoi elementi sono  faccine di un simolesso di grado massimo 



PEr mesh si intende un complesso massimo di grado 2



Non necessariamente un complesso sempliciale è ben formato è anche un 2 Manifold 

# 25-09-2024

Poligoni palatonici : come i poligoni regolari la in 3D ne esistono solo 5




Guardandola i poligoni platonici due sono i duali del altro. cubo-ottaedro e dodecaedro-icosaedro.

per calcolarli basta prendere i baricentri delle facce e collegandoli con un ed



Caratteristica di eulero:  somma a vertici delle componenti di un complesso sempliciale
$\chi=V - E + F$ 
questo valore è una costante con le modifiche locali al complesso  nel caso in cui si il complesso sempliciale sia corretto e massimale 

ed ogni oggetto simile ad una palla $\chi=2$ probabilmente simile ad una palle intende topologicamente (con trasformazione).  




la Caratteristica di eulero conta il Genus, interpretato come il numero di buchi o maniglie,

le geometrie che hanno lo stesso giunus possono essere trasformata da una al altra in modo continuo ovvero come se fosse una gomma. in altri casi andrebbe “spezzata”


il gibus è definito come il numero massi di tagli che si possono fare senza perdere pezzi della superficie.

in caso di superfici aperta si ha che $$\chi =2-2g-b$$ dove $b$ è definito come loop di edge sul bordo 


dimostrazione intuitiva nelle slide molto fica si usa aggiungendo un vertice. 



###### Conversione 

un campionamento del dominio di una  [[Curve parametriche]] , 
campionamento regolare del domioneo non implica regolarità nella mesh, ovvero la mesh finale avrà delle zone con faccine piu piccole e zone con faccine piu grandi. 

Secondo me questo dipende dal fatto che la derivata in certi piu della funzione e piu grande e quindi una piccola variazione sposta di tanto sulla funzione e quindi in 3D punti piu distanti e faccine piu grandi.



convertire [[Superfici implicite]] in mash 
si utilizza il marching cube: compinamento regolare della funzione e interpolazione lineare tra gli spigoli per trovare l iso superficie. 2^4 casi in 3D 2^8 ma per simmetria ci si riduce a 15 casi

per passare da mesh a superi e implicita: 
campi di distanza campianati:  questo è utile in quanto è comodo fare operazioni con funzioni implicite come somma che resta un operazione implicita 


Teoria dei segnali: casino col campionamento. questo genera quindi un sacco di sampling artifact.



##### Formati
STL : molto brutto poche operazioni semplici da fare, solo una collezione di faccie


obj,OFF: lista di vertici e lista di vertici per faccia.


face-Base Connectivity: 
vertici che tengono posizione e il riferimento ad una faccia
faccine: 3 vertici e riferimento a 3 faccine adiacenti.
Non mantengono edge e questo puo essere un problema.



Edge-base rappresentation:
- Vertici:
	- posizione 
	- 1 edge




rappresentazione Halfedge-Based:


esiste un rappresentazione puramente matriciali con tante matrici sparse.



# Lezione 30-09-2024
Lezione codice: 


VCG LIbrary: c++ template base nessun grande problema di compilazione (da vedere)

Una libreria  per mesh processing, molti algoritmi stato del arte. 
Lavoriamo sul branch devel 


La libreria e face centrica: tutti i conti si fanno con le faccie. 

un po’ di caos e da scrivere per evitare il boilerplate 


usa un sacco di metodi statici, quindi un saaaaacco di boilerplate 


ha anche delle funzioni di utilità per fare l IO dei file.
gestisce tutto con i valori di errore, quindi niente eccezioni 


3D stendford’ bunny primo modello acquisito digitalmente è aperto pubblicamente a tutti, è usato storicamente 


Load mask = maschera di ciò che trova nel file, fatto durante il caricamento del STL

con STL si salvano molti volte gli stessi vertici ciò si puo risolvere con la parte “Clean” della libreria. Il cleaning funziona con le posizioni quindi se servono vertici duplicati per mantenerli dati diversi questi sono persi.

lezy delation: si maria un bit per gli elementi cancellati, questo si fa perche cancellare e spostare i vettori è un operazione tendenzialmente molto pesante. 


allocazione e decollo azione deve essere gestita dalla libreria che gestisce tutte le referenze ai puntatori.

CI sono funzioni di compattazione che gestisce esplicitamente gli elementi cancellati.

se non si fa la compattatura la fatto il check a mano per controllare se il vertice è cancellato o meno, se si itera sui vettori non compattati .

per contare gli edge si usa la formula:
$$Edge = \cfrac{Face*3}{2} +\cfrac{EdgeBuondry}{2}$$
1. 
nominazione:
solitamente gli edge sono numerati in senso anti orario 



nel adiacenza faccia faccia si usa che un faccia è collegata a se stessa se non c è un altra faccia in quella direzione. questo ha diversi vantaggi come avere al possibilità di distinguer nulla da non inizializato e la possibilità di alcuni algoritmi di funzionare comunque.
df


Capire i loop di boundary: 
si usano le funzioni di navigazione. 
la navigazione si fai con i pos che sono coppie e ci si sposta con i flip che è un operante simmetrica, se ne si fa due si torna alla stessa posizione. 
C è un flip per ogni elemento quindi faccia edge e vertice.

per cercare i buchi insogna marcante delle facce e e questo funziona perche le mesh sono manifold 2



# 2024-10-02


Remeshing: si ma remeshng perche puo service siccome triangoli di diemensioni di verse hanno proprietà diverse, gli equilateri sono leggermente migliori se i triangolo sono troppo appiattiti molte operazioni sono mal codizionati.

Refinement e suddivisione: capire come aggiungere informazione in modo da avere una mesh simile al originale.

Coarsening e semplificazione: capire cosa buttare via per semplificare la mesh



Refinement e suddivisione si puo usare per gestire una forma complessa con pochi punti di controllo, si usa una forma semplice e si muovo i punti di quella mesh semplice e poi si fa suddivisione che è un processo controllabile per avere una forma piu refinita.



sono organizabili in due classi:

Dividono una faccia in sotto faccia oppure si puo fare la suddivisione sul duale.

Oppure si pussono classificare in approssimazione e interpolazione, nel primo caso perdo i verici originali e li suo come punti di controllo. mentre nel interpolazione mantengo i vertici originali.

Solidi di archimede: figure fatte da forme regolareù




Algorito duale e approssimante:
Doo sabin: dopo il primo passo si hanno solo vertici di grado 4





Primale aprossimante
Catmull Clark: dopo il primo paso si hanno vertici con gerardo irregolari, preserva i gradi originali
Proprietà comoda: la mesh diventa solo quad dopo il primo step.

ed esiste una forma chiusa per trovare la superficie. 
Se non ci sono



Loop:
Suddivisione per mesh triangolori primale aprossimante :

PReserva i triangoli in triangolo generando da un triangolo 4 triangolo.


Primale e interpolante
Butterfly suddivisione: si mantiene la posizione originale tra i vertici 
geometricamente fa cagare siccome per lasciare i punti fermi fa ondulare le superfici che dovrebbero essere dritte. Funiziona bene geometria molto curve di base tipo un toro.



Semplificazione:
Utile per semplificare delle parti della mesh che non ha bisogno di tanti triangolo per essere rappresentata.
 Si fa per efficentee per implementare i Level od detail (LOD)


Complessità e accuratezza non hanno una relazione lineare.

va gestito l errore, e questa è definito in due modi
si milita geometrica e similarità di apparenza.

la differenza in apparenza è difficile da misurare perche ci sono molti fattori in gioco. 

quella geometrticaè facile: 

trovare un errore sotto un certo epsilon è Np-Hard ma si usano delle uristiche che funnzionano bene tranne nei casi con occhi poligoni ma va bene perche l interesse e nello spettro dove l errore è molto minore.


si Usano algoritmi gready : 

si scegli l operazione migliore che alza di meno l errore. 

solitamente si usa la versione con gli edge che ha parte combinatoria facile e geometrica leggermente piu difficile, mentre quelli con la faccia meno.

con i vertici la parte combinatoria è difficile, non c è un unico modo per collegare i vertici restanti.


si vuole anche migliorare la mesh durante questo processo.

Puo creare situazione non manifold ma ci sono dei sistemi per controllare quando questo accade. 

Valutazione efficiente del errore:

# 2024-10-07


L algoritmo di suddivisione clad in-Clark puo essere nche fatto in due passi utilizzando un algoritmo “half dual” che ha anche delle proprietà comode da solo siccome rende la mesh comporta solo da quadriilati, che in certi contesti è comodo.

La libreria è face center e solitamente funziona per triangolo ma ha qualche utilità anche per i poligoni.

Si possono calcolare i baricentri delle facce con CalcolatePolyBaricenter()


La libreria tende a non aggiornare i puntatori interni qundi conviene usare altre cose come male (int, int), int


#  2024-10-09

Spazio l index:



Affrontare dal lato continuo della mesh e non da quella combinatoria.

Servono a rispondere a domande diverse rispetto alle query combinatorie. ad esempio capire i punti di intersezioni o la selezione con un interfaccia utente.


Utili anche per fare simulazione fisica.



si usano strutture dati che permettono di capire le collisioni in tempi sub logaritmi quasi costanti.


le strutture si dividono non genrarchiche e gerarchiche.


le non gerarchiche ha senso avvolte in caso in cui l overhead di gestire una struttura piu grande supera la non ottimalita che danno queste strutture.


quella non gerarchica costruisce3 una griglia con celle uniformi , ogni cella mantiene i riferimenti a tutte le primitive che toccano quella cella. 


La griglia occupa molta memoria e ciò non è buona anche per la cache.


per risolverla si utilizzza una funzione di hashing 
spagina hashi. Trovare la dimensione delle cellu non è facile e il che viene risulto cn le strutture gerarchiche.

Hierarchical Indexing:



BSP. vengon usati in DOOM
Binari space partitionTree:
si divide uno spazio con un piano e ogni meta è un nodo di un albero. finche ogni nodo ha una sola primitiva
Query con albero bilanciato




Importante la scelta del puano, ortogonalmente si possono scegliere un piano che agilità per la divisone per massima re  la profondità o il bilanciamento


kD-Tree:
Specializzazione di BSP dove ogni piano è allineato a gli assi.



Quad_Tree: 
Si divide la regione in 4 parti uguali nel caso 2D o in 8 in caso 3D 

memorizzazione con Z ordering per ottimizzare sulle cache.

tutte cose viste anche in computer grafica.








