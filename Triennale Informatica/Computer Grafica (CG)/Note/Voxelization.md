---
Course: "[[Computer Grafica (CG)]]"
tags:
  - CG
  - ToReview
Area: 
topic: "[[Rappresentazione di modelli 3D]]"
SubTopic: "[[Voxelization]]"
---

# Voxelization
---
 la __Voxelizazione__ è una tecnica per [[Rappresentazione di modelli 3D|rappresentare modelli in 3D]] ti tipo __volumetrico__
I __Voxel__ solo l esenzione 3D dei __pixel__, infatti, questi rappresentano un volume e sono salvati come una griglia a 3 coordinate di booleani, $1$ significa che il voxel è pieno $0$ che vuoto.
Ogni voxel puo avere dei dati aggiuntivi e come temperatura, pressione, colore a seconda del applicazione.
![[Pasted image 20240224012534.png]]
la griglia è della dimensione
$$sizeX\cdot sizeY \cdot sizeZ$$ e piu la dimensione della griglia piu la risoluzione del modello sarà altra e piu si potranno vedere i dettagli del modello.
![[Pasted image 20240224014511.png]]
Questo pero aumenta anche il costo in memoria e poi in operazioni che scala cubicamente con l aumentare di ogni singola dimensione.

Questo tipo è di rappresentazione è il tipo piu natura per la [[Stampa 3D]] e per l interpretazione di dati medici come scan magnetici.


#### Encoding Efficiente  dei modelli in Voxel oct-tree
Mantenere direttamente tutti in memoria puo essere velocemente proibitivo.
un modo per ottimizzare lo spazio utilizzato e mantenere in una struttura gerarchica i volumi. 
per costruire la struttura si parte dal un singolo Voxel grande quanto tutto il volume che si vuole utilizzare e si divide in 8 parti. Dei voluimi risultanti quelli _NON_ vuoti  vengono suddivisi nuovamente in 8 e cosi via, mente quelli vuoti saranno salvati come sono.
in questo modo eviteremmo di salvare molti volumi vuoti e ne salveremo solo alcuni piu grandi.
 Cosi facendo il costo di memorizzazione sarà quadratico anziché cubico rispetto alla risoluzione $sizeX\cdot sizeY \cdot sizeZ$. Questa struttura è chiamata __[[Quad-Tree e Oct-Tree|oct-tree]]__
 ![[Pasted image 20240224015718.png]]
 ![[Pasted image 20240224021719.png]]

in una versione 2D si divide per 4 invece che per 8 e alcuni esempi sono
![[Pasted image 20240224015807.png]]![[Voxel oct-tree.png]]

#### Rappresentazione di oggetti con Voxel
Ogni __Voxel__ Mantiene un float che puo essere un qualsiasi valore, Questo è mantenuto al centro del volume o dualmente in un angolo.
![[Pasted image 20240224022240.png]]

#### Applicazioni
##### Tomografia computerizzata
la __Tomografia computerizzata__ da in output una serie di immagini 2D, ed ognuno di questa immagine rappresenta una fetta del volume che è stato scannerizato, si possono Stackare le immagini per generare il volume come Voxel
![[Pasted image 20240224022444.png]]
avere un modello Voxellizato ci permete di vedere sezioni che non sono state origariamente catturate
![[Pasted image 20240224022731.png]]
Questo lo si fa intersecando un piano con il modello voxelizato 
![[Pasted image 20240224022803.png]]
![[Pasted image 20240224022821.png]]