---
Course: "[[Machine Learning (ML)]]"
topic: "[[Reti Neurali (NN)]]"
tags:
  - IA
  - ML
---

# Recurrent Neural Network
---
le __reti neurali ricorrenti (RNN)__ sono [[Reti Neurali (NN)|reti neurali]] dove sono anche presenti __connessioni riccorrenti__ ovvero connessioni che vanno all indietro. l'output della rete non dipende solo dal l'input corrente ma anche dalla storia degli input arrivati precedentemente, questo rende la rete adatta al trattamento di __dati sequenziali__.
Le __connessioni ricorrenti__ della rete fungono da __memoria interna__ interna e siccome questa evolve nel tempo la rete diventa un [[sistemi dinaimci|sistema dinamico]] e può quindi essere analizzata con la teoria dei sistemi dinamici. 
A differenza dei metodi basati su una finestra temporale fissa ([[Input delay neural network (IDNN)|IDNN - Input Delay Neural Networks]]), le __RNN__ possono trattare sequenze di __lunghezza variabile__.

![[Pasted image 20241229014553.png]]

le __reti neurali ricorrenti__ hanno come  __dominio del input__ una __sequenza discreta di [[vettori|vettori]]__ e  possono risolvere task di  __Trasduzione generale__ mapping da una sequenza di input in un __valore o sequenza__ di output. 
![[Pasted image 20250207233220.png]]
I task possibili sono: 
- __Sequence Classification__:  l'intera sequenza di input viene processata e produce un'unica uscita che rappresenta la classe a cui appartiene la serie. __Esempi:__ Sentiment analysis su una frase (positivo, negativo, neutro).
- __IO-Transduction (Input-Output Isomorphic):__  per ogni elemento della sequenza di input vine dato un output __Esempi:__ Traduzione automatica (parola per parola).
- __Next-Step Prediction__:  Prevedere il prossimo elemento nella sequenza, basandosi sui precedenti.  __Esempi:__ Completamento del testo.
- __Sequence Generation__ : si genera una sequenza di output basata su un input iniziale. L'output può essere di lunghezza variabile. __Esempi:__ Generazione di testo.




###  Simple RNN 
I implementazione più semplice di una __rete ricorrente__ è la __simple RNN__ ovvero una rete dove c è una singola __connessione ricorrente__ che aggiunge l output della rete prossimo vettore di input.   ![[Pasted image 20250207233844.png]]
![[Pasted image 20250207234035.png]]
assumendo $x(0) = 0$ l'intera rete è descritta dalle equazioni $$\begin{cases}
x(t) = f(W l(t) + \hat{W} x(t-1) + b) \\
y(t) = f_{out}(W_{out}x(t) + W_{in}l(t) + b_{out})
\end{cases}$$
- $l(t), x(t), y(t)$ input e stato e l output al tempo $t$
- $W,\hat{W},W_{out},W_{in}$  i pesi delle connessioni tra input e stato, della connessione ricorrente, della connessione dallo stato al output e dal input al output.
- $b,b_{out}$ è il bias e il bias del output,
- $f(\cdot),f_{out}(\cdot)$  sono [[Funzioni di attivazione|funzione di attivazione]] dello stato e del output.t 

![[Pasted image 20250207233930.png]]


## Assunzioni dei Modelli di Reti Neurali Ricorrenti (RNN)

Le __Reti Neurali Ricorrenti (RNN)__ si basano sulle seguenti assunzioni:

- **Causalità**: Un sistema è causale se l'output al tempo $t_0$ (o nodo _v_) dipende solo dagli input al tempo $t < t_0$ (dipende solo da _v_ e dai suoi discendenti). Questo è necessario e sufficiente per avere uno **stato interno**.
- **Stazionarietà**: Invarianza temporale (dopo l'addestramento del modello), ovvero la funzione di transizione dello stato $\tau$ è indipendente dal nodo $v$ della sequenza. Ciò significa che $\tau$ è la stessa in qualsiasi tempo $t$, indipendentemente dalla dimensione delle sequenze. Questa proprietà è utile per elaborare dati di lunghezza variabile mantenendo una dimensione fissa del modello.
- __Adattività__: Le funzioni di transizione sono realizzate da una rete neurale con __parametri liberi__ (pesi), i quali vengono appresi dai dati.




#### Algoritmi di learning
su una __rete ricorrente__ si può applicare l __unfolding__ ( o unrolling) che consiste replicare la stessa rete una collegata al altra in modo da costruire una [[Reti neurali Feed-Forward (FF)|feed forward]]. 
in questo modo i pesi di un layer al successivo sono condivisi (__weight sharing__) e le due reti sono totalmente equivalenti. 
![[Pasted image 20250207234512.png]]

l' addestramento viene fatto tramite **Backpropagation Through Time (BPTT)**, che applica la __[[backpropagation|backpropagation]]__ su una versione __unfolded__ equivalente della rete che si vuole allenare, limitando la profondità di unrolling con un iperparametro.

Durante la __BPTT__ i gradienti possono diminuire esponenzialmente, rendendo difficile l'apprendimento di **dipendenze a lungo termine**. Questo fenomeno è dovuto alla moltiplicazione ripetuta della matrice dei pesi ricorrenti:  I valori  della matrice $\hat{W}$ vengono moltiplicati tra di loro $n$ volte quanti sono i vettori di ingresso perciò il valore del peso e’ $w^n$ quindi si ha che:
- con $w<1$  __vanishing gradient__ il gradiente diventa troppo piccolo per fare degli spostamenti 
- con $w>1$ __exploding gradient__ gradiente diventa troppo grande per spostarsi senza “mancare” il minimo
Questa problematica è stata mitigata con altre architettura come la  [[RNN - Long Short-term Memory (LSTM)|LongShort-term Memory]] e dalle [[RNN - Gated reccurrent unit (GRU)|GRU]] e i [[RNN - Transformer|transformers]]



