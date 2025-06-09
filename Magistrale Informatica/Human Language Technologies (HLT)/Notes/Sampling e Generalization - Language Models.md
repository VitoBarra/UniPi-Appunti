
Un modo importante per visualizzare il tipo di conoscenza che un [[Probabilistic Language models]] incorpora è effettuare sampling (campionare) da esso. Campionare da una distribuzione significa selezionare dei punti in modo casuale, ma tenendo conto della loro probabilità. 
Campionare da un modello linguistico, quindi, vuol dire generare frasi scegliendo ogni parola o frase in base alla probabilità che il modello le attribuisce. 
In pratica, le frasi che il modello considera più probabili verranno generate più spesso, mentre quelle meno probabili saranno generate più raramente.

Nel 1948, Claude Shannon illustrava questo concetto con un esperimento curioso: proponeva di aprire un libro a caso, scegliere una lettera qualsiasi su una pagina, registrarla, poi aprire un'altra pagina e leggere fino a trovare quella stessa lettera, quindi annotare la lettera successiva. Ripetendo questo processo, si otteneva una sequenza di lettere che simulava un campionamento linguistico. Oggi, lo stesso principio viene applicato dai computer, ma in modo molto più efficiente.

Immaginando di rappresentare tutte le parole di un corpus su un asse orizzontale, in base alla loro probabilità cumulativa, le parole più comuni come "il", "di" o "un" avranno probabilità elevate e occuperanno segmenti più ampi, mentre parole più rare come "tuttavia" o "polifonico" avranno probabilità molto più basse e segmenti più piccoli.

Per campionare una parola, si genera un numero casuale tra 0 e 1, che viene poi mappato sull’asse delle probabilità cumulative. Se, ad esempio, il numero è 0,07, ricade nel segmento della parola "di", che viene quindi selezionata. Un numero come 0,66 potrebbe corrispondere a una parola meno comune come "tuttavia", mentre un valore molto alto come 0,99 potrebbe portare alla scelta di una parola rara come "polifonico".

Nell'illustrazione, le barre colorate rappresentano le parole comuni e ad alta probabilità, mentre linee tratteggiate e marcatori indicano le parole rare. Un dado nero a 100 facce simboleggia l’elemento casuale insito nel processo di campionamento.
![[sampling _ LM.png]]

Questo metodo garantisce che le parole con probabilità più alta vengano campionate più frequentemente, pur consentendo occasionalmente la selezione di parole meno comuni.

Per visualizzare i **bigrammi** secondo l'approccio di **Shannon**, si procede così: si sceglie un bigramma iniziale del tipo $(<s>, w)$ in base alla probabilità condizionata $p(w | <s>)$, poi si seleziona un nuovo bigramma $(w, x)$ secondo $p(x | w)$, e si continua in questo modo finché non si arriva al simbolo di fine frase $<\s>$. 
Alla fine, si concatenano le parole ottenute per formare una frase.


Naturalmente, nei **modelli linguistici neurali** esistono altri metodi di campionamento, pensati per evitare la generazione di parole molto improbabili (cioè nella "coda" della distribuzione). Tra questi:

- **Temperature sampling**: inizialmente si imposta una temperatura alta, che corrisponde a un campionamento quasi casuale; man mano che il testo viene generato, la temperatura si abbassa per mantenere la coerenza.
- **Top-k sampling**: si sceglie casualmente tra i k termini più probabili.
- **Top-p sampling (nucleus sampling)**: si seleziona casualmente tra il gruppo più piccolo di parole la cui somma di probabilità è almeno pari a p (ad esempio, 90%).

Tuttavia, i modelli basati su **n-grammi** funzionano bene nella predizione solo se il **corpus di test è molto simile a quello di addestramento**. Ma, anche con un buon corpus di training, il test set riesce spesso a sorprenderci. Per questo servono **modelli robusti**, capaci di **generalizzare**.

Un problema cruciale è rappresentato dalle **sequenze mai viste** (o "zeri"), per due motivi:

1. La loro presenza comporta una sottostima della probabilità di sequenze di parole plausibili, riducendo così le prestazioni del modello.
2. Se anche una sola parola del test set ha probabilità zero, l’intera sequenza avrà probabilità zero. Questo rende impossibile il calcolo della **perplessità**, che è definita come l’inverso della probabilità del test set: non possiamo dividere per zero.


Per risolvere il problema degli **n-grammi con probabilità zero**, si usano tecniche chiamate **smoothing** o **discounting**. Questi metodi "tolgono" una piccola parte di probabilità dagli eventi più comuni per redistribuirla su quelli mai osservati. Alcuni algoritmi di smoothing semplici includono:

- **Smoothing di Laplace** (add-one),
- **Stupid backoff**
- **Interpolazione n-gramma**.
- ![[Sampling LM 2.png]]

## Laplace smoothing

Il modo più semplice per applicare lo **smoothing** è il metodo **add-one**: consiste nell’aggiungere 1 a tutti i conteggi degli n-grammi prima di normalizzarli in probabilità. In questo modo, ogni n-gramma che aveva un conteggio pari a zero avrà ora un conteggio di 1, quelli che avevano 1 diventano 2, e così via. È come se fingessimo di aver visto ogni parola una volta in più rispetto alla realtà.

Una versione più generale è lo **smoothing add-k**, dove si aggiunge un valore kkk qualsiasi (non necessariamente 1) a ogni conteggio.

La formula della **probabilità smussata con Laplace** (add-one) è:.

$$P_{\text{Laplace}}(w_n\mid w_{n-1})=\frac{C(w_{n-1}w_n)+1}{\sum_w(C(w_{n-1}w)+1)}=\frac{C(w_{n-1}w_n)+1}{C(w_{n-1})+V}$$



dove:

- $C(w_{n-1}w_n)$ è il conteggio del bigramma,
- $C(w_{n-1})$ è il conteggio del primo termine del bigramma,
- $V$ è la dimensione del vocabolario.

Una tecnica utile per visualizzare l’effetto dello smoothing è costruire una **matrice dei conteggi aggiustati** $C^*$: questi conteggi sono quelli che, se divisi per $C(w_{n-1})$, restituirebbero la probabilità smussata. 
In questo modo, è più facile confrontare i conteggi smussati con quelli originali (massima verosimiglianza - MLE).

Tuttavia, l’add-one è uno strumento troppo grossolano: quando ci sono molti zeri (che è tipico degli n-grammi, data la loro sparsità), si finisce per spostare troppa probabilità verso eventi non osservati. Per questo motivo, **non si usa normalmente per gli n-grammi**, ma può funzionare bene in altri contesti NLP (come la classificazione di testo), dove lo spazio degli zeri non è così ampio.

### Altre strategie più efficaci:

- **Backoff**: si usa un trigramma solo se si hanno dati sufficienti. Altrimenti si “ripiega” su bigrammi o perfino unigrammi

- **Interpolazione**: si combinano le probabilità di unigrammi, bigrammi e trigrammi, con dei pesi $\lambda$ che devono sommare a 1. È un metodo che solitamente dà risultati migliori rispetto al backoff.

### Vocabolario chiuso vs aperto

Se conosciamo tutte le parole in anticipo, il vocabolario $V$ è **chiuso**: possiamo gestire direttamente ogni parola. 
Tuttavia, spesso ci troviamo in una situazione di **vocabolario aperto**, in cui compaiono parole **fuori vocabolario (OOV)**, non presenti durante l’addestramento.

Per gestire questo caso, usiamo un **token speciale UNK** (unknown word). Durante l’addestramento:

1. Si definisce un **lessico fisso** $L$ di dimensione $V$
    
2. Qualsiasi parola che non è in $L$ viene sostituita con il token `UNK`.
    
3. Si allenano le probabilità di `UNK` come se fosse una parola normale.

Durante la decodifica, ogni parola non vista nel training viene gestita usando la probabilità di `UNK`.