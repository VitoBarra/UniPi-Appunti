---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area: Modelli Generativi
topic: Continuous-time generative models
SubTopic:
---
# Discrete Flow Matching
---
Il **Discrete Flow Matching** e una variante del [[Flow Matching | flow matching]] pensata per spazi di stato **discreti**, dove i campioni non sono vettori continui in $\mathbb{R}^d$ ma sequenze di token, simboli categorici, oppure strutture discrete come grafi con etichette discrete su nodi ed edge. L'idea di base resta quella di definire un percorso probabilistico tra una distribuzione iniziale semplice e la distribuzione dei dati, ma la dinamica che realizza questo trasporto non puo piu essere descritta da un [[Campo vettoriale|campo vettoriale]] continuo.

Nel [[Flow Matching | flow matching]] standard il campione evolve secondo una [[Ordinary Differential Equation (ODE)|ODE]]

$$
\frac{dx}{dt}=v_t(x)
$$

dove $x$ varia in modo infinitesimo nel continuo. Nel caso discreto questo non ha piu senso, perche uno stato discreto non si muove con piccole variazioni differenziali: puo solo **saltare** da una configurazione a un'altra. Per questo la dinamica continua nel tempo viene modellata tramite una [[Continue Time Markov Chain (CTMC) | CTMC]], cioe un processo a tempo continuo con transizioni tra stati discreti governate da tassi istantanei.

L'oggetto centrale non e quindi un campo di velocita $v_t(x)$, ma una **rate matrix** o **generatore** $Q_t$, i cui coefficienti descrivono i tassi di transizione tra stati discreti. Se $p_t$ rappresenta la [[Distribuzione di probabilita | distribuzione del processo]] al tempo $t$, allora la sua evoluzione non segue una equazione di continuita nello spazio continuo, ma una equazione di tipo Kolmogorov:

$$
\frac{d}{dt}p_t = Q_t^\top p_t
$$

oppure in forma equivalente a seconda della convenzione usata per rappresentare i vettori di probabilita. Il significato operativo resta simile a quello del [[Flow Matching | flow matching]] continuo: non si apprende direttamente la distribuzione finale, ma la legge locale che trasporta la probabilita lungo il tempo.

Anche qui si costruisce una **probability path** che collega una distribuzione iniziale semplice a quella dei dati. La differenza e che, invece di interpolare punti nello spazio continuo, si definisce un processo di corruzione o mescolamento discreto che trasforma gradualmente il dato in una configurazione piu semplice. Il modello viene allora addestrato a predire la dinamica inversa o, piu precisamente, i tassi coerenti con il trasporto discreto lungo la path scelta.

Una maniera utile di leggere la differenza e la seguente:

- nel [[Flow Matching | flow matching]] continuo il modello apprende come un punto deve **muoversi** nello spazio;
- nel discrete flow matching il modello apprende con quali tassi uno stato deve **saltare** verso altri stati.

Quindi il passaggio concettuale fondamentale e

$$
\text{velocity field} \quad \longrightarrow \quad \text{rate matrix}
$$

Nel caso continuo il vincolo strutturale e dato dall'equazione di continuita; nel caso discreto il vincolo analogo e dato dalla dinamica markoviana a tempo continuo. In entrambi i casi si impone che l'evoluzione temporale della distribuzione sia coerente con la path probabilistica prescelta, ma cambia la natura dello spazio di stato e quindi cambia anche la forma matematica della dinamica.

Una conseguenza importante riguarda il sampling. Nel [[Flow Matching | flow matching]] classico, una volta appreso $v_{\theta}(x,t)$, si genera un campione risolvendo una [[Ordinary Differential Equation (ODE)|ODE]] dal rumore al dato. Nel discrete flow matching, invece, la generazione consiste nel simulare oppure approssimare una [[Continue Time Markov Chain (CTMC)|CTMC]] governata dai tassi predetti dal modello. In pratica:

- nel continuo si integra una ODE;
- nel discreto si simula una dinamica di salti.

Questo rende il discrete flow matching particolarmente naturale per domini come testo, sequenze simboliche e grafi discreti, dove lo stato non e un vettore reale ma una configurazione combinatoria. In lavori come **DeFoG**, per esempio, nodi ed edge vengono generati tramite transizioni discrete nel tempo invece che tramite traiettorie differenziabili nello spazio euclideo.

Il legame con [[Diffusion Models | diffusion models]] resta presente anche qui. Come nei modelli diffusivi discreti, si definisce una corruzione progressiva e si impara una dinamica di generazione inversa; tuttavia il discrete flow matching enfatizza la descrizione del trasporto tramite tassi di transizione in tempo continuo, piu che tramite un obiettivo di denoising o una [[Score Function|score]].

Rispetto a [[Flow Matching | flow matching]], quindi, non cambia l'idea generale di apprendere una dinamica che collega una distribuzione semplice ai dati, ma cambia completamente l'oggetto matematico che rappresenta quella dinamica:

- continuo: [[Campo vettoriale|campo vettoriale]] e [[Ordinary Differential Equation (ODE)|ODE]]
- discreto: matrice dei tassi e [[Continue Time Markov Chain (CTMC)|CTMC]]

Le proprieta operative piu importanti sono:
- apprende tassi di transizione discreti invece di un campo di velocita continuo
- usa una dinamica markoviana a tempo continuo invece di una ODE nello spazio euclideo
- e adatto a token, simboli e grafi discreti
- mantiene la separazione concettuale tra probability path e parametrizzazione della dinamica
