---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
  - paper
  - temporary
Area: Modelli Generativi
topic: Discrete Flow Matching
SubTopic: Graph Generation
---

# DeFoG - appunti
---

Nota temporanea per accumulare osservazioni sul paper **DeFoG - Discrete Flow Matching for Graph Generation**. L'idea e farla crescere progressivamente fino a trasformarla in un riassunto strutturato del paper.

## Mappa mentale del paper

Per leggere DeFoG in modo ordinato conviene tenere separati quattro livelli:

1. **oggetto modellato**: grafi discreti con tipi di nodo ed edge
2. **dinamica ideale**: una [[Continue Time Markov Chain (CTMC)|CTMC]] con rate matrix $R_t$
3. **training**: imparare bene le distribuzioni pulite condizionate $p_{1|t}$
4. **sampling**: approssimare numericamente la dinamica continua con una griglia temporale scelta dal sampler

Quasi tutte le difficolta del paper nascono dal passaggio tra questi quattro livelli.

## Idea generale

Il paper propone un metodo di **[[Discrete Flow Matching | discrete flow matching]]** per la generazione di grafi. Rispetto al [[Flow Matching | flow matching]] standard, che lavora in spazi continui e apprende un [[Campo vettoriale|campo vettoriale]] $v_t(x)$, qui lo stato del sistema e **discreto**:

- tipi di nodo
- tipi di edge
- struttura del grafo

Quindi la dinamica non puo essere descritta da una [[Ordinary Differential Equation (ODE)|ODE]] sullo stato, ma da una [[Continue Time Markov Chain (CTMC)|CTMC]] con matrice dei tassi.

## Differenza con il flow matching continuo

Nel [[Flow Matching | flow matching]] continuo:

$$
\frac{dx}{dt} = v_t(x)
$$

e il sampling consiste nel risolvere una ODE.

Nel discrete flow matching:

- lo stato appartiene a uno spazio discreto;
- il modello apprende tassi di transizione;
- la distribuzione evolve secondo una equazione di Kolmogorov del tipo

$$
\frac{d}{dt}p_t = R_t^\top p_t
$$

Quindi il sampling non integra una traiettoria continua nello spazio euclideo, ma approssima una dinamica markoviana a tempo continuo.

Un punto importante e che questa equazione non descrive il moto di un singolo grafo campionato, ma l'evoluzione della **[[Distribuzione di probabilita | distribuzione di probabilita]]** sui grafi. La **Kolmogorov equation** dice cioe come la massa di probabilita si sposta nel tempo quando i salti tra stati discreti sono governati dalla rate matrix $R_t$.

Per questo in DeFoG la Kolmogorov equation ha un ruolo strutturale:

- la dinamica continua ideale del modello e definita da $R_t$
- l'evoluzione della distribuzione associata e determinata da $\partial_t p_t = R_t^\top p_t$
- il sampler approssima numericamente questa dinamica continua con passi discreti nel tempo

In altre parole, la Kolmogorov equation e la **legge dinamica di riferimento** che collega l'oggetto appreso dal modello, cioe i tassi di transizione, al comportamento globale della distribuzione generata.

## Loss di training

La loss usata da DeFoG e una **[[Cross Entropy Loss | cross-entropy]]** di denoising. Il modello osserva un grafo rumoroso $G_t$ e deve predire, per ogni nodo e per ogni edge, la distribuzione del corrispondente stato pulito nel grafo finale $G_1$.

La forma generale della loss e

$$
\mathcal{L}_{\mathrm{DeFoG}}
=
\mathbb{E}_{t \sim T,\; G_1 \sim p_1,\; G_t \sim p_{t|1}(\cdot|G_1)}
\Big[
\mathrm{CE}_\lambda\bigl(G_1,\; p_\theta(\cdot|G_t,t)\bigr)
\Big]
$$

dove la cross-entropy interna si separa in un termine sui nodi e uno sugli edge:

