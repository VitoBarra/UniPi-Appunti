---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Self organizing Map (SOM)
---
le __self organizing maps__ (__SOM__) o anche dette __Kohonen maps__ sono [[Modelli di machine learning parametrici|modelli parametrici]] basto su [[Reti Neurali (NN)|reti neurali]] allenate con un algoritmo per l' [[Algoritmi di Apprendimento NON supervisionato|apprendimento non supervisionati]]. 


Le __SOM__ sono formate da $N$ neuroni -disposti su di una griglia uniforme a bassa dimensionalità, solitamente si usa una griglia 2D anche detta __lattice__   ![[Pasted image 20250222181050.png]]
Ogni neurone è univocamente identificabile sulla griglia con delle __coordinate__ dove il numero delle coordinate necessarie è la dimensione scelta della griglia ed ad ognuno di questi è associato un peso $\mathbf{w}$ che rappresenta la sua posizione in __input space__, infatti si ha che $dim(\mathbf{x}) = dim(\mathbf{w}) = k$ .

le __SOM__ sono un mapping dal __input space__ ai neuroni presenti sulla griglia è questo è utile per fare 
- __[[Data analisys - Clustering|Clustering]]__: i cluster possono essere identificati sulla mappa, permettendo di trovare rapidamente le strutture sottostanti nei dati.  
- __Riconoscimento di pattern e [[Quantizzatori Vettoriali (VQ)|Quantizazione vettoriale]]__: l'input viene trasformato nei pesi del neurone più vicino, ovvero nel vettore di riferimento o "codebook".  
- **Compressione dei dati**: l'input viene convertito negli indici, o codici digitali, dell'unità vincente.  
- **Proiezione ed esplorazione**: la distribuzione dei dati multidimensionali viene visualizzata in uno spazio a dimensione inferiore (la mappa 2D).  


Imparare i pesi $\mathbf{w}$ muove i neuroni nel input space ma l'algoritmo usato preserva l'[[Ordinamento topologico|ordinamento topologico]] in modo che vettori in __input space__ vicini vengo mappati nello stesso neurone o in neuroni vicini [[Topologia|topologicamente]] nella griglia.
![[Pasted image 20250222180820.png]]

### Algoritmo di learning
l algoritmo di learning delle __SOM__ è del tipo [[Learning Competitivo|learning competitivo]] è segue come:
1. **Inizializzazione**: i pesi $\mathbf{w}$ di ogni neurone nella viene inizializato casualmente  
2. **Selezione dell'input**: viene estratto un campione di input $x$ e viene passato a tutti i neuroni.
	![[Pasted image 20250222171555.png]]
3. __Fase competitiva__: si sceglie il neurone __vincente__ è ovvero quello con il peso $\mathbf{w}$ più vicino usando la [[Distanza euclidea|distanza euclidea]] al input $\mathbf{x}$. Questo è indicato dalle coordinate $r_{i^*(x)}$ con $i^*(\boldsymbol x)= \arg_i \min \|\boldsymbol x -\mathbf{w}_i\|^2_2$
4. __Fase cooperativa__: vengono aggiornati i pesi dei neuroni che hanno __relazioni topologiche__ con il neurone vincente sulla mappa (soft-max). indicando con $t$ l indice di iterazione abbiamo che la regola di update è la seguente $$\mathbf{w}_i(t+1) = \mathbf{w}_i(t) + \eta(t) h_{i, i^*(x)}(t) \left[ \mathbf{x} - \mathbf{w}_i(t) \right]$$ con $\eta$ il learning rate e $h_{i, i^*(x)}(t)$ è detta __neighborhood kernel__ ed è una __funzione di vicinanza__ nella griglia definita come:$$h_{i, j}(t) = \exp \left( -\cfrac{\| r_i - r_j \|^2}{2 \sigma^2_{nh}(t)} \right)$$ con $r_i$ coordinate sulla griglia e $\sigma$ è il raggio dei vicini che decresce in funzione delle iterazioni $t$. Questa è una funzione [[Funzione Monotona|monotonica descrescente]]  al aumento di $\|i-j\|$
 ![[Pasted image 20250222172136.png]]
5. __Iterazione fino alla convergenza__: il processo continua fino a che non si verificano più cambiamenti.  

![[Som gif.gif.gif]] ![[Pasted image 20250222192015.png]]


### Discussione
Un aspetto fondamentale nella formazione di mappe topograficamente ordinate è la regola di aggiornamento dei pesi nella fase cooperativa. A differenza di un aggiornamento indipendente per ogni unità, i pesi vengono modificati in gruppi che rispettano una relazione topologica.  

In pratica, per ogni iterazione del processo di apprendimento, non viene aggiornata solo l'unità vincente, ma anche le unità vicine nella griglia. Questo significa che i nodi che si trovano nello stesso vicinato ricevono aggiornamenti simili, permettendo loro di sviluppare una risposta coerente agli stessi tipi di input.  

Questo meccanismo garantisce che la mappa apprenda una rappresentazione organizzata dei dati, mantenendo una struttura in cui unità vicine rispondono a stimoli simili. Anche se questo approccio appare intuitivo, dimostrare formalmente come avvenga l'ordinamento delle unità è un compito complesso, come approfondito nel libro di Kohonen.  
