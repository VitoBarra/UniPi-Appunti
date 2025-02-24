---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Machine Learning (ML)]]"
topic: nota
tags:
  - IA
---

# Statistical Learning Theory (SLT)
---
### Numero dei dati di input
Aumentando la __complessità__ del modello sono richiesti più dati per evitare l __[[Overfitting e Underfitting|overfitting]]__. infatti l _overfitting_ è un fenomeno che dipende dalla complessità e dal numero dei dati. al aumentare dei dati il modello può essere anche più complesso senza andare in over fitting 

>[!example]- polinomio di grado 9
> ![[AD987627-2D22-47F8-B3ED-7EC8512A4295.jpeg]]
>![[11752980-DCE7-4DC2-8E9B-1C39288F32A0.jpeg]]



### Statitistical learning Theory
è una teoria matematica che unifica i concetti di [[Concetti generali del Machine Learning|machine Learning]] 
1. Capacita di generalizare
	1. misurata come _rischio_ è _errore sul test_
	2. considerando le problematiche di [[Overfitting e Underfitting|overfitting e underfitting]]
2.  il ruolo della complessità del modello 
3. il ruolo della quantità di dati


### setting Formale
- si cerca di stimare la [[Funzioni|funzione]] sconosciuta  $f(\boldsymbol x)=d$ 
- Si vuole minimizzare la funzione di rischio $R=\int L(d,h(\boldsymbol x))dP(\boldsymbol x,d))$ (il _vero errore su tutti i dati_ )
- dato
	- il valore dal theatcher ($d$) e la [[Distribuzione di probabilita|Distribuzione di probabilita]] $P(\boldsymbol x,d)$
	- una funzione di $Loss$ 
- si cerca una ipotesi $h \in H$ tale che $\min R$
	- dove $H$ è lo spazio delle possibili ipotesi 
- avendo pero solo una set finiti di dati $TR$ possiamo solo minimizzare il _rischio empirico_ $R_{emp}$ (gli errori sul $TR$) 

Possiamo utilizzare $R_{emp}$ per  approssimare $R$ ?

## Definizioni
- _VC-dimensio_: la _dimensione di Vapnik-Chervonenkis_ è una misura di complessità di $H$ 
- _VC-bounds_: garantisce con in una certa probabilità $1-\delta$ 
	- $$R \leq R_{emp}+\epsilon\left (\frac{1}{l},VC,\frac{1}{\delta}\right)$$
	- Dove 
		- $\epsilon$ è una funzione  detta _VC-confidece_ che cresce con il crescere di $VC$ e decresce al crescere di $l$ (numero di dati) e $\delta$ 
		-  $R_{emp}$ decresce con modelli complessi
		- $\delta$ è la [[Intervalli di fiducia|confidenza]] con cui si decide che la maggiorazione regga
- Intuizioni:
-  $l$ (data) più alto. $\rightarrow$ VC-confidence più bassa minorazione più vicina a $R$
- modello troppo semplice (VC-dim bassa) $\rightarrow$ $R_{emp}$ troppo alto (_undefitting_) 
- alto (VC-Dimension) $\rightarrow$ basso $R_{emp}$ ma $VC-conf$ si alza il che può portare ad $R$ alto. (_overfitting_)
- ![[2459D540-ACAE-42F0-BDFA-18BEEBFB6B4F.jpeg]]
- si utilizza quindi questa formula per trovare il giusto trade off tra l accuracy sul $TR$ e tra la complessità del modello $VC-dim$
 

>[!note]
>nonostante i [[Modelli lineari con LMS|modelli lineare]] e [[Alberi di decisione|alberi di decisione]] siano stati formalizzati prima della SLT vedere come questi applicano entrambi i principi di questa teoria. che infatti è l astratto di quello che viene detto in questi modelli


> [!note]
> questo modello da i fondamenti giusti per il ML che è quindi ben fondato teoricamente