$$
\mathrm{CE}_\lambda
=
- \sum_n \log p^{(n)}_{\theta,1|t}\bigl(x^{(n)}_1 \mid G_t\bigr)
- \lambda \sum_{i<j}\log p^{(ij)}_{\theta,1|t}\bigl(e^{(ij)}_1 \mid G_t\bigr).
$$

Qui:

- $x^{(n)}_1$ e il tipo pulito del nodo $n$
- $e^{(ij)}_1$ e il tipo pulito dell'edge $(i,j)$
- $\lambda$ pesa diversamente nodi ed edge
- $T$ e la distribuzione con cui si campiona il tempo di training

Quindi, in pratica, il training e un problema di **reconstruction / denoising supervisionato**: dato un campione pulito $G_1$, lo si corrompe ottenendo $G_t$, e il modello deve predire la distribuzione degli stati puliti originali.

## Perche questa loss ha senso

La cosa importante nel paper e che la loss non viene motivata solo come una euristica di denoising, ma viene collegata direttamente all'oggetto usato in sampling.

Il sampling in DeFoG non usa direttamente le probabilita predette dal modello come output finale, ma costruisce da esse una **rate matrix** per la [[Continue Time Markov Chain (CTMC)|CTMC]] di denoising. Quindi il punto teorico e:

- in training il modello predice $p_{\theta,1|t}$
- in sampling questa predizione viene trasformata in una matrice dei tassi $R^\theta_t$
- perche il sampler sia corretto, $R^\theta_t$ deve essere vicina alla rate matrix vera

Il paper mostra allora che l'errore sulla rate matrix puo essere maggiorato da termini che dipendono proprio dalla cross-entropy di training. In sostanza:

$$
\text{small CE loss}
\quad \Rightarrow \quad
\text{small error on } p_{\theta,1|t}
\quad \Rightarrow \quad
\text{small error on } R^\theta_t.
$$

L'idea tecnica passa attraverso questi passaggi:

1. la rate matrix vera dipende dalle marginali pulite condizionate $p_{1|t}$
2. il modello approssima queste marginali con $p_{\theta,1|t}$
3. l'errore tra rate matrix vera e approssimata si puo controllare tramite una distanza tra distribuzioni
4. quella distanza viene poi controllata tramite [[Kullback-Leibler (KL) Divergence | KL divergence]] / cross-entropy, usando disuguaglianze come Pinsker

Quindi la CE non e solo una loss "comoda": e una loss che controlla l'errore sull'oggetto che il sampler usa davvero.

Più precisamente, il motivo per cui questo e sufficiente e che la dinamica della distribuzione viene poi governata dalla Kolmogorov equation associata a quella rate matrix. Quindi, se la rate matrix appresa e buona, allora anche la legge evolutiva usata dal sampler e buona.

## Presupposto chiave

Il motivo per cui tutto questo funziona e che la formulazione del paper rende la rate matrix una funzione delle marginali pulite condizionate. Di conseguenza, se il modello impara bene

$$
p_{1|t}(\cdot|G_t),
$$

allora puo anche costruire bene la dinamica di denoising continua nel tempo.

Quindi il presupposto implicito e:

- non serve imparare direttamente la rate matrix
- basta imparare bene le distribuzioni pulite condizionate da cui la rate matrix viene derivata

Ed e proprio qui che la loss di [[Cross Entropy Loss | cross-entropy]] diventa naturale.

## Intuizione finale

La loss chiede al modello:

$$
\text{“dato } G_t,\ \text{qual e lo stato pulito piu probabile di ogni nodo ed edge?”}
$$

Se questa previsione e accurata, allora la rate matrix costruita a partire da tali probabilita guida correttamente il sampler verso la distribuzione dei grafi reali.

## Pipeline teorica del metodo

Il cuore del paper puo essere riassunto con questa catena:

$$
G_t
\quad\longrightarrow\quad
p_{\theta,1|t}(\cdot \mid G_t,t)
\quad\longrightarrow\quad
R_t^\theta
\quad\longrightarrow\quad
\partial_t p_t = (R_t^\theta)^\top p_t
\quad\longrightarrow\quad
\text{sampler discreto}.
$$

