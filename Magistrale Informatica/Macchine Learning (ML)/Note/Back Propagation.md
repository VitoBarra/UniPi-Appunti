---
Course: "[[Machine Learning (ML)]]"
tags:
  - IIA
  - ML
Area: "[[Reti Neurali (NN)]]"
topic: 
SubTopic:
---
# Back Propagation
---
La __Back Propagation__ è un algoritmo che permette di allenare delle [[Reti Neurali (NN)|reti neurali]] utilizzando il [[Tecnica di ottimizzazione Gradient Descent|gradient descent]] e quindi è formulato come [[Problemi di ottimizzazione|problema di minimizzazione]]: trovare i pesi $w$ che minimizzano l'errore totale $E_{\text{tot}}$. 


In particolare vediamo la derivazione del algoritmo considerando un [[Reti neurali Feed-Forward (FF)|MLP]]  [[Reti Neurali (NN)|completamente connessa]]. 
![[Pasted image 20250101225508.png]]
Gli indici $k, j, i$ rappresentano i diversi strati della rete.

In questo tipo di rete è importante stimare il contributo delle unità nascoste all'errore a al livello di output.  


Si può scegliere una qualsiasi funzione di errore e il risultato finale non cambia. Per semplicità di calcolo si è scelta la __MSE__ e quindi : $$E_{\text{tot}} = \sum_{p} E_p, \quad E_p = \frac{1}{2} \sum_{k} (d_k - o_k)^2
$$
dove $p$ rappresenta un pattern di input.
```pseudo
	\begin{algorithm}
	\caption{Back-Propagation}
	\begin{algorithmic}
	\state initialte all the weights $\mathbf{w}$ in the network ans $\eta$
	\state Compute units outputs and $E_{tot}$
	\While{ $E_{tot} > \varepsilon$ } 
			\State $\Delta \mathbf{w}=-\cfrac{\partial E_{tot}}{\partial \mathbf{w}}$ 
		\State $\mathbf{w} ^{new} = \mathbf{w} + \eta \Delta \mathbf{w}$
		\state Compute units outputs and $E_{tot}$
    \EndWhile
	\end{algorithmic}
	\end{algorithm}
```

Per eseguire l'algoritmo si ha bisogno di calcolare il gradiente di $E_{tot}$ rispetto a $\mathbf{w}$, e riscrivendola in termini di ogni singolo patter $p$, si ha: $$\frac{\partial E_{\text{tot}}}{\partial \mathbf{w}} = \sum_p \frac{\partial E_p}{\partial \mathbf{w}} $$Usando la [[Derivate|derivata parziale]] di $E_p$ rispetto ogni peso  $w_{tu}$, dove $t$ rappresenta l'unità di destinazione e $u$  l'unità di origine, abbiamo che la regola di aggiornamento è:
$$ \Delta w_{tu} = - \frac{\partial E_p}{\partial w_{tu}} $$sviluppando la derivata, utilizzando la chain rule, otteniamo :$$ \begin{array}{}
\cfrac{\partial E_p}{\partial w_{tu}}  & = &  \cfrac{\partial E_p}{\partial \text{net}_t} \cdot \cfrac{\partial \text{net}_t}{\partial w_{tu}}  & = \\
 & = &  \delta_t \cdot o_u
\end{array}
$$ In quanto: $$\begin{cases}
\text{net}_t = \sum_s w_{ts} o_s \\
o_t = f_t(net_t)
\end{cases}\implies \frac{\partial \text{net}_t}{\partial w_{tu}} = \cfrac{\partial \sum_s w_{ts} o_s}{\partial w_{tu}} =o_u$$perché solo il termine dove  $s=u$ contribuisce e gli altri hanno derivata $=0$.


Il termine $\delta_t$ lo si può continuare a scomporre con la chain rule e si ottiene che: $$  \begin{array}{}
  \delta_t  & = &  \cfrac{\partial E_p}{\partial \text{net}_t} &  =   \\ 
  &  & \cfrac{\partial E_p}{\partial o_t} \cdot \cfrac{\partial o_t}{net_t}  &  \overset{o_t=f_t(net_t)}{=}   \\ 
  &  & \cfrac{\partial E_p}{\partial o_t} \cdot f'(net_t)
\end{array}
 $$Il valore di $\delta_t$ dipende dal tipo di unità, se di output o nascosta, e bisogna valutarne il rispettivo $\frac{\partial E_p}{\partial o_t}$.
 
 __Unità di output ($t = k$)__: $$ 
\begin{array}{}
 & -\cfrac{\partial E_p}{\partial o_k}  & = &  -\cfrac{\partial\left( \cfrac{1}{2} \sum_{k=1}^K (d_k - o_k)^2 \right)}{\partial o_k}  & =  & (d_k - o_k) \\
  \implies &    \delta_k  & =    &   (d_k - o_k) \cdot f_k'(\text{net}_k)
 
\end{array}
$$
Dove $K$ è il numero di neuroni d'output. 

__Unità nascosta ($t = j$)__: $$
\begin{array}{}
 & \displaystyle-\cfrac{\partial E_p}{\partial o_j} & = & \displaystyle  \sum_{h=1}^H -\frac{\partial E_p}{\partial \text{net}_h} \cdot \frac{\partial \text{net}_h}{\partial o_j}  & = &  \displaystyle \sum_{h=1}^H \delta_h \cdot w_{hj}\\
 \implies &  \delta_j & = &  \displaystyle\left( \sum_{k=1}^H \delta_h \cdot w_{hj} \right) \cdot f_j'(\text{net}_j)
\end{array}
$$Dove $H$ è il numero di neuroni del layer successivo.


![[Pasted image 20250103181501.png]]

Possiamo notare che il termine $-\cfrac{\partial E_p}{\partial o_j}$ lo abbiamo già calcolato nello step precedente e quindi lo possiamo riusarlo, ad esempio usando la [[Programmazione Dinamica|programmazione dinamica]]. 
Grazie a questo riutilizzo, ogni $\delta$ viene calcolato una sola volta e utilizzato per ogni neurone del layer precedente, rendendo il numero di operazioni proporzionale al numero di pesi $O(|W|)$.
 
### Aggiornamento dei pesi 
Una volta calcolati $\delta_t$ e  $o_u$, possiamo aggiornare i pesi: $$ \Delta w_{tu} = - \frac{\partial E_p}{\partial w_{tu}}= -\delta_t \cdot o_u $$ E quindi: $$ w_{\text{new}} = w - \eta \cdot \delta_t \cdot o_u $$

![[Pasted image 20250103181525.png]]

### Considerazioni
Questa è la versione [[Tecnica di ottimizzazione Gradient Descent|online]] del algoritmo dove l aggiornamento si fa per ogni patter. 
in generale i gradienti possono essere accumulati e poi sommati o mediati prima di essere applicati.
- __Somma__ : funziona ma tende il gradiente tende ad esplodere a seconda della dimensione del mini-batch o del batch, solitamente  richiede un learning rate più basso.
- __Media__: Tende a dare risultati più stabili e rende il training più indipendente dagli iper-parametri.