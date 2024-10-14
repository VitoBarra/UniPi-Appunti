---
Subject: "[[Data Base (DB)]]"
topic: nota
tags:
  - DB
---
# Algebra Relazionale - Trasformazione di espressioni
---
#### Proprietà delle operazioni 
Un’espressione dell’algebra relazionale puo essere trasformata in un’altra equivalente sfruttando alcune proprieta degli operatori. Queste trasformazioni sono utili perche possono ridurre di ordini di grandezza il costo di esecuzione delle espressioni (riscrittura algebrica).
Si consideri la rappresentazione di un’espressione algebrica come un albero le cui foglie siano le relazioni e i nodi interni sono gli operatori dell’algebra; i figli di un nodo interno N sono gli operandi dell’operatore associato al nodo N
![[IMG_1059.jpeg]]

L’idea alla base della riscrittura algebrica e di anticipare l’applicazione degli operatori di proiezione e restrizione rispetto al prodotto e alla giunzione (spostamento verso le foglie della proiezione e restrizione), in modo da ridurre la dimensione dei risultati intermedi. 
Poiché la restrizione e' l’operatore che in generale produce una relazione con un numero di ennuple inferiore rispetto a quello della relazione a cui viene applicato, le proprietà piu utili dell’algebra relazionale sono quelle che consentono di anticipare l’operatore di restrizione. E anche utile anticipare l’operazione di proiezione rispetto al prodotto e alla giunzione, perché una proiezione riduce la dimensione delle ennuple dell’operando ed elimina eventuali ennuple uguali dal risultato.
Indicando con $E$ un’espressione dell’algebra relazionale, esempi di regole su cui si
basa la riscrittura sono:
1. Raggruppamento di restrizioni: 
	- $\sigma_{\phi_X}(\sigma_{\phi_Y}(E)) = \sigma_{\phi_X \land \phi_Y}(E)$
	dove $\sigma_{\phi_X}$ e' l’operatore di restrizione con condizione sull’insieme di attributi  $X$
2. Commutatività della restrizione e della proiezione: 
	- $\pi_Y(\sigma_{\upphi_X}(E)) = \sigma_{\upphi_X}(\pi_Y(E))$, se $X \subseteq Y$.
	Se la condizione interessa attributi $X \not\subseteq Y$, allora vale:
	- $\pi_Y(\sigma_{\upphi_X}(E)) = \pi_Y(\sigma_{\upphi_X}(\pi_{XY}(E)))$.
3. Anticipazione della restrizione rispetto al prodotto e alla giunzione
	- $\sigma_{\upphi_x}(E_1 \times E_2) = \sigma_{\upphi_X}(E_1) \times E_2$,
	- $\sigma_{\upphi_X}(E_1 \bowtie E_2) = \sigma_{\upphi_X}(E_1) \bowtie E_2$,
	se $X$ sono attributi di $E_1$.
	- $\sigma_{\upphi_X \land \upphi_Y}(E_1 \times E_2) = \sigma_{\upphi_X}(E_1) \times \sigma_{\upphi_Y} (E_2)$
	- $\sigma_{\upphi_X \land \upphi_Y}(E_1 \bowtie E_2) = \sigma_{\upphi_X}(E_1) \bowtie \sigma_{\upphi_Y} (E_2)$
	se $X$ sono attributi di $E_1$ ed $Y$ sono attributi di $E_2$.
	- $\sigma_{\upphi_X \land \upphi_Y \land \upphi_J}(E_1 \times E_2) = \sigma_{\upphi_X}(E_1) \underset{\upphi_J}{\bowtie} \sigma_{\upphi_Y} (E_2)$
	se $X$ sono attributi di $E_1$, $Y$ sono attributi di $E_2$ e $\upphi_J$ e' una condizione di giunzione `
4. Raggruppamento di proiezioni
	- $\pi_Z(\pi_Y(E)) = \pi_Z(E)$
	dove $\pi_Z$ e' l’operatore di proiezione sull’insieme di attributi $Z$, e $Z \subseteq Y$ in espressioni ben formate.
5. Eliminazioni di proiezioni superflue
	$\pi_Z(E) = E$,
	se $Z$ sono gli attributi di $E$
