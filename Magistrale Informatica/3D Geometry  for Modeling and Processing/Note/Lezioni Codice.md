---
Course: "[[3D Geometry for Modeling and Processinga (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic:
---

# Lezioni Codice
---
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




Require dellla VCL assert per assicurare alcune proprietà sulle mesh.




casino mesh lab in arrivo:

Modulo VCGLIB


Architettura mesh lab:
Architettura a plugin


