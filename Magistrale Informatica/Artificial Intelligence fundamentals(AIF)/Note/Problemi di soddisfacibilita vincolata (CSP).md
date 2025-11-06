---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Problemi di soddisfacibilita vincolata (CSP)
---
Un **Problemi di soddisfacibile vincolata** (**CSP**) è caso particolare di un [[Problemi di ottimizzazione|problema di ottimizzazione]] dove la __funzione obiettivo__ è costate o assente ed è una generalizzazione di un [[Problemi della Sodisfacibilita (SAT)]] a domini non boolenani

si usa in situazioni in cui si vuole ottenere una soluzione ad che soddisfa in vincoli ma non si può applicare o non importa trovare una soluzione "ottima", ogni soluzione è egualmente valida.

La definizione canonica di **CSP** si articola in tre componenti fondamentali: 
- $X = \{X_1, X_2, \dots, X_n\}$ un insieme di **variabili**. 
- $D = \{D_1, D_2, \dots, D_n\}$ un insieme di domini, ogni $D_i$ è associato a una variabile corrispondente $X_i$ ed  è costituito da un [[Insiemi Matematici|insieme]] di valori ammissibili $\{v_1, v_2, \dots, v_k\}$ per la variabile $X_i$
- $C$ un **insieme di vincoli** che determinano le **combinazioni ammissibili** dei valori assegnati.

Ogni vincolo è formalmente espresso come $\langle scope, rel \rangle \in C$  dove 
- $scope$ è un  [[Insiemi Matematici|insieme]] che tiene le variabili  $(X_{i_1}, X_{i_2}, \dots, X_{i_k})$ che partecipano nella relazione
- $rel$ è una **relazione** tra variabili, la quale specifica le combinazioni di valori che soddisfano una determinata condizione logica o numerica In termini formali, una relazione è può essere espressa in modo esplicito un sottoinsieme del [[Prodotto Cartesiano|prodotto cartesiano cartesiano]] dei domini delle variabili coinvolte $\text{rel} \subseteq D_{i_1} \times D_{i_2} \times \dots \times D_{i_k}$ oppure in modo implicito con una **funzione** logica o aritmetica che risulta in un valore booleano.

I Risolvere un **CSP** significa trovare un **assegnamento alla variabile** $\{X_i = v_i, X_j = v_j, \dots\}$ è queste possono essere classificate in vario modo: 
- **consistente** o **legale**: Un’assegnamento che non viola alcun vincolo
- **completa**: se ogni variabile è stata **assegnata** altrimenti viene detta **parziale** 
se un assegnamento è **coerente è parziale** è detta **soluzione parziale** mentre se è **coerente è completa** allora è una soluzione del **CSP**. 

trovare la **soluzione di un CSP** è in generale un problema **[[Complessita|NP-completo]]**, sebbene esistano classi importanti di **CSP** che possono essere risolte in modo più efficiente.


###  Tipi di vincoli
I **vincoli** nei **problemi di soddisfacimento vincolati** (CSP) possono essere di vario tipo. In generale, si distinguono:
- **Vincoli unari**: restringono il dominio ammissibile di una singola variabile, limitando i valori che può assumere.
- **Vincoli globali**: coinvolgono un insieme arbitrario di variabili e consentono una modellazione più compatta. Un esempio classico è il vincolo $\text{Alldiff}$, che richiede che tutte le variabili coinvolte assumano valori distinti.


I vincoli possono essere rappresentati graficamente tramite **ipergrafi**, dove:
- I **nodi** rappresentano le variabili
- gli archi rappresentano i **constraint binari**
- Gli ipernodi rappresentano i vincoli $n$-ari

Ogni vincolo $n$-ario può essere trasformato in un insieme equivalente di vincoli binari attraverso:
- **Introduzione di variabili ausiliarie**, che semplificano il problema in termini binari
- **Grafo duale**, in cui:
  - Si crea una variabile per ogni vincolo originario
  - Si introducono vincoli binari tra tali variabili quando condividono variabili comuni
  - I domini delle nuove variabili sono insiemi di tuple che rispettano i vincoli iniziali

Nonostante la riduzione a vincoli binari sia sempre possibile, l'utilizzo diretto di vincoli globali come $\text{Alldiff}$ offre vantaggi significativi:
- Modellazione più chiara e compatta
- Possibilità di impiegare algoritmi inferenziali specializzati, più efficienti rispetto a quelli generici
 
ai CSP reali si può aggiungere dei **Vincoli di preferenza**, che introducono criteri qualitativi tra le soluzioni sono formalizzati attraverso **costi associati alle assegnazioni** e questo li trasforma nella forma generale di  **[[Problemi di ottimizzazione vincolata (COP)|problema di ottimizzazione vincolata (COP)]]**



### Classificazione CSP
i *CSP* possono essere classificati in vario modo a secondo dei tipi di variabili e tipi di vincoli, problemi con variabili con **domini discreti** e **finiti** , sono i **CSP** più semplici

variabili con **domini discreti** e **infiniti** ad esempio $D_i=\mathbb{Z}$ o delle stringhe. In questi casi la rappresentazione **esplicita** dei valori non è praticabile, rendendo necessario l’uso di **vincoli impliciti**. nel caso in cui ci siano solo **vincoli lineari** su **variabili intere** esistono algoritmi specializzati efficienti mentre il problema diventa [[Complessita|indecidibile]] se i vincoli sono **non lineari**.

### Inferenza
Per la risoluzione dei **Constraint Satisfaction Problems** (**CSP**) si utilizza il principio della **propagazione dei vincoli**, tecnica che sfrutta i vincoli definiti dal problema per ridurre i **domini delle variabili**. La riduzione di un dominio può propagarsi, inducendo ulteriori riduzioni nei domini di altre variabili collegate da vincoli, semplificando la ricerca o, in alcuni casi, portando direttamente alla soluzione. Tale approccio può essere impiegato sia in fase di ricerca sia come operazione preliminare di **preprocessing**.