6. Anticipazione della proiezione rispetto al prodotto e alla giunzione
	- $\pi_{XY}(E_1 \times E_2) = \pi_X(E_1) \times \pi_Y(E_2)$
	- $\pi_{XY}(E_1 \underset{\upphi_J}{\bowtie} E_2) = \pi_X(E_1)\underset{\upphi_J}{\bowtie} \pi_Y(E_2)$,
	dove $X$ sono attributi di $E_1$, $Y$ sono attributi di $E_2$ e $\upphi_J$ la condizione di giunzione con attributi $J \subseteq XY$.
	- $\pi_{XY}(E_1 \underset {\upphi_J}{\bowtie} E_2) = \pi_{XY}((\pi_{XX_{E_1}}(E_1)) \underset{\upphi_J}{\bowtie}(\pi_{YX_{E_2}}(E_2)))$
	dove $X$ sono attributi di $E_1$, $Y$ sono attributi di $E_2$, $X_{E_1}$ sono gli attributi di giunzione di $E_1$ che non sono in $XY$ e $X_{E_2}$ sono gli attributi di giunzione di $E_2$ che non sono in $XY$.
7. Commutatività del prodotto e della giunzione
	- $E_1 \times E_2 = E_2 \times E_1$
	- $E_1 \underset{\upphi_J}{\bowtie} E_2 = E_2\underset{\upphi_J}{\bowtie} E_1$
8. Associatività del prodotto e della giunzione
	- $(E_1 \bowtie E_2) \bowtie E_3 = E_1 \bowtie (E_2 \bowtie E_3)$,
	- $(E_1 \underset{\upphi_{J_1}}{\bowtie} E_2) \underset{\upphi_{J_2}\land \upphi_{J_3}}{\bowtie} E_3 = E_1 \underset{\upphi_{J_1}\land \upphi_{J_3}}{\bowtie} (E_2 \underset{\upphi_{J_2}}{\bowtie} E_3)$,
	dove $\upphi_{J_2}$ contiene attributi solo di $E_2$ e $E_3$. Se mancano le condizioni di giunzione, ne segue che anche il prodotto $\times$ e associativo. `
9. Commutatività degli operatori insiemistici
	- $E_1 \cup E_2 = E_2 \cup E_1$
	- $E_1 \cap E_2 = E_2 \cap E_1$
	- $E_1 - E_2 \not= E_2 - E_1$
10. Associatività degli operatori insiemistici
	- $(E_1 \cup E_2) \cup E_3 = E_1 \cup (E_2 \cup E_3)$
	- $(E_1 \cap E_2) \cap E_3 = E_1 \cap (E_2 \cap E_3)$
1. Anticipazione della restrizione rispetto agli operatori insiemistici
	- $\sigma_{\upphi_X}(E_1 - E_2) = \sigma_{\upphi_X} (E_1) - \sigma_{\upphi_X}(E2)$
	l’equivalenza vale anche sostituendo $-$ con $\cup$ o $\cap$. Mentre
	- $\sigma_{\upphi_X}(E1 - E2) = \sigma_{\upphi_X}(E_1) - E_2$
	vale anche sostituendo $-$ con $\cap$, ma non con $\cup$.
12. Anticipazione della proiezione rispetto agli operatori insiemistici
	- $\pi_X(E_1 \cup E_2) = (\pi_X(E_1)) \cup (\pi_X(E_2))$


Esistono altre regole di riscrittura algebrica di espressioni che usano il _raggruppamento_, 
1. _l’anticipazione della proiezione rispetto al raggruppamento_:$\sigma_{\phi}(_A\gamma_F(E)) = _A\gamma_F(\sigma_\phi(E))$, se $\phi$ usa solo attributi in $A$.

#### Algoritmo
Un possibile algoritmo di riscrittura algebrica procede quindi secondo i seguenti
passi:
1. Si anticipa l’esecuzione delle restrizioni sulle proiezioni usando la regola 2 da destra verso sinistra (in tutti gli altri casi le regole verranno usate nell’altra direzione);
dato che la regola e usata in questa direzione, vale sempre la condizione  $X \subseteq Y$.
2. Si raggruppano le restrizioni usando la regola 1.
3. Si anticipa l’esecuzione delle restrizioni sul prodotto e sulla giunzione usando la regola 3.
4. Si ripetono i tre passi precedenti fino a che e possibile. `
5. Si eliminano le proiezioni superflue usando la regola 5.
6. Si raggruppano le proiezioni usando la regola 4.
7. Si anticipa l’esecuzione delle proiezioni rispetto al prodotto e alla giunzione usando ripetutamente la regola 2, ma solo nel caso in cui E e un prodotto o una giunzione, e la regola 6.

In generale, quindi, il risultato di questo algoritmo e un’espressione in cui la restrizione e la proiezione sono eseguite il piu presto possibile, e la restrizione e' anticipata rispetto alla proiezione. In particolare, nel caso di espressioni con una sola giunzione, l’espressione ottimizzata ha la forma:
$$\pi_{X_1}(\pi_{X_2}(\sigma_{\upphi_{Y_2}}(R)) \bowtie \pi_{X_3}(\sigma_{\upphi_{Y_3}}(S)))$$

![[IMG_1060.jpeg]]

