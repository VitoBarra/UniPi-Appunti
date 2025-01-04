---
Course: "[[Programmazione e Algoritmica (PEA)]]"
topic: 
tags:
  - PEA
---



# Programmazione Dinamica
---
La **programmazione dinamica** (**PD**) rappresenta un paradigma algoritmico avanzato finalizzato alla risoluzione di problemi computazionalmente complessi mediante la decomposizione in sottoproblemi sovrapposti. Si tratta di una metodologia cruciale nell'informatica teorica e applicata, che sfrutta una **relazione di ricorrenza** per calcolare iterativamente le soluzioni ottimali.

## Principi Teorici Fondamentali

1. **Sottoproblemi Sovrapposti**: I problemi affrontabili con **PD** sono caratterizzati dalla ripetuta risoluzione degli stessi sottoproblemi. Per ottimizzare i calcoli, i risultati intermedi vengono memorizzati in strutture dati adeguate, minimizzando il costo computazionale derivante da ricalcoli inutili.
    
2. **Proprietà dell'Ottimalità dei Sottoproblemi**: La costruzione della soluzione globale si basa sulla combinazione di soluzioni ottimali dei sottoproblemi componenti. Questa proprietà è essenziale per l'applicazione corretta della tecnica.
    

## Strategia di Risoluzione

1. **Formulazione della Relazione di Ricorrenza**: Per ogni problema, è necessario derivare una relazione matematica che descriva la dipendenza tra un problema principale e i suoi sottoproblemi.
    
2. **Tecnica di Memorizzazione (Memoization)**: La memorizzazione consiste nel salvare i risultati intermedi all'interno di strutture come tabelle o dizionari, che possono essere consultati in tempo costante.
    
3. **Approccio Bottom-Up**: Questa strategia prevede il calcolo iterativo delle soluzioni dei sottoproblemi in ordine crescente di complessità, fino alla risoluzione del problema globale.
    

## Caso Studio: Serie di Fibonacci

Il calcolo della sequenza di Fibonacci rappresenta un esempio paradigmatico. La relazione di ricorrenza è:

F(n)=F(n−1)+F(n−2),con F(0)=0,  F(1)=1F(n) = F(n-1) + F(n-2), \quad \text{con } F(0) = 0, \; F(1) = 1

### Implementazione Iterativa Bottom-Up

```python
# Calcolo della sequenza di Fibonacci mediante programmazione dinamica

def fibonacci(n):
    if n <= 1:
        return n
    dp = [0] * (n + 1)
    dp[1] = 1
    for i in range(2, n + 1):
        dp[i] = dp[i - 1] + dp[i - 2]
    return dp[n]
```

### Analisi della Complessità

- **Tempo**: **O(n)**
- **Spazio**: **O(n)** (riducibile a **O(1)** mediante ottimizzazione dello spazio).

## Problemi Classici della Programmazione Dinamica

1. **Problema dello Zaino (Knapsack Problem)**: Si cerca di massimizzare il valore totale degli oggetti selezionati, rispettando un vincolo di capacità. La relazione di ricorrenza associata è: dp[i][w]=max⁡(dp[i−1][w],dp[i−1][w−wt[i]]+val[i])dp[i][w] = \max(dp[i-1][w], dp[i-1][w-wt[i]] + val[i])
    
2. **Allineamento di Sequenze**: Fondamentale nella bioinformatica, questo problema riguarda la determinazione della somiglianza ottimale tra due sequenze biologiche, utilizzando punteggi definiti per allineamenti e mismatch.
    
3. **Problemi sui Grafi**:
    
    - **Cammini Minimi**: Calcolo del percorso più breve tra due nodi.
    - **Cammini Massimi**: Identificazione di percorsi con il massimo valore cumulativo.

## Vantaggi e Limiti

**Vantaggi**:

- Riduzione drastica della complessità temporale rispetto agli approcci ricorsivi naïve.
- Applicabilità a una vasta gamma di problemi teorici e pratici.

**Limiti**:

- Elevato consumo di memoria dovuto alla memorizzazione delle soluzioni intermedie.
- Richiede una formulazione precisa della relazione di ricorrenza, il che può risultare non banale.

## Conclusioni

La programmazione dinamica costituisce un approccio indispensabile per l'elaborazione di algoritmi efficienti in contesti computazionali complessi. Comprendere e applicare correttamente i suoi principi permette di risolvere problemi altrimenti intrattabili, sia in ambito teorico che applicativo.