Lettura del diagramma:

- da un grafo rumoroso $G_t$ il modello predice le distribuzioni pulite condizionate
- da queste distribuzioni viene costruita la rate matrix appresa $R_t^\theta$
- quella rate matrix definisce la dinamica continua ideale tramite la Kolmogorov equation
- il sampler implementa una versione discreta di questa dinamica continua

Questo schema aiuta anche a capire dove agiscono i vari ingredienti del paper:

- la **loss** agisce sul blocco $G_t \to p_{\theta,1|t}$
- la **teoria** giustifica il passaggio $p_{\theta,1|t} \to R_t^\theta$
- la **Kolmogorov equation** governa il blocco $R_t^\theta \to p_t$
- il **sample distortion** modifica l'ultimo blocco, cioe come il sampler attraversa il tempo

## Independent Euler step

Quando il paper parla di **independent Euler step**, sta approssimando numericamente la dinamica continua sottostante con un passo di Eulero nel tempo.

L'idea non e:

$$
\frac{dx}{dt} = v_t(x)
$$

come nel caso continuo, ma piuttosto una dinamica sulle distribuzioni indotta dalla CTMC.

In pratica:

- si discretizza il tempo in passi $\Delta t$;
- si approssimano le transizioni infinitesime;
- l'aggiornamento viene applicato separatamente a nodi ed edge.

Quindi "independent" non vuol dire che nodi ed edge siano veramente indipendenti a livello semantico, ma che il passo numerico viene fattorizzato per componenti nel sampler.

## Sample Distortion

Il paper osserva che usare passi temporali uniformi nel sampling puo essere subottimale. In particolare, nelle fasi finali della generazione possono servire passi piu piccoli per evitare modifiche brusche che rompano proprieta globali del grafo, come per esempio la planarita.

Per questo introduce una **distorsione temporale**: invece di usare direttamente un tempo uniforme $t \in [0,1]$, si applica una funzione crescente e biiettiva

$$
t' = f(t).
$$

Un esempio e

$$
f(t)=2t-t^2
$$

chiamata `polydec`, che produce passi via via piu piccoli verso la fine del sampling.

Idea chiave:

- piu risoluzione temporale dove il campione e piu fragile;
- meno risoluzione dove non serve.

## Train Distortion

Qui il punto importante e che il paper sfrutta un **decoupling tra training e sampling**.

Prima di tutto, la **sample distortion** puo essere cambiata **senza retraining**. Quindi:

- il modello puo essere addestrato con una certa distribuzione dei tempi;
- in sampling si puo poi usare una distorsione temporale diversa;
- questo mostra che training e sampling **non sono rigidamente coupled**.

Questo e un aspetto importante rispetto al flow matching "standard", dove di solito probability path, parametrizzazione temporale e dinamica usata in sampling tendono a coincidere piu strettamente.

Nel paper, invece, si usa esplicitamente il fatto che il sampler puo essere modificato a posteriori per adattarsi meglio alle caratteristiche del dataset. In altre parole:

$$
\text{train once} \quad \Rightarrow \quad \text{change sampling schedule without retraining}
$$

Solo **dopo** aver trovato una distortion efficace per il sampling, gli autori propongono anche di usarla nel training.

Questo significa che il tempo di training non viene piu campionato uniformemente, ma puo essere deformato con la stessa funzione:

$$
t \sim \mathrm{Uniform}(0,1),
\qquad
t' = f(t).
$$

Quindi il quadro corretto e:

- **prima**: training e sampling sono disaccoppiabili;
- **poi**: si puo scegliere di riallinearli se questo migliora performance e convergenza.

Questa seconda parte non nega il decoupling, ma mostra che il decoupling e utile anche come strumento di analisi:

- si sperimentano diverse distortion in sampling senza riaddestrare;
- si individua quali intervalli temporali sono piu critici;
- solo a quel punto si puo trasferire questa informazione nel training.

Quindi il messaggio non e

$$
\text{training and sampling must match}
$$

ma piuttosto