## Riassunto dei Concetti Fondamentali della Statistical Learning Theory (SLT)

### **Introduzione**
La Statistical Learning Theory (SLT) fornisce un approccio teorico per comprendere l'apprendimento automatico, concentrandosi su come bilanciare l'errore sui dati di addestramento con la capacità del modello di generalizzare su nuovi dati. I concetti chiave includono la __dimensione VC__ e la __Minimizzazione del Rischio Strutturale (SRM)__, che offrono un quadro per selezionare modelli in modo rigoroso.

---

### **Validazione e Stima dell'Errore**
La stima dell'errore di un modello può essere affrontata con metodi analitici o empirici:

1. **Metodi analitici**:
   - Criteri come AIC (Akaike Information Criterion) o BIC (Bayesian Information Criterion) valutano la qualità del modello sulla base della probabilità dei dati osservati.
   - SRM utilizza la dimensione VC per stimare il rischio vero, introducendo un termine legato alla complessità del modello.

2. **Tecniche empiriche**:
   - __Cross-validation__: suddivide il dataset in sottoinsiemi per calcolare errori su dati non utilizzati nell'addestramento.
   - __Bootstrap__: genera molteplici campioni del dataset tramite campionamento con reinserimento per stimare la variabilità dell'errore.

---

### **Dimensione VC: Capacità del Modello**
La __dimensione VC__ è una misura di complessità di una classe di funzioni \( H \). Essa rappresenta il numero massimo di punti \( p \) che possono essere separati perfettamente da \( H \) in tutte le possibili configurazioni di etichettatura.

- La definizione formale è:
  $$
  \text{VC}(H) = p \quad \text{se esiste un insieme di } p \text{ punti separabile in tutte le configurazioni, ma non esiste un insieme di } p+1 \text{ punti con tale proprietà.}
  $$

- __Esempio__: Per iperpiani in \( \mathbb{R}^n \), la dimensione VC è \( n+1 \), perché:
  - In \( \mathbb{R}^2 \), una linea può separare fino a tre punti in tutte le configurazioni, ma non quattro.
  - In \( \mathbb{R}^n \), gli iperpiani possono separare \( n+1 \) punti.

### **Shattering**
Il concetto di __shattering__ descrive la capacità di una classe di funzioni di rappresentare tutte le possibili etichettature di un insieme di punti senza errori:
- Un'ipotesi \( H \) __"shattera"__ un insieme \( X \) di \( N \) punti se può rappresentare tutte le \( 2^N \) possibili etichettature dei punti in \( X \).
- __Esempio__: Una linea in \( \mathbb{R}^2 \) può separare tre punti in tutte le configurazioni, ma non quattro.

---

### **Minimizzazione del Rischio Strutturale (SRM)**
La __SRM__ mira a bilanciare l'errore empirico sui dati di addestramento (\( R_{\text{emp}} \)) con la complessità del modello. Il limite superiore del rischio vero è espresso da:
$$
R \leq R_{\text{emp}} + \frac{\text{VC-dim} \cdot \log(1/\delta)}{N},
$$
dove:
- \( R_{\text{emp}} \): errore empirico calcolato sui dati di addestramento.
- \( \text{VC-dim} \): dimensione VC del modello.
- \( \delta \): livello di confidenza scelto (probabilità di errore del limite).
- \( N \): numero di esempi nel dataset.

Questa equazione mostra che:
1. All'aumentare della complessità del modello (\( \text{VC-dim} \)), cresce il termine di penalità.
2. È necessario un numero sufficiente di dati (\( N \)) per compensare l'aumento della complessità e garantire una buona generalizzazione.

La SRM si applica a molte classi di modelli:
- In una rete neurale, aumentando il numero di neuroni nascosti si incrementa la dimensione VC.
- Nei modelli regolarizzati, si può limitare la norma dei pesi per controllare la complessità.

---

