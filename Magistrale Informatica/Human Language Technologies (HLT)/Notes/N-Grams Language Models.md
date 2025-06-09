---
Course: "[[Human Language Technology (HLT)]]"
Course 2: 
tags:
  - HLT
Area: 
topic: 
SubTopic:
---
# N-Grams Language Models
---
Un **N-gram** è un [[Probabilistic Language models]] che semplifica la stima delle probabilità delle parole in un testo tenendo conto solo delle k parole precedent, seguendo l'assunzione di Markov:
$$P(w_{1}​,\dots ,w_n​)=\prod_{i=1}^n ​P(w_i \mid w_i−k​,\dots ,w_{i-1}​)$$
Un n-gram è una sequenza di n parole: un 2-gram, chiamato bigramma, è una sequenza di due parole ed un 3-gram, trigramma, è una sequenza di tre parole.

Gli n-gram sono anche detti modelli di Markov, e sono una classe di modelli probabilistici che assumono che sia possibile prevedere la probabilità di una unità futura senza dover guardare troppo lontano nel passato.

## Unigram
Il caso più semplice è quello dell'unigramma: un modello basato su una sola parola. Questa è un'assunzione troppo forte e non c'è dipendenza tra le parole di un testo. non si considerano le parole precedenti

$$P(w_1,\dots,w_n)=\prod_{i=1,\dots,n}P(w_i)$$
## Bigram 

Il bigram considera solo la parola precedente

$$P(w_1,\dots,w_n)=\prod_{i=1,\dots,n}P(w_i\mid w_{i-1} )$$

## Maximum Likelihood Estimation
Per stimare le probabilità nei modelli bigramma, possiamo utilizzare il metodo della massima verosimiglianza (MLE), che consiste nel contare quante volte si verificano certe sequenze in un corpus e poi normalizzare questi conteggi. 
La normalizzazione serve a trasformare i conteggi in probabilità comprese tra 0 e 1, dividendo ciascun conteggio per un totale appropriato, in modo che la somma delle probabilità risulti uguale a 1.

$$P(w_i\mid w_{i-1})=\frac{c(w_{i-1},w_i)}{c(w_{})}$$

L'equazione stima la probabilità di un n-gramma dividendo la frequenza osservata di una determinata sequenza per la frequenza osservata del suo predecessore. 
Questo rapporto è chiamato **frequenza relativa**. 

**Esempio**: frasi dal _Berkeley Restaurant Project_  
• puoi dirmi qualcosa su qualche buon ristorante cantonese qui vicino  
• sto cercando cibo thailandese di fascia media  
• puoi darmi un elenco dei tipi di cucina disponibili  
• sto cercando un buon posto dove fare colazione

**Conteggi grezzi dei bigrammi**, su un totale di 9222 frasi (molti zeri → non è davvero un buon modello del testo inglese, il dataset è piccolo e si modellano solo coppie di parole; man mano che si aumenta il valore di N, sarà necessario avere più dati per rendere il modello meno sparso).

![[MLE.png]]

È importante assicurarsi che il testo che si sta analizzando abbia senso.

Per stimare la probabilità di una frase, possiamo usare i bigrammi. Tuttavia, la probabilità complessiva di una frase risulta spesso molto bassa.  
Ad esempio:

$$\begin{array}
PP(<s>\text{I want english food} </s>) = \\
P(I | <s>) × P(\text{want} | \text{I}) × P(\text{english} | \text{want})× P(\text{food} | \text{english}) × P(</s> | \text{food}) \\
=0.000031
\end{array}
$$

Poiché moltiplicare molte probabilità (tutte ≤ 1) porta rapidamente a valori molto piccoli, si rischia underflow, ovvero che il risultato sia troppo piccolo per essere rappresentato in memoria. 
Per evitare questo problema, eseguiamo tutti i calcoli nello **spazio logaritmico**.

Nel dominio logaritmico:

- Le **moltiplicazioni** si trasformano in **addizioni** $(log(a × b) = log(a) + log(b))$, che sono più stabili e computazionalmente più efficienti.
- Tutti i valori sono più gestibili numericamente, poiché l’aggiunta di log-probabilità produce numeri meno estremi rispetto alla moltiplicazione diretta delle probabilità.

Conserviamo quindi i valori in log-probabilità durante l’elaborazione, e solo se necessario riconvertiamo in probabilità "normali" applicando la funzione esponenziale alla fine:  
$\text{probabilità} = exp(log-\text{probabilità})$


$$\begin{array}
 & \log(p_1 \cdot p_2 \cdot p_3 \cdot p_4)=\log p_1+\log p_2 + \log p_3 +\log p_4 \\
\log P(w_1,\dots,w_n)=\sum _{i=1,\dots,n} \log P(w_i\mid w_{i-1},\dots,w_{i-k})
\end{array}$$