$$
\text{sampling can be optimized independently, and training can optionally be adapted afterwards}.
$$

Il valore del paper sta proprio qui:

$$
\text{best sampling schedule} \Rightarrow \text{useful training bias},
$$

ma non il contrario come vincolo iniziale.

## Perche il decoupling e possibile

Il decoupling e possibile perche il modello non viene addestrato su una specifica griglia temporale di sampling, ma su una **dinamica continua nel tempo**.

L'oggetto appreso dal modello e qualcosa del tipo

$$
R_\theta(x,t)
$$

cioe una legge di transizione parametrizzata dallo stato discreto $x$ e dal [[Time Embedding | tempo continuo]] $t \in [0,1]$.

Il punto chiave e che il training non insegna al modello "cosa fare al passo numero 17", ma piuttosto:

$$
\text{dato lo stato } x \text{ al tempo } t,\ \text{questi sono i tassi corretti}.
$$

Quindi il modello impara una dinamica locale continua nel tempo, mentre la discretizzazione dei tempi usata per generare un campione viene scelta solo in fase di sampling.

In questo senso:

- il **training** impara la legge continua $R_\theta(x,t)$;
- il **sampling** decide con quali tempi discreti interrogare il modello.

Per questo si puo cambiare la griglia temporale del sampler senza riaddestrare:

$$
\text{same } R_\theta(x,t), \qquad \text{different time grid}.
$$

La distortion temporale non cambia cio che il modello ha imparato; cambia solo **quali tempi** vengono visitati e con quale densita durante l'approssimazione numerica del processo.

Un dettaglio importante e che questo non significa che il modello abbia "dati memorizzati" per ogni valore reale di $t$. Significa piuttosto che il modello e definito come funzione continua del tempo e quindi, in principio, puo essere interrogato per qualunque $t \in [0,1]$.

Pero, sia in training sia in sampling, le valutazioni effettive avvengono sempre in un insieme **discreto** di tempi:

- in training si campionano alcuni valori di $t$
- in sampling si sceglie una griglia $t_0,t_1,\dots,t_N$

Quindi la picture corretta e:

- **modello**: continuo in $t$
- **query effettive**: discrete in $t$
- **time distortion**: cambia quali punti discreti vengono interrogati

In altre parole:

$$
\text{continuous-time model}
\quad+\quad
\text{discrete-time numerical evaluation}.
$$

## Componenti architetturali

Qui entrano gli elementi che aiutano il modello a rappresentare bene la struttura del grafo.

### PE

`PE` sta per **Positional Encoding**. In generale e una informazione aggiuntiva data al modello per descrivere la posizione o la struttura degli elementi in input.

Nel caso dei grafi, una PE non rappresenta necessariamente una posizione geometrica, ma puo codificare:

- ruolo strutturale di un nodo
- distanza o relazione tra coppie di nodi
- informazione topologica utile al modello

Quindi, in ambito graph generation o [[Graph Transformer | graph transformer]], una PE serve a dare al modello informazione che non e immediatamente leggibile solo dai tipi di nodi ed edge.

### RRWP

`RRWP` sta per **Relative Random Walk Probabilities**. E una forma di positional encoding relativa per grafi.

L'idea e che, per una coppia di nodi $i,j$, si guardi la probabilita che un random walk partito da $i$ arrivi in $j$ dopo $k$ passi:

$$
\mathrm{RRWP}_{ij}^{(k)} = (P^k)_{ij}
$$

dove $P$ e la matrice di transizione del random walk sul grafo.

Usando piu valori di $k$, si ottiene una rappresentazione del tipo

$$
\bigl((P)_{ij}, (P^2)_{ij}, \dots, (P^K)_{ij}\bigr)
$$

che cattura struttura locale e semi-globale del grafo.

Interpretazione intuitiva:

- valore alto per piccoli $k$ = nodi fortemente connessi o vicini nella struttura
- valore basso = nodi lontani o poco raggiungibili

Quindi RRWP e una PE **relativa**, perche descrive la relazione strutturale tra due nodi, non solo una proprieta assoluta del nodo preso da solo.

