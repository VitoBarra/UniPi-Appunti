---
Course: "[[Quantum Computing (QC)]]"
topic: nota
tags:
  - QC
---

# Quantum computing
---
il _quantum coputing_ è un [[Nozione di Calcolabilità|modello di calcolo]] che fa utilizzo dei fenomeni della [[Meccanica quantistica|Meccanica quantistica]]. inizialmente è stato inventato per studiare il funzionamento dei quanti ma ad oggi ha attirato gli interessi delle altre applicazioni informatiche.


l unita di rappresentazione del _computer quantico_ è il _qubit_ è analogo al normale _bit_ 
Abbiamo che un _qubit_ è ha due stati $| 0 \rangle$ e $|1\rangle$ che corrispondono a i normali stati del _bit_
$$| 0 \rangle = \begin{pmatrix}1  \\0\end{pmatrix} \ \ \ \ \ |1\rangle = \begin{pmatrix}0  \\1\end{pmatrix}$$
ma il _qubit_ può essere in uno stato diverso da questi soli due essendo possibile la _sovrapposizione_ abbiamo che lo stato del _qubit_ è rappresentato come
$$| \uppsi \rangle = \alpha | 0 \rangle + \beta | 1 \rangle = \alpha\begin{pmatrix}1  \\0\end{pmatrix} +\beta \begin{pmatrix}0  \\1\end{pmatrix} =\begin{pmatrix}\alpha  \\ \beta\end{pmatrix}$$
dove $\alpha,\beta \in \mathbb{C}$ e $|\alpha|^{2}+|\beta|^{2}=1$ e gli stati $| 0 \rangle$ e $|1\rangle$ sono chiamati _stati base computazionali_ e formano una base [[Base Ortogonale e Ortonormale|Base Ortogonale]] dello [[Spazio Vettoriale|spazio vettoriale]] $\mathbb{C}^{2}$

![[Pasted image 20230820164306.png]]

Se un registro di $n$ _bit_ può conservare $n$ bit di informazione un registro di $n$ _qubit_ conservare $2^{n}$  _bit_ di informazioni (ovvero tutte le [[Combinatoria|sequenza]] costruibili con 2 simboli), questo avviene siccome in _qubit_ è in sovrapposizione tra $2$ stati e quindi $n$ qubit sono in sovrapposizione di $2^{n}$ stati 
Non si possono pero leggere contemporaneamente tutte le configurazioni siccome _durante la lettura_ interverrà il fenomeno di _decoerenza_  che farà collassare il valore e ogni _qubit_ nel  in uno stato 
- $| 0 \rangle$ con [[Definizione di Probabilita|probabilità]] $|\alpha|^{2}$ 
- $| 1 \rangle$ con [[Definizione di Probabilita|probabilità]] $|\beta|^{2}$
restituendo cosi un risultato _classico_ in _bit_. 
una volta letto il registro tutta l informazione sulla _superposizione_ è _persa_ rileggere il registro piu volte dara sempre lo stesso risultato della prima lettura.

>[!warning]
>i valori $\alpha$ e $\beta$ sono valori ignoti e cercare di misurare il qubit per scoprirli distrugge questi valori siccome avviene la _decoerenza_


### Algoritmi quantistici 
l idea del _quantum computing_ e degli _algoritmi quantistici_ è quella di far divergere questi $2^{n}$ in uno stato che è soluzione del problema che vogliamo risolvere.

Un algoritmo quantistico segue queste procedure
- Si inizia con un stato conosciuto es. $n$ _qubit_ a $| 0 \rangle$  
- Il sistema evolve in _modo quantistico_: i qubit sono connessi tra loro attraverso _circuiti logici elementari_ e vengono manipolati mediante un semplice insieme di regole (_rotazioni del vettore_ che rappresenta lo stato quantico).
- ![[Pasted image 20230820170134.png]]
- Quando la macchina _misura lo stato finale_, la sovrapposizione dei risultati collassa sull'unico risultato con la _probabilità più alta_.
- Questa misurazione, darà con _alta probabilità la soluzione del problema_.

> [!warning]
> va tenuto a mente che guardare lo stato del sistema troppo presto rovina completamente la computazione, va guardato solo lo stato finale. questo una volta generato comunicherà con l sterno tramite i normali _bit_



### Capacita di calcolo
Il _quantum computing_ non viola la [[Tesi di Church-Turing|Tesi di Church-Turing]] siccome è potente quanto la macchia di turing e non riesce quindi a calcolare efficientemente i problemi $NP$-complete, ma ci sono certi problemi che il _quantum computing_ risolve velocemente  mentre la computazione con un sistema classico è esponenziale. 

#### classe di complessità BQP
_BQP_  (_bounded-error quantum polynomial_) è la classe di problemi risolubili con un algoritmo quantistico in tempo polinomiale con errore $<\cfrac{1}{2}$

Si crede  crede che per questa classe valga che 
- $\mathbf{P} \subset \mathbf{BQP}$ 
-  $\mathbf{BQP} \cap \mathbf{NPC} = \emptyset$
![[IMG_0608.jpeg]]

un esempio di problemi che appartengono alla classe BQP sono  
- [[Algoritmo di Shor|algoritmo di Shor]] per la [[Funzioni One-Way Trapdoor|fattorizzazione in numeri primi]]  che ha [[Complessita|tempo polinomiale]] mentre su i sistemi classici ha tempo esponenziale
-  [[Grover’s quantum search|Grover’s quantum search]] per la ricerca in un [[Data Base (DB)|database]] non strutturato che ha complessità $O(\sqrt{N})$ dove $N$ è il numero di entry mentre in un sistema normale la complessità è $N$ al caso pessimo e $\frac{N}{2}$ nel caso medio



### Evlouzione del quantum computing 
![[Pasted image 20230820171554.png]]
La _Quantum supremacy_ o _quantum advantage_ è l'obiettivo di dimostrare che un dispositivo _quantistico programmabile_ può risolvere un problema che nessun computer classico può risolvere in un periodo di tempo fattibile (indipendentemente dall'utilità del problema). 
La _supremazia quantistica implica_: 
- L'aspetto ingegneristico di costruire un potente computer quantistico
-  L'aspetto teorico di trovare un problema che può essere risolto da quel computer quantistico e che ha un vantaggio di velocità super polinomiale rispetto all'algoritmo classico migliore o possibile noto per quel compito.
  
   >[!nota] 
>Implementare l'[[Algoritmo di Shor|algoritmo di Shor]] per _numeri grandi_ è irrealizzabile con la tecnologia attuale, quindi l'algoritmo di Shor _non_ può essere utilizzato per dimostrare la supremazia quantistica.


#### Hardware
![[Pasted image 20230820172721.png]]

I _qubit_, come i bit, sono realizzati come sistemi fisici effettivi. Possono essere utilizzati molti diversi sistemi fisici.
Un _qubit_ può essere realizzato
- come le due diverse polarizzazioni di un fotone, 
- come l'allineamento di uno spin nucleare in un campo magnetico uniforme
- come i due stati di un elettrone che orbita attorno a un singolo atomo nel modello atomico: 
	- l'elettrone può trovarsi nello stato cosiddetto "fondamentale" o "eccitato", che chiameremo rispettivamente $|0\rangle$ e $|1\rangle$,
	-  irradiando l'atomo con luce, con energia appropriata e per un tempo adeguato, è possibile spostare l'elettrone dallo stato $|0\rangle$ allo stato $|1\rangle$ e viceversa
	-  ma in modo più interessante, riducendo il tempo di esposizione alla luce, un elettrone inizialmente nello stato |0⟩ può essere spostato a metà strada tra $|0\rangle$ e $|1\rangle$. 


![[Pasted image 20230820173041.png]]

![[Pasted image 20230820173619.png]]
![[Pasted image 20230820173637.png]]

per costruire un computer quantistico_ e assicurarsi che il suo stato non venga influenzato da varie fonti di errore.

_Le operazioni quantistiche_:
	le rotazioni non sono mai perfette. Un'operazione intesa a ruotare un qubit di 90 gradi potrebbe finire per ruotarlo di 90,1 o 89,9 gradi. Tali errori si accumulano rapidamente, portando a un output completamente errato.
    
_[[Meccanica quantistica|Decoerenza]]_: 
	I qubit perdono gradualmente le informazioni che contengono perché interagiscono con l'ambiente in qualche misura. Per preservare lo stato di un qubit, deve essere perfettamente isolato; una condizione che in generale può essere mantenuta solo per un periodo di tempo molto breve, dopo il quale lo stato quantistico va perduto.
	    
I codici di correzione degli errori quantistici sono essenziali per costruire grandi computer quantistici, insieme a protocolli tolleranti agli errori che descrivono come eseguire calcoli su _qubit_ codificati. Il loro utilizzo implica l'inserimento di un numero molto elevato di qubit aggiuntivi.

_Dimensioni dei circuiti_:
	Gli algoritmi quantistici noti richiedono molto _qubit_ per risolvere problemi di dimensioni pratiche nell'informatica. La fattorizzazione di un numero mediante l [[Algoritmo di Shor|algoritmo di Shor]] richiede un circuito con $O(n^{2}\log n \log \log n)$ porte quantistiche elementari., ovvero un numero troppo grande per le grandezze pratiche del informatica

### Altri fenomeni 
Un altro fenomeno utilizzabile nella Computazione quantistica è la _polarizzazione dei fotoni_. questo possono avere infinito valori ma ridotto a due per poter assegnare valori binari.