La propagazione dei vincoli si fonda sul concetto di **consistenza locale**. Rappresentando il CSP come un [[Grafi|grafo]], in cui i nodi corrispondono alle **variabili** e gli archi ai **vincoli binari**, si procede progressivamente all'eliminazione dei valori incompatibili dai domini, seguendo diversi livelli di **consistenza locale**.

i livelli di consistenza sono: 
- **consistenza del nodo** (**node consistency**): Una variabile è detta **nodo-consistente** se tutti i valori del suo dominio rispettano i vincoli unari associati. 
- **consistenza del arco**: (**arc consistency**):  una variabile $X_i$ è detta **arco-consistente** rispetto a una variabile $X_j$ se, per ogni valore $v_i$ appartenente al dominio $D_i$, esiste almeno un valore $v_j$ nel dominio $D_j$ tale che la coppia $(v_i, v_j)$ soddisfi il vincolo binario tra $X_i$ e $X_j$. Formalmente riassumibile come $$\forall v_i \in D_i, \exists v_j \in D_j : (v_i, v_j) \in C_{ij}$$ per ridurre i domini in modo che siano **arco consistenti** si spesso usa L'[[Algoritmi|algoritmo]] **[[Algoritmo per consistenza archi AC-3|AC-3]]**
- **consistenza di percorso** (**path consistency**):  un [[Insiemi Matematici|insieme]] di due **variabili** $\{X_i, X_j\}$ sono dette **path-consistent** rispetto a una terza variabile $X_m$ se, per ogni assegnamento $\{X_i = a, X_j = b\}$ che soddisfa i vincoli binari, se presenti, tra $X_i$ e $X_j$, esiste almeno un valore per $X_m$ tale che siano soddisfatti i vincoli sia tra $\{X_i, X_m\}$ che tra $\{X_m, X_j\}$. formalmente la relazione si riassume come:$$
\begin{array}{}

\forall \, a \in D_i, \, \forall \, b \in D_j \mid (a, b) \in C_{ij}  \\
\implies \exists \, c \in D_m \, : \, (a, c) \in C_{im} \land (c, b) \in C_{mj}
\end{array}
$$il nome viene dal fatto che i domini sono consistenti sul percorso che collega $X_i,X_j$ e passa per $X_m$ Ci sono casi in cui i vincoli 
- **$k$-Consistenza** (**$k$-consistency**): la **$k$-consistenza** è la definizione di consistenza più generale. Un insieme di $k$ variabili $\{X_i,\dots ,X_k\}$  è detto $k$-consistente se, per ogni sottoinsieme di $k - 1$ variabili esiste un **assegnamento consistente** ed esiste un valore per la $k$-esima variabile che mantiene la **consistenza** rispetto a tutti i vincoli coinvolti. **la consistenza di nodo** corrisponde al $k=1$, **la consistenza di arco** corrisponde al caso $k = 2$, **la consistenza di percorso** se si hanno solo vincoli binari, corrisponde al caso $k = 3$. 
- **strong $k$-consistency** è una condizione più  forte della $k$-consistenza in quanto implica la $j$-consistenza  $\forall j \leq k$. 

con $n$ il numero di variabili e con $d$ il numero di valori consistenti per ogni variabile, la $k=n$-consistenza permette di cercare un **assegnamento soluzione** in $O(n^2d)$ che è molto meno di esponenziale nel numero di variabili $n$. Trovare questo tipo di consistenza in se pero ha [[Complessita|complessità]] esponenziale in $n$ sia in tempo che in spazio.


Per alcuni tipi di __vincoli globali__ si possono costruire algoritmi ad hoc per garantire la consistenza. Questi algoritmi sono spesso più efficienti rispetto alla trasformazione del vincolo in un insieme equivalente di vincoli binari.

**Alldiff** $alldiff(X_1,\dots, X_i)$: impone che tutte le variabili coinvolte assumano valori distinti. per questo vincolo vale che se $m$ variabili sono coinvolte e i loro domini contengono in totale $n$ valori distinti **allora**  **se** $m > n$, il vincolo non può essere soddisfatto $\Rightarrow$ **inconsistenza**.
da questo l algoritmo segue:
1. Eliminare le variabili con dominio singoletone e rimuovere il valore singoletto dai domini delle altre variabili.
2. Ripetere fino a esaurimento dei singoletoni.
3. Se ad un qualsiasi step un dominio si svuota o $m > n$ allora il vincolo non puo essere sodisfatto $\Rightarrow$ inconsistenza.



**Vincoli di risorse** o **Atmost** $Atmost(n, X_1, \dots, X_i)$: impone che la somma complessiva non superi $n$ unità.
Controllo di consistenza: Se la somma dei minimi dei domini $> n$ $\Rightarrow$ inconsistenza. se non è questo i caso si possono rendere i domini consistenti eliminano dai domini i valori massimi incompatibili con il vincolo, ovveroquelli  $>n$

Nei problemi di grandi dimensioni (es. logistici) si usano rappresentazioni con estremi, in questo caso si fa:
Si applica la __bounds propagation__:
- I domini sono intervalli $[min, max]$.
- Si aggiornano i limiti inferiori e superiori in base ai vincoli.
Un CSP è __bounds-consistent__ se per ogni variabile $X$, esistono valori minimi e massimi nel dominio tali che: È possibile estendere l’assegnazione in modo consistente rispetto ai vincoli tra $X$ e ogni altra variabile $Y$.