## Lettura attuale del contributo

Per ora il contributo del paper sembra essere:

1. portare il [[Discrete Flow Matching | discrete flow matching]] alla generazione di grafi;
2. usare una dinamica discreta su nodi ed edge;
3. mostrare che il sampling puo essere migliorato con una distorsione temporale non uniforme anche senza retraining;
4. usare poi questa informazione per ridefinire il training e migliorare convergenza e performance.

## Punti da approfondire

- definizione precisa della rate matrix usata dal modello
- come vengono parametrizzati i tassi per nodi ed edge
- objective di training esatto
- differenza precisa tra predictor parametrico e target teorico
- dettagli del sampler in Alg. 2
- appendice sulle distortion functions
- risultati sperimentali principali e su quali dataset

## Paper utili

### Must read

- **DeFoG: Discrete Flow Matching for Graph Generation**. E il paper principale e va letto fino a capire bene tre cose: loss, costruzione della rate matrix e sampler. Link: https://proceedings.mlr.press/v267/qin25d.html
- **Discrete Flow Matching**. E il riferimento piu diretto per capire la versione generale del DFM fuori dai grafi. Serve per separare cio che e specifico di DeFoG da cio che appartiene al framework discreto in generale. Link: https://arxiv.org/abs/2407.15595
- **Flow Matching for Generative Modeling**. E il punto di partenza per capire da dove arriva l'idea originale di flow matching e in che senso il discreto ne modifica l'oggetto matematico. Link: https://openreview.net/forum?id=PqvMRDCJT9t

### Useful For Theory

- **Generator Matching: Generative modeling with arbitrary Markov processes**. Utile per inquadrare DeFoG dentro una visione ancora piu generale basata su generatori markoviani. Da leggere quando vuoi capire bene il ruolo della rate matrix come oggetto centrale. Link: https://openreview.net/forum?id=RuP17cJtZo
- **Variational Flow Matching for Graph Generation**. Utile per confrontare la prospettiva di DeFoG con una formulazione variazionale basata sulla posterior path. Serve soprattutto per capire meglio alternative alla loss e al target di training. Link: https://openreview.net/forum?id=UahrHR5HQh

### Useful For Comparison

- **DiGress: Discrete Denoising Diffusion for Graph Generation**. Utile per confrontare DeFoG con i graph diffusion discreti classici. Importante sul tema coupling training-sampling e sul framing del denoising come classificazione di nodi ed edge. Link: https://openreview.net/forum?id=UaAD-Nu86WX
- **Diffusion Models for Graphs Benefit From Discrete State Spaces**. Utile per capire perche i grafi si prestano naturalmente a noising discreto e quali vantaggi pratici porta restare nello spazio discreto. Link: https://openreview.net/forum?id=06erEMdoSml
- **Cometh: A continuous-time discrete-state graph diffusion model**. Utile per il confronto con altri modelli CTMC su grafi. Da leggere quando vuoi capire cosa distingue DeFoG da altri approcci continui nel tempo ma discreti nello stato. Link: https://openreview.net/forum?id=nuN1mRrrjX
- **Hierarchical Discrete Flow Matching for Graph Generation**. Utile come sviluppo successivo del filone. Non serve subito per capire DeFoG, ma e utile dopo per vedere come il discrete flow matching sui grafi evolve in direzione piu efficiente. Link: https://arxiv.org/abs/2604.00236

### Useful For Architecture

- **Graph Inductive Biases in Transformers without Message Passing**. E il riferimento utile per capire RRWP, pair representations e il ruolo delle positional / structural encodings nel graph transformer usato da DeFoG. Link: https://openreview.net/forum?id=HjMdlNgybR

### Ordine di lettura consigliato

1. DeFoG
2. Flow Matching for Generative Modeling
3. Discrete Flow Matching
4. DiGress
5. Generator Matching
6. Variational Flow Matching for Graph Generation
7. Graph Inductive Biases in Transformers without Message Passing
8. Cometh
9. Hierarchical Discrete Flow Matching for Graph Generation
