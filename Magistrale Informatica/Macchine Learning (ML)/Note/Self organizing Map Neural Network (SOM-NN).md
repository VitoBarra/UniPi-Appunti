---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Self organizing Map Neural Network (SOM-NN)
---
L'**apprendimento non supervisionato** è un tipo di apprendimento automatico in cui non sono disponibili etichette per i dati di addestramento.

- **Dati di training**: insieme di dati non etichettati ${x}$
- **Obiettivi principali**:
    - **Clustering**: trovare gruppi naturali nei dati
    - **Riduzione della dimensionalità**: proiezione dei dati in uno spazio di dimensione inferiore
    - **Analisi della densità dei dati** (non trattato in questo corso)

## **Clustering**

- I dati vengono suddivisi in sottoinsiemi (**cluster**) in cui i campioni all'interno dello stesso cluster sono più simili tra loro che con quelli di cluster differenti.
- Concetti chiave:
    - **Centroide**: rappresentante del cluster
    - **Vettori di riferimento**: chiamati anche codice o prototipo

## **Quantizzazione vettoriale (VQ)**

- Tecnica per rappresentare un insieme di dati con un numero finito di vettori di riferimento $w = (w_1, ..., w_K)$
    
- Un vettore dato $x$ viene associato al **vettore vincente** $w^*(x)$ che minimizza l'errore di distorsione:
    
    d(x,w∗(x))=min⁡wid(x,wi)d(x, w^*(x)) = \min_{w_i} d(x, w_i)
    
- Divide lo spazio dei dati in regioni chiamate **poliedri di Voronoi**.
    

## **Errore di Quantizzazione**

- La funzione di errore di quantizzazione è definita come:
    
    E=∫∫p(x)d(x,w∗(x))dxE = \int \int p(x) d(x, w^*(x)) dx
    
- Versione discreta:
    
    E=∑i∑jδwinner(i,j)∣∣xi−wj∣∣2E = \sum_i \sum_j \delta_{winner(i,j)} || x_i - w_j ||^2
    
    dove $\delta_{winner(i,j)} = 1$ se $j$ è il vincitore per $x_i$, altrimenti $0$.
    

## **Algoritmo K-means**

- Metodo iterativo per partizionare i dati in $K$ cluster.
    
- Passaggi:
    
    1. Scegliere $K$ centri iniziali casuali
    2. Assegnare ogni punto al centro più vicino
    3. Ricalcolare i centri come media dei punti assegnati
    4. Ripetere finché la convergenza non è raggiunta
- Variante **online** (stocastica):
    
    - Aggiornare solo il prototipo vincente
    - Algoritmo **sensibile all'inizializzazione**

## **SOM (Self-Organizing Map)**

- Mappa topologica che associa i dati a una griglia bidimensionale di neuroni
    
- Principi:
    
    - **Competizione**: il neurone più simile all'input vince
    - **Cooperazione**: i neuroni vicini al vincitore vengono aggiornati
- **Fasi dell'algoritmo**:
    
    1. **Competizione**: determinazione del neurone vincitore
        
        $$i∗(x)=arg⁡min⁡i\|x−wi\|2i^*(x) = \arg \min_i \| x - w_i \|^2$$
        
    2. **Cooperazione**: aggiornamento dei pesi dei neuroni vicini al vincitore
        
        $$wi(t+1)=wi(t)+\eta hi^*,i(t)(x-wi(t))w_i (t+1) = w_i (t) + \eta h_{i^*, i}(t) (x - w_i (t))$$
        
        dove $h_{i^*, i}(t)$ è la funzione di vicinanza.
        
- **Proprietà**:
    
    - Mantiene la topologia dei dati
    - Possibilità di visualizzazione e interpretabilità

## **Conclusioni**

- Il clustering e la quantizzazione vettoriale sono strumenti fondamentali per l'analisi dei dati non supervisionata.
- K-means è un metodo semplice ed efficace ma limitato dalla necessità di specificare $K$.
- SOM offre vantaggi nella visualizzazione e preservazione della topologia.