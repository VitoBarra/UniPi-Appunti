---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---

# Alberi di decisione
---
modello di [[Concetti generali del Machine Learning|machine lerning]] [[Modelli di machine learning NON parametrici|non parametrico]] per imparare degli [[Albero di decisione|Albero di decisione]] per il [[Concept Learning|concept Learning]]

sono espressi come [[Forma normale disgiuntiva (DNF)|Disgiungzione di congiunzioni]]. quindi una sequenza di clausole tutte in  _and_ unite da _or_. essenzialmente regole  _if else_

>[!example]-
>![[E468986E-BCC7-462A-997B-E6C0426953DF.jpeg]]


### Algoritmo ID3
dati 
- $X$: gli esempi di training
- $T$: l attributo target
- _Attrs_: altri attributi, inizialmente tutto gli attributi
 
$IDA(X,T,attrs)$
1. crea il nodo radice
2. __if__ tutti gli in $X$ sono positivi, __return__ la calasse+
3. __if__ tutti gli in $X$ sono negativi, __return__ la classe -
4. __if__ Attrs è vuoto __return__  radice con la stessa classe della più comune in $X$
5. __else__
	1. $A \leftarrow$ _migliore attributo_; attributo di decisione per la radice $\leftarrow A$
	2. __for each__ possibile valore $v_i$ di _A_
		1. aggiungi un nuovo ramo sotto la radice dove
		2. $X_i \leftarrow$ sotto insieme di $X$ con $A +v_i$
		3. __if__ $X_i$  è vuoto aggiungi un nuovo nodo con classe il valore più comune di $T$ in $X$
		4. __else__ aggiungi il sotto albero generato da $ID3(x_i,T,attrs-\{A\})$
6. __return__ root
 
## Selezionare il migliore attributo 
#### Entropia
Si utilizza la nozione di _[[Entropia in teoria del informazione|entropia]]_ usata in [[Teoria del informazione (TDI)|Teoria del informazione]]
questa misura l _impurità_ di una collezione di esempi, dipende dalla distribuzione della [[Variabili Aleatorie (Casuali)|variabile aleatoria]] $p$
- $S$ è una collezione di Training example
- $p_+$ è la porzione _positiva_ in $S$
- $p_-$ è la porzione _negativa_ in $S$
l entropia è definita come 
$$Entropy(S)\equiv -p_+log_2(p_+)-p_-log_2(p_-) $$
dove $p = \cfrac{ncasi}{ntotali}$
con questa definizione più il numero dei casi positivi e negativi si equivalgono più $Entropy$ tende ad 1. con $Entropy(S)=1$ la collezione è molto impura e l _omogenosita_ è bassa 
- $0 \leq p \leq 1$
- $0 \leq entropy \leq 1$
- assume $0log_2(0)=0$

![[2589D1C6-6FAC-48B8-B665-411E979FCDBD.jpeg]]

#### Information gain 
l _information gain_ è la riduzione attesa del entropia data dalla [[Partizione di un insieme]] degli esempi su un attributo $A$.
$$Gain(S,A) = Entropy(S)-\sum_{v \in Values (A)}\frac{|Sv|}{|S|}Entropy(Sv)$$
dove  
- $Values(A)$ sono i possibili valori per l attributo $A$
- $Sv$ sotto insieme di esempi di $S$ dove $A$ ha valore $v$ (_somma pesata_)

#### scelta 
più è altro il valore di _gain_  più è efficacia l attributo nel classificare i dati di training, più è alta l _omogeneità_ più una scelta ci da una chiara classificazione. detto questo sappiamo che per scegliere il _miglior attributo_ dobbiamo _massimizzare_ il $gain$ ovvero dobbiamo fare la scelta che abbassa maggiormente l $entropy$

### Problema con gain
gain favorisce gli attributi con molte possibili valori, un esempio potrebbe essere l attributo “Date”. 
- questo caso da massimo gain per ogni scelta siccome divide in tanti sub set quanti i giorni considerati e potrebbe essere classificato _chiaramente_ quindi l entropia è 0
	- da quindi overfitting 
- non è _utile_ non funzione con dati nuovi 
-   ![[53FBA723-0E74-45AA-A4CB-53F8ABC9D6FE.jpeg]]
per evitare questo problema si utilizza un altra metrica il _GainRation_
$$GainRatio(S,A)= \frac{Gain(S,A)}{SplitInformation(S,A)}$$
dove 
$$SplitInformation(S,A)=-\sum^C_{i=1}\left(\frac{|S_i|}{|S|}log_2\frac{|S_i|}{|S|}\right)$$
dove 
- $S_i$ sono i set ottenuto partizionando su un valore $v_i$ di $A$ fino a $c$ valori
$SplitInformation$ misura l entropia di $S$ in rispetto del valore di $A$. più i valori sono _uniformemente dispersi_ più è alto il valore  

cosi facendo $GainRatio$ penalizza gli attributi che dividono gli esempi in tante piccole classi 

### Problema con Gain-ration
$SplitInformation$ può essere 0 o molto piccolo con $|S_i| \approx |S|$ 
- casi estremi con $|S_1| =0 \ \ |S_2|=n$
- $SplitInformation = -[\frac{0}{n}log(\frac{0}{n}) +\frac{n}{n}log(\frac{n}{n}) ] = -0-0 =0$

per risolvere questo problema si usa l euristica del 
1. calcolare $gain$ per ogni attributo
2. Applicare $GainRatio$ per gli attributi con $gain$ sopra la media


### Analisi di ID3
- lo spazio delle ipotesi di ID3 è _completo_. si possono rappresentare tutte le funzioni discrete
- la ricerca mantiene una singola ipotesi corrente ([[Ricerca Hill Climbing|hill-Climbing]])
- _no backtracking_: ottimo non garantito
- usa tutte gli esempi disponibili
- puo terminare prima, accetta classi perturbate 


## bias per DT
1. si preferiscono alberi corti rispetto a quelli lunghi
	1. dato dal fatto di andare da un caso semplice ad uno complesso 
	2. _non basta_  questo bias  è lo stesso di una semplice [[Ricerca in ampiezza BF|breath first ]] che esplora tutto l albero e sceglie il percorso piu corto
2. si _preferiscono_ albero che hanno atributi con alto gain vicino alla radice 
 
>[!note] restizione sulla ricerca
>la restrizione dei Bias non è sulla spazio delle ipotesi ma sulla _strategia  ricerca_ 

## Overfitting con DT
considerando l errore del ipotesi $h$
- dati di training: $errore_d(h)$
- intera distribuzione dei dati $X$: $error_x(h)$
 l ipotesi $h$ fa overfitting sui dati di training se c è un  un altra ipotesi $h’\in H$ tale che
$$
\begin{array}{}
error_D(h) <error_D(h’) & and \\
erorr_x(h’) <error_X(h)
\end{array}$$
$h’$ lavora peggio sui dati di training e meglio su i dati non visti 
![[645DF648-3E36-464B-9384-C57595A38CE7.jpeg]]


### ridurre l overfitting
per ridurre il fenomeno del overfitting si possono fare due cosi 
- impedire la crescita del albero. fare quindi _early stoppign_
- permetter al albero di fare _overfitting_ e  fare post-punt 

per valutere gli effetti ci sono varie strade
- dividere in due set i dati di training. uno di _training_ uno di _validazione_
	- valutare su entrambi  per valutare le due strategie
- usare test statistici per stimare l effetto del pruning 
-  Minimum description length principle : the tree sets) uses a measure of complexity of encoding the DT and (misclassified) examples, and halt growing the tree when this encoding size is minimal

### Pruning
il pruning consiste nel rimuovere un sotto albero, il nodo radice di quel sotto albero diventa una foglia e gli viene assegnata la classificazione piu comune. 
-  ogni nodo puo essere tagliato
- un nodo viene tolto solo se _non_ performa peggio sul _validation set_ 
- i nodo sono tagliati interativamente. ad ogni iterazione si toglie il nodo la cui rimozione aumenta di piu l acuracy 
- si _smette_ di fare pruning quando non ci sono piu nodi che se tagliati migliorano l _accuracy_
![[035477F2-E7BA-4AF8-BA56-58843ADE5736.jpeg]]


### Rule Post-Pruning
1. care un albero di decisione sul _training set_
2. convertire l albero in regole equivalenti
	1. ogni percorso corrisponde ad una regola
	2. ogni nodo sul percorso corrisponde ad una precondizione
	3. ogni _foglia_ corrispode ad una post condizione
3. fare _pruning_ sulle regole rimuovendo le precodizioni che aumentano l accuracy
	1. sul set di validazine
	2. sul set di training con una euristica
4. ordina le regolo in ordine stimato di accuracy, e confidare le in sequenza quando bisogna classificare un nuovo dato 


### perchè in regole?
- ogni percorso genera una regola: una condizione puo essere rimossa sulla base del contesto locale
- fare _pruning_ sulle regole è specifico  per un percorso mentre farlo sul albero è da un cambiamento globale
- convertire in regole le rendere piu leggibile per l umano
 
## attributi con valore continuo
quandi si gestiscono atributi continui si _discretizando_ per poterci lavorare
per ogni attributo continuo $A$ si genera dinamicamente l attributo $A_c$ definito come
$A_c =$ true if $A<c$ else false
per determinare il parametro $c$ si prendere la media di valori consecutivi dove la classificazione è _cambiata_

	
### valori mancanti
analizziamo il caso in cui i valori di alcuni atributi manchino.

si attuano delle strategia per indovinare il valore
1. Si scegli il piu comune tra i valori di quel attributo dei dati d esempio che classificano nello stesso modo 
2. assegna una probabilità $p_i$ ad ogni valore $v_i$, basato sulla frequenza e assegna il valore casualmente tenendo conto della distribuzione 
3. classifica il nuovo esempio  con la classificazione piu probabile 


### Attributi con costo 
gli atributi potrebbero avere un costo associato: e potremmo proferire un albero che ha il costo piu basso 
![[FB0282FB-4687-4CC1-B845-BB16961D1C2D.jpeg]]

### Vista giometrica

![[C3F91C3D-9A2C-49FF-9595-AE8DAE000409.jpeg]]

