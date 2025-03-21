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
le __self organizing maps__ (__SOM__) o anche dette __Kohonen maps__ sono [[Modelli Parametrici|modelli parametrici]] basto su [[Reti Neurali (NN)|reti neurali]] allenate con un algoritmo per l' [[Algoritmi di learning NON supervisionato|apprendimento non supervisionati]]. 


Le __SOM__ sono formate da $N$ neuroni  disposti su di una griglia uniforme a bassa dimensionalità, solitamente si usa una griglia 2D anche detta __lattice__   ![[Pasted image 20250222181050.png]]
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
1. **Inizializzazione**: i pesi $\mathbf{w}$ di ogni neurone nella viene inizializzato casualmente  
2. **Selezione dell'input**: viene estratto un campione di input $x$ e viene passato a tutti i neuroni.
	![[Pasted image 20250222171555.png]]
3. __Fase competitiva__: si sceglie il neurone __vincente__ è ovvero quello con il peso $\mathbf{w}$ più vicino usando la [[Distanza euclidea|distanza euclidea]] al input $\mathbf{x}$. Questo è indicato dalle coordinate $r_{i^*(x)}$ con $i^*(\boldsymbol x)= \arg_i \min \|\boldsymbol x -\mathbf{w}_i\|^2_2$
4. __Fase cooperativa__: vengono aggiornati i pesi dei neuroni che hanno __relazioni topologiche__ con il neurone vincente sulla mappa (soft-max). indicando con $t$ l indice di iterazione abbiamo che la regola di update è la seguente $$\mathbf{w}_i(t+1) = \mathbf{w}_i(t) + \eta(t) h_{i, i^*(x)}(t) \left[ \mathbf{x} - \mathbf{w}_i(t) \right]$$ con $\eta$ il learning rate e $h_{i, i^*(x)}(t)$ è detta __neighborhood kernel__ ed è una __funzione di vicinanza__ nella griglia definita come:$$h_{i, j}(t) = \exp \left( -\cfrac{\| r_i - r_j \|^2}{2 \sigma^2_{nh}(t)} \right)$$ con $r_i$ coordinate sulla griglia e $\sigma$ è il raggio dei vicini che decresce in funzione delle iterazioni $t$. Questa è una funzione [[Funzione Monotona|monotonica descrescente]]  al aumento di $\|i-j\|$
 ![[Pasted image 20250222172136.png]]
5. __Iterazione fino alla convergenza__: il processo continua fino a che non si verificano più cambiamenti.  

![[IMG - Som alg gif.gif]] ![[IMG - SOM wheight Positions.png]]