---
Course: "[[Human Language Technology (HLT)]]"
Course 2: "[[Information Retrieval (IR)]]"
tags:
  - HLT
  - IR
Area: 
topic: 
SubTopic:
---
# Language models
---
Un ***language model*** è un [[Algoritmi di Machine Learning|modello di machine learning]] che predice le parole successive data una sequenza di parola.

Più formalmente, un language model assegna una [[Definizione di Probabilita|probabilità]] a ciascuna possibile parola successiva, o equivalentemente fornisce una [[Distribuzione di probabilita]] sulle possibili parole successive. 
I language models possono anche assegnare una probabilità a un’intera frase.

Possiamo assegnare una probabilità a una frase nei seguenti contesti:  
• **Traduzione automatica**: P(forti venti) > P(grandi venti)  
• **Correzione ortografica**: P(circa quindici minuti da) > P(circa quindici minueti da)  
• **Riconoscimento vocale**: P(ho visto un furgone) >> P(occhi o awe di un)  
• Altri esempi includono: **riassunto automatico**, **risposta a domande**, ecc.



Per rappresentare la probabilità che una particolare variabile casuale $X_i$​ assuma il valore “the”, si scrive $P(X_i = \text{“the”})$, o semplicemente $P(\text{“the”})4$. 

Si rappresenta una sequenza di $n$ parole come $w_1, w_2, \dots, w_n$​ oppure come $w_{1:n}$​. 
L’espressione $w_{1:n-1}$​ indica la stringa $w_1, w_2, \dots, w_{n-1}$​, cioè tutti gli elementi di $w$ da $w_1$​ a $w_{n-1}$ incluso.

Per la [[Probabilita condizionata]] di ogni parola in una sequenza con un particolare valore $P(X_1 = w_1, \dots, X_n = w_n)$ si usa la notazione $P(w_1, \dots, w_n)$.

L’obiettivo della **modellazione linguistica probabilistica** è calcolare la **probabilità di una frase o di una sequenza di parole**:  
$$P(W) = P(w_1, w_2, w_3, w_4, \dots, w_n)$$

Quindi il compito di un ***Language model*** è trovare la probabilità di: 
$$P(w_5 \mid w_1, w_2, w_3, w_4)$$


Per calcolare questa probabilità bisogna basarsi sulla [[Formula del condizionamento ripetuto (Chain rule)|chain rule]]:
$$P(B|A) = \frac{P(A,B)}{P(A)} \Rightarrow P(A,B) = P(A) \cdot P(B|A)$$

In generale, la chain rule si definisce come:  
$P(w_1, w_2, w_3, w_4, \dots, w_n) = P(w_1) \cdot P(w_2 \mid w_1) \cdot P(w_3 \mid w_1, w_2) \dots P(w_n \mid w_1, \dots, w_{n-1})$ 

si può quindi applicare per calcolare la probabilità  delle parole in una frase:

$$P(w_1, \dots, w_n) = \prod_{i=1}^{n} P(w_i \mid w_{1:i-1})$$
Ad esempio:

$$P(\text{'its water is so transparent'}) = P(\text{its}) \cdot P(\text{water} \mid \text{its}) \cdot P(\text{is} \mid \text{its water}) \cdot P(\text{so} \mid \text{its water is}) \cdot P(\text{transparent} \mid \text{its water is so})$$

In un testo però questa probabilità non si può stimare in quanto ci sarebbero troppe frasi possibili e non si avrebbero mai abbastanza dati per stimarle tutte.  

Si passa quindi ad un modello [[N-Grams Language Models|n-gram]].
L’intuizione dietro a questo modello è che, invece di calcolare la probabilità di una parola data **tutta la sua storia precedente**, possiamo **approssimare la storia** usando solo le **ultime parole**.

Si fa quindi un’**assunzione**, chiamata **assunzione di Markov**, per semplificare:

$$P(w_1, \dots, w_n) = \prod_{i=1}^{n} P(w_i \mid w_{i-k}, \dots, w_{i-1})$$

dove $k$ è il numero di parole del contesto che decidiamo di considerare.


# Language models tabulari
Nella figura è illustrato un LM tabulare utilizzabile per predire le parole in base alle probabilità
![[N-gram probabilty.png]]