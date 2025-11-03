---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Inferenza con Full Joint distribution
---
L un [[Agenti Razionali|agente]] capaci di prendere delle decisioni in [[Modelli Probabilistici|ambienti incerti]] usa l'**inferenza probabilistica** che consiste nel calcolo delle [[Probabilita condizionata|probabilità posteriori]] per proposizioni di interesse, date alcune evidenze osservate $e$. Una strategia generale prevede l'utilizzo della **[[Distribuzione di probabilita congiunta totale|full joint distribution]]** come **base di conoscenza** $KB$, da cui possono essere derivate tutte le risposte possibili. In pratica si vuole fare una **query** al $KB$ del tipo:
**sia**
- $X$ è la variabile di query
- $e\in E$ è l'**insieme delle evidenze osservate** a cui è assegnato un valore $e$
- $Y$ l insieme delle **variabili non osservate**
**allora** la query puo essere espressa come:$$
\mathbf{P}(X \mid e) = \alpha \mathbf{P}(X,e)=\alpha \sum_y \mathbf{P}(X, e, y)
$$dove $\mathbf{P}$ è un vettore di tutte le [[Definizione di Probabilita|probabilita]] dei valori di $X$ e $\alpha=\cfrac{1}{\mathcal{P}(e)}$ è un coefficiente di normalizzazione per far sommare le probabilità ad $1$ , potremmo non conoscere $\alpha$ ma questo non è un problema perche sappiamo che $\alpha \sum_{y,x} \mathcal{P}(x, e, y) =1$ e possiamo ottenerlo risolvendo per $\alpha$. 
Questa formula viene direttamente dal applicazione della regola di marginalizzazione

Usare direttamente questa formula è **poco pratico** perche anche per domini dove ogni variabile è di [[Variabili Aleatorie Notevoli - Bernulli|bernulli]] (**binaria**) avremmo  una [[Complessita|complessità]] $O(2^n)$ spazio e tempo esponenziali in funzione del numero di variabili.
