---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: "[[Concetti generali del Machine Learning]]"
topic: 
SubTopic:
---
# Rete di Percetroni
---
una __rete di percetroni__ è un [[Modelli di machine learning parametrici|modello parametro]] di [[Algoritmi di Machine Learning|machcine learning]]  del paradigma delle [[Reti Neurali (NN)|reti neurali]] 
può essere usato solo per risolvere problemi di classificazione binaria e si basa sul __percetrone__ ovvero un __neurone__ la cui [[Funzioni di attivazione|funzione di attivazione]] è  la funzione Threshold. 

![[Pasted image 20241226222224.png]]

con un __singolo percettrone__ si possono rappresentare tutte le __funzioni logiche__ AND, OR, NOT, NAND, NOR ma non la funzione XOR.

Questo avviene perché lo XOR non è una funzione [[Linearmente Separabili|linearmente separabile]] e quindi il percettrone fallisce. 


### Algoritmo di learning
Per una rete con un singolo per __percettrone__ l algoritmo di learning è il seguente: 
1. __Inizializza i pesi__ impostandoli a zero o a un piccolo valore casuale.  
2. __Seleziona un tasso di apprendimento__ $\eta$ (un numero compreso tra 0 e 1).  
3. __Fino al raggiungimento di una condizione di arresto__ (es. i pesi non cambiano):  

Per ogni pattern di addestramento $(\mathbf{x}, d)$ dove $d = +1$ o $d = -1$,   
- Calcola l'attivazione in uscita:  $$\text{out} = \text{sign}(w^T x) \quad [+1, -1]$$
   - __Se $\text{out} = d$:__  
     Non modificare i pesi  
   - __Se $\text{out} \neq d$:__  
     Aggiorna i pesi con la regola (__Hebbian learning__):$$w_{\text{new}} = w + \begin{cases}
+\eta \mathbf{x} & se & w^T \mathbf{x} \leq 0 & e &d = +1 \\
-\eta \mathbf{x} &se& w^T \mathbf{x} > 0 & e &d = -1
\end{cases}$$  
     riscrivibile anche come $w_{\text{new}} = w + \eta d\mathbf{x}$    
	 ![[Pasted image 20241227020044.png]]
	 O, equivalentemente nella forma forma (__delta rule__) :  $$w_{\text{new}} = w + \frac{1}{2}\eta \, \delta  \, x \ \ \ \ \ \ \delta=d - \text{out}$$
	    è questa è una regola di correzione degli errori che cambia i pesi sono in caso mal classificazione e in modo proporzionale al errore.
	 



### Teorema di convergenza del percettrone
l´algoritmo di learning di un __percettrone__ converge sempre ad una soluzione assumendo che lo spazio sia [[Linearmente Separabili|linearmente separabile]]. La soluzione non è unica e dipende dal punto di inizio. 



La Dimostrazione del teorema segue la seguente idea:
si dimostra che il numero di passi necessari per la convergenza  $q$ è un numero finito finito e questo si fa trovando un limite inferiore e superiore a $||w(q)||^2$.


__Sia__
- $(x_i, d_i)$ il training set con $d_i \in \{+1, -1\}$ per $i = 1, \dots, l$.  
- $\alpha = \min_i d_i (w^* x_i) > 0$ 
__Se__ il problema è [[Linearmente Separabili|linearmente separabile]],
__Allora__ esiste un vettore soluzione $w^*$ tale che:  $$ \mathbf{d}_i (w^* \mathbf{x}_i) \geq \alpha >0$$ e quindi vale che $$ \mathbf{w}^* (d_i\mathbf{x}_i) \geq \alpha >0$$e possiamo definire $x_i' = d_i x_i$. Allora il problema si riduce a:  $$ w^* x_i' \geq \alpha > 0 $$ e abbiamo che $w^*$ è soluzione per $(x_i,d) \iff w^*$  è soluzione per $(x'_i,+1)$ ovvero per il dataset comporto dalle coppie $(x'_i,+1)$  che ha solo patter positivi.


__Sia__ 
- $w(0) = 0$, il punto di inizio del algoritmo.
- $\eta = 1$  il learning rate (costante).

L'algoritmo aggiorna i pesi solo sui pattern mal classificati ($d_i \neq \text{segno}(w x_i)$), con la regola:  $$ \mathbf{w}_{\text{new}} = \mathbf{w} + \eta d_i \mathbf{x}_i. $$ o equivalentemente $$ \mathbf{w}(j) = \mathbf{w}(j-1) + \eta d_i \mathbf{x}_i. $$
  
Nel caso $\eta=1$ e  pattern tutti positivi $d_i = +1$ la regola diventa semplicemente $\mathbf{w}(j) = \mathbf{w}(j-1) + \mathbf{x}_i$ e quindi al passo $q$ del algoritmo avremmo 
$$ \mathbf{w}(q) = \sum_{j=1}^q \mathbf{x}_{i_j}$$ dove $i_j$ denota gli indici dei pattern mal classificati.





__sia__
- $\beta = \max_i ||x_i||^2_2$, ovvero la il quadrato della [[Norme Matriciali e Norme Vettoriali|norma euclidea]] massima tra gli input.
- $\alpha = \min_i w^* x'_i > 0$ 

Allora per la ricerca del limite inferiore abbiamo  che 
   abbiamo che: $$(w^*)^T w(q)= (w^*)^T \sum_{j=1}^q \mathbf{x}_{i_j} \geq q\alpha$$  e dalla [[Diseguaglianza di Cauchy-Schwartz|disuguaglianza di Cauchy-Schwarz:]]  vale che: $$\|\mathbf{w}^*\|^2 \|\mathbf{w}(q)\|^2\geq ((w^*)^T w(q))^2 \geq (q \alpha)^2. $$ da cui segue che:  $$ ||w(q)||^2 \geq \frac{(q \alpha)^2}{||w^*||^2}. $$  ovvero il lower bound


Me per la ricerca del limite superiore:
   Espandendo $||w(q)||^2$ e applicando iterativamente la regola di aggiornamento:  $$ ||w(q)||^2 = ||w(q-1) + x_{i_q}||^2 = ||w(q-1)||^2 + 2 w(q-1) x_{i_q} + ||x_{i_q}||^2 $$  Per la $q$-esima iterazione, il termine $2 w(q-1) x_{i_q}$ è negativo, quindi togliendolo  vale$$ ||w(q-1)||^2 + ||x_{i_q}||^2 \geq ||w(q)||^2$$ da cui espandendo per iterazione fino a $w(0)=0$ abbiamo $$q \beta \geq   \sum_{j=1}^q ||x_{i_j}||^2 \geq ||w(q)||^2  $$
Da qui Combinando i abbiamo che risultati otteniamo:  $$ q \beta \geq ||w(q)||^2 \geq \frac{(q \alpha)^2}{||w^*||^2}$$ e semplificando abbiamo 
$$ q \beta \geq  \frac{q^2 \alpha^2}{||w^*||^2}$$ e ponendo $\alpha'= \cfrac{ \alpha^2}{||w^*||^2}$ si ha che $$q \beta \geq q^2\alpha'$$Da cui considerando che non si possono avere un numero negativi di step si ottiene un limite superiore per $q$:  
$$\frac{\beta}{\alpha'} \geq q \geq 0 $$
![[Pasted image 20241227055850.png]]