### **Relazione tra Dati e Complessità**
L'efficacia di un modello dipende dal bilanciamento tra complessità e dimensione del dataset:
- Modelli più complessi richiedono più dati per evitare sovra-adattamento.
- La dimensione VC fornisce un'indicazione quantitativa di quante osservazioni siano necessarie per imparare in modo efficace.

Ad esempio, per un modello lineare con \( n \) parametri, il numero di dati richiesto cresce linearmente con \( n \).

---

### **Considerazioni Pratiche**
Nonostante i limiti teorici siano utili per comprendere i principi generali, presentano alcune limitazioni nella pratica:
- I limiti basati sulla dimensione VC tendono a essere molto conservativi, fornendo stime pessimistiche dell'errore.
- La difficoltà di calcolare la dimensione VC per modelli complessi può limitare l'applicazione diretta della teoria.
- La SRM è più spesso utilizzata per guidare la selezione dei modelli rispetto a calcolare stime predittive precise.

---

### **Conclusione**
La Statistical Learning Theory fornisce strumenti teorici fondamentali per comprendere il rapporto tra complessità del modello, dati e generalizzazione. Concetti come la dimensione VC e la SRM permettono di affrontare in modo rigoroso problemi di selezione dei modelli, riducendo la dipendenza da approcci empirici basati sul tentativo ed errore. Sebbene i limiti siano spesso difficili da applicare direttamente, offrono una base solida per sviluppare metodi di apprendimento più robusti ed efficienti.






#### Purpose
--- 
Investigare sulla capacità di generalizzazione di un modello misurata in termini di *errore di test* o *rischio* rispetto all'*errore di training*, analizzando gli andamenti per identificare l'underfitting e l'overfitting.
Importanti anche i ruoli della complessità del modello e del numero dei dati.

## Formal setting

#### Empirical Risk Minimization (ERM)

- Instead of minimizing the true risk $R$, minimize the **empirical risk** $R_\text{emp}$​, which is an approximation based on the training data $TR$.
    
- **Empirical Risk**:
    $R_\text{emp}(h, TR) = \frac{1}{l} \sum_{p=1}^l (d_p - h(x_p))^2$
    This is the **training error** $E$, calculated as the average loss over the finite dataset.
  - 
#### Key Concept: ERM Inductive Principle

- **Why Use ERM?**
    - We cannot compute the true risk $R$ directly since $P(x,d)$ is unknown.
    - By minimizing $R_\text{emp}$​, we attempt to approximate $R$, assuming the training dataset is representative of the true distribution.


# Statistical Learning Theory 

- ***Given***:
	- The *VC-dimension* (VC), a measure of the complexity of $H$, that means the flexibility to fit data
- We define ***VC-bound*** in the form :
$$R\leq R_{\text{emp}}+\epsilon\left( \frac{1}{l}, VC, \frac{1}{\delta} \right) $$

Where :
- $\epsilon$ , the VC confidence, is a function that grows with the $VC$ dimension and decreases with higher $l$ and $\delta$ 
- $R_{\text{emp}}$ decreases using complex models, that means with high $VC$
- $\delta$ is the confidence, that rules the probability that the bound holds -> the bound holds with probability $1-\delta$

Intuitions :
- higher $l$ means low VC -> low $\epsilon$ -> bound close to $R$ (it's limited)
- fixing $l$, a too simple model (low $VC$) -> Training Error could be high because the model cannot explain patterns in data -> high $R_{\text{emp}}$ -> **underfitting**
- fixing $l$, high $VC$ -> lower $R_{emp}$ -> $\epsilon$ could grow a lot -> not well bounds -> ***overfitting***

![[Bound on R.png]]



> [!NOTE] Simplifying
> We can make a good approximation of $f$ from examples, provided a good number of data and the complexity of the model is suitable for the task 
> 
> Fit the data as much as possible to avoid underfitting but not too much to avoid overfitting.


