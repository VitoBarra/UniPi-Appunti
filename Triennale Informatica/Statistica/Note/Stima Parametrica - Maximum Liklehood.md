---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Stima Parametrica - Maximum Likelihood
---
La **massima verosimiglianza** (Maximum Likelihood) è un metodo di [[Stima Parametrica]] dei [[Modelli Probabilistici  - Agire in domini incerti|modelli probabilistici]] che sceglie il parametro $\theta$ che rende più plausibile il [[Campione Statistico|campione osservato]].

Dato un [[Campione Statistico|campione]] $X_1,\dots,X_n$ con osservazioni raccolte nel dataset $\mathcal{D}=\{x_1,\dots,x_n\}$, la **funzione di verosimiglianza** è una [[Funzioni|funzione]] del parametro $\theta$ ottenuta dalla [[Probabilita sui numeri Reali|legge di probabilità]] del campione osservato.

La quantità di base è $p(\mathcal{D}\mid\theta)$, cioè la [[Probabilita condizionata|probabilità condizionata]] dei dati osservati dato il parametro. La likelihood usa questa stessa quantità, ma la interpreta come funzione di $\theta$: $$L(\theta;\mathcal{D})=p(\mathcal{D}\mid\theta)$$

Se le osservazioni sono [[Famiglia di variabili aleatorie Indipendenti e identicamente distribuite (IDD)|iid]], la likelihood si fattorizza:
- caso discreto: si usa la [[Definizione di Probabilita|probabilità]] degli esiti osservati: $$L(\theta;\mathcal{D})=p(\mathcal{D}\mid\theta)=\prod_{i=1}^n p(x_i\mid\theta)$$
- caso continuo: si usa la densità valutata negli esiti osservati: $$L(\theta;\mathcal{D})=f(\mathcal{D}\mid\theta)=\prod_{i=1}^n f(x_i\mid\theta)$$
La **stima di massima verosimiglianza** è una [[Statistica Parametrica#Statistica campionaria (definizione)|statistica campionaria]] che massimizza la likelihood: $$\hat{\theta}_{ML}=\arg\max_{\theta\in\Theta} L(\theta;\mathcal{D})=\arg\max_{\theta\in\Theta} p(\mathcal{D}\mid\theta)$$
Nel caso discreto si sceglie il parametro che massimizza la probabilità degli esiti osservati. Nel caso continuo l'idea è analoga, ma $L$ è una densità [[Full Joint Distribution (FJD)|congiunta]] valutata nei dati osservati, non la probabilità puntuale del campione.

## Metodo di massimizzazione
Per trovare il [[Massimi e minimi|massimo]] si lavora quasi sempre con il [[Funzione logaritmica|logaritmo]] della likelihood: $$\ell(\theta)=\log L(\theta;\mathcal{D})$$

Questo non cambia la posizione del massimo perché il logaritmo è una funzione [[Crescenza e Decrescenza di una funzione#Funzioni monotona crescente (Definizione)|monotona crescente]], ma trasforma i prodotti in somme: $$\ell(\theta)=\sum_{i=1}^n \log p(x_i\mid\theta)$$ nel caso discreto, oppure $$\ell(\theta)=\sum_{i=1}^n \log f(x_i\mid\theta)$$ nel caso continuo.

Se $L(\theta)>0$ e la funzione è derivabile, allora dalla [[Derivate fondamentali|derivata del logaritmo]]: $$\frac{d}{d\theta}\log L(\theta)=\frac{L'(\theta)}{L(\theta)}$$ quindi i punti interni in cui si annulla la [[Derivate|derivata]] $L'(\theta)$ coincidono con quelli in cui si annulla la derivata della log-likelihood: $$L'(\theta)=0 \iff \frac{d}{d\theta}\log L(\theta)=0$$

### Visione Machine Learning
Nel [[Concetti generali del Machine Learning|Machine Learning]], o più precisamente nel [[Learning nei modelli probabilistici]], lo stesso criterio viene chiamato **maximum likelihood learning**. 

Questa lettura interpreta la massima verosimiglianza come un criterio di training: si scelgono i parametri che assegnano alta probabilità al dataset $\mathcal{D}$. Non usa un prior esplicito sui parametri, quindi produce una stima puntuale interamente guidata dai dati. Con pochi dati può essere instabile; il [[Maximum a posteriori (MAP) learning]] può essere visto come una versione regolarizzata che aggiunge il contributo del prior.
