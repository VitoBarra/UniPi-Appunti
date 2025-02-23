---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Machine Learning (ML)]]"
topic: nota
tags:
  - IA
---
# K-Means
---
il __$k$-Means__ è un [[Algoritmi di Apprendimento NON supervisionato|algoritmo di apprendimento non supervisionato]] [[Modelli di Macchine learning Instance-Based|Instance-Based]]  usato per il [[Data analisys - Clustering|clustering]] 

il __$k$-Means__ per fare [[Data analisys - Clustering|clustering]] usa l approccio che utilizza la [[Quantizzatori Vettoriali (VQ)|quantizazione vettorialie]], si usa quindi la definizione del problema ![[Data analisys - Clustering#Clustering tramite quantizzazione di vettori]]
[[Derivate|Derivando]] la funzione di loss si può ottenere ottenere la regola di aggiornamento come $$\Delta \mathbf{w}_{i^*} = \eta \delta_{winner} (i,i^*)(x_i-w_{i^*}) $$ e questa regola costituisce la versione __[[Tipi di strategie di learning con gradient descent|online]]__ del __$k$-mean__

Mentre la versione __[[Tipi di strategie di learning con gradient descent|batch]]__ segue come:
1. Scegliere $k$ __centroidi__ iniziali, posizionandoli in uno dei seguenti modi:
    - Selezionando casualmente $k$ punti dal set di dati.
    - Definendo $k$ punti casuali all'interno dell'iper-volume che contiene il set di dati.
2. Assegnare ogni punto del dataset al __centroide__ più vicino (ovvero al cluster più vicino).
3. Ricalcolare i __centroidi__ dei cluster come la media geometrica dei punti attualmente assegnati a ciascun cluster.
	- per ogni $cluster_i$  il nuovo _centroide_ $$\mathbf{w}_i=\frac{1}{|cluster_i|}\sum_{\mathbf{x}_j\in cluster_i}\mathbf{x}_j$$ dove $|cluster_i|$ è il numero di elementi nel cluster
	    
4. Se il criterio di convergenza non è soddisfatto, tornare al passo $2$. Alcuni possibili criteri di convergenza sono:
    - Nessuna (o minima) riassegnazione di punti ai cluster.
    - Minima riduzione dell'errore quadratico.

Ripetere il processo fino al raggiungimento della convergenza.


![[53FD956D-E338-4DDF-923B-FDF28C4F01B7.gif]]


### Discussione
il __$k$-means__ è un algoritmo molto semplice ma si devono conoscere a priori il numero di cluster $k$ che ci vogliono cercare il che può comportare il trovare il numero giusto tramite try and error.
è un problema di ottimizzazione locale quindi soffre del problema dei __minimi locali__ e quindi la soluzione dipende dal punti di inizio. Funziona bene solo nei casi in cui i dati siano in uno ipersfera compatta e non funziona quindi bene con forme diverse dei dati ad esempio con forme concave. ![[E461230C-BFBE-420F-A3B6-DBE774395364.jpeg]]
in più questo algoritmo __non__ ci permette di proiettare i dati in una __dimensione più bassa__.


