---
Course: "[[Human Language Technology (HLT)]]"
Course 2: 
tags:
  - HLT
Area: 
topic: 
SubTopic:
---
# Tokenizzazione - NLP
---
La **tokenizzazione** è il processo di suddivisione del testo in unità minime chiamate **token**, che in genere corrispondono a parole, ma possono includere anche numeri, punteggiatura, o espressioni multi parola. È un passaggio fondamentale in molti compiti di [[Natural Language Processing|NLP]], come la traduzione automatica, il riconoscimento vocale, l'analisi del sentiment e il recupero di informazioni.

Un buon sistema di tokenizzazione tiene conto di clitici, punteggiatura, espressioni fisse, entità nominate e può anche integrare fasi di normalizzazione per migliorare i risultati delle fasi successive dell’analisi del testo.

## Tokenizzazione basata su spazi
In molte lingue scritte con alfabeti che separano le parole con spazi (come il latino, il greco, il cirillico, o l'arabo), la forma più semplice di tokenizzazione consiste nel **separare il testo ogni volta che si incontra uno spazio**.

Nei sistemi Unix, strumenti di base come:

- `tr` (per trasformare o eliminare caratteri),
- `sort` (per ordinare le parole alfabeticamente),
- `uniq` (per raggruppare e contare le occorrenze di parole ripetute),

possono essere utilizzati per dividere un testo in token e calcolare la frequenza delle parole. 

### Sfide nella tokenizzazione
Tuttavia, questo approccio presenta alcune **limitazioni**.
- **Punteggiatura**: Non si può semplicemente rimuoverla, perché a volte è parte integrante della parola.
	- _Ph.D._, _$45.55_, _01/02/06_, _[www.example.com](http://www.example.com)_, _#hashtag_, _nome@email.it_
- **Clitici**: un **clitico** è una parte di parola che **non può stare da sola** e appare solo se collegata ad altre parole, come _'re_ in _we’re_.  I tokenizer più avanzati possono **espandere le contrazioni clitiche** trasformando _what’re_ in _what are_.
- **Espressioni multi parola (MWE)**: Frasi come _New York_ o _rock ‘n’ roll_ a volte devono essere trattate come un **unico token**. Per farlo, il sistema deve usare un dizionario di espressioni multi parola.


Inoltre per la tokenizzazione è utile tenere conto di altri 2 aspetti:
- **[[Normalizzazione - NLP|Normalizzazione]]**: In alcuni casi, è utile **uniformare le varianti di una parola**, ad esempio trattare _USA_ e _US_ come lo stesso token. Anche se si perde parte dell'informazione originale (come le maiuscole o le abbreviazioni), si guadagna in coerenza e compattezza del lessico.

- **Case folding (conversione in minuscolo)**: tutto il testo viene convertito in minuscolo. È utile in compiti come il **riconoscimento vocale** ed il **recupero di informazioni ([[Search engine]])**


Tuttavia, in altri contesti (es. analisi del sentiment, traduzione automatica, estrazione di entità), le **maiuscole contengono informazioni importanti** (es. nomi propri), quindi **non si applica il case folding**.

## Tokenizzazione in NLTK

**NLTK** (Natural Language Toolkit) è una libreria open source per il linguaggio Python, ampiamente utilizzata per l'elaborazione del linguaggio naturale. 
È uno strumento che offre un'ampia gamma di funzionalità, tra cui tokenizzazione, analisi grammaticale, tagging morfosintattico, parsing, stemming, lemmatizzazione e riconoscimento di entità nominate. 
NLTK include anche diversi corpus linguistici e risorse lessicali come WordNet. 
![[Tonenizzation NLTK.png]]


# Tokenizzazione nelle lingue senza spazi tra le parole
In molte lingue, come il **cinese**, il **giapponese** o il **thai**, **non si usano spazi** per separare le parole. Questo rende la tokenizzazione un compito molto più complesso rispetto a lingue come l'italiano o l'inglese, dove la presenza di spazi fornisce un'indicazione chiara dei confini tra le parole.

Stabilire cosa costituisca una “parola” in questi sistemi di scrittura è una **decisione non banale** e spesso **non esiste un consenso unico**.

### Algoritmo del Maximum Matching (MaxMatch)

Un metodo per segmentare testi in lingue come il cinese è l’algoritmo chiamato **Maximum Matching**, o **MaxMatch**. È spesso usato come **baseline** per confrontare metodi più avanzati.

Questo algoritmo:

- Richiede un **dizionario di parole** della lingua in esame.
- Parte dall’inizio della stringa e cerca **la parola più lunga possibile** nel dizionario che combacia con quella posizione del testo.
- Una volta trovata, **sposta il cursore** alla fine di quella parola e ripete il processo.
- Se **non trova alcuna parola corrispondente**, avanza semplicemente di **un carattere alla volta** e riprova.

È una forma di **ricerca greedy**, in cui si cerca di fare la scelta ottimale a ogni passo senza considerare tutte le possibilità future.


## Algorithms

Oltre alla tokenizzazione basata su spazi o caratteri singoli, oggi si adottano metodi più sofisticati basati sui **dati stessi**, come la **Tokenizzazione sub-lessicale (subword)**.  
In questo approccio, i token non sono necessariamente parole complete, ma anche **parti di parole**. Questo è particolarmente utile per gestire morfologie complesse, parole composte o neologismi.
Viene sempre più usato nei modelli moderni di NLP, come BERT o GPT, che lavorano spesso a livello di subword.

Tre principali di questi algoritmi sono:
Nei moderni sistemi di elaborazione del linguaggio naturale, sono comunemente utilizzati tre algoritmi per la **tokenizzazione a livello di subword**:

- **Byte-Pair Encoding (BPE)**
- **Unigram Language Model**
- **WordPiece**

Tutti e tre seguono una **struttura simile**, composta da due fasi principali:

1. **Token Learner**: analizza un corpus di addestramento grezzo e costruisce un vocabolario, cioè un insieme di token che rappresentano unità frequenti (caratteri, sillabe, radici, ecc.).
2. **Token Segmenter**: utilizza questo vocabolario per suddividere nuove frasi (test sentences) in token coerenti con quanto appreso nella fase precedente.

## Byte-Pair Encoding (BPE)
Il **BPE** nasce come tecnica di **compressione del testo**, ma è stato adattato per la tokenizzazione. È semplice ma molto efficace.

#### **Funzionamento dell’algoritmo:**

Si parte con un vocabolario che contiene **tutti i singoli caratteri** del corpus (ad esempio: A, B, C, …, a, b, c, …) e ogni parola viene rappresentata come **sequenza di caratteri**, seguita da un **simbolo speciale di fine parola** (ad esempio: `·`).

L’algoritmo procede per iterazioni. Ad ogni passo:
1. Si identificano **le due unità adiacenti più frequenti** nel corpus (es. “A” e “B”)
2. Si crea un **nuovo simbolo combinato** (“AB”) e lo si aggiunge al vocabolario
3. Si sostituiscono tutte le occorrenze della coppia “A B” con il nuovo simbolo “AB” in tutto il corpus

Questo processo viene **ripetuto per un numero prefissato di iterazioni (k merge)**.
  

Alla fine, il vocabolario sarà composto:

- Dalla **lista originale dei caratteri**, e
- Da **k nuovi simboli** ottenuti tramite fusione

![[Byte-Pair Encoding.png]]

Esempio algoritmo: 

![[BPE es1.png]]
![[BPE es 2.png]]
![[BPE es 3.png]]

### **Applicazione del BPE sui dati di test**

Dopo che il vocabolario dei token è stato appreso dal **corpus di addestramento**, si può applicare il BPE ai dati di **test** seguendo questi passaggi:

1. **Divisione per spazi**: ogni frase viene suddivisa in parole usando gli spazi.
2. **Aggiunta del simbolo di fine parola** (`_`) a ogni parola.
3. **Suddivisione in caratteri**: ogni parola viene trattata come una sequenza di caratteri singoli.

A questo punto si eseguono, in ordine, **tutte le fusioni (merge)** apprese durante la fase di training, **in modo greedy**, cioè sempre prendendo la prima fusione disponibile.

> ⚠️ Importante: le **frequenze nel testo di test non influenzano** le scelte. Si seguono solo le regole imparate nella fase di addestramento.

---

### **Esempi pratici**

Supponiamo che durante l’addestramento siano stati appresi i seguenti merge, in quest’ordine:

- `e` + `r` → `er`
- `er` + `_` → `er_`

Se applichiamo questi merge al testo di test, otteniamo:

- Frase di test: `n e w e r _`  
    Risultato: **newer_** → un unico token (parola frequente)
- Frase di test: `l o w e r _`  
    Risultato: **low** + **er_** → due token (la prima parte non è stata fusa nel training)

---

### **Proprietà dei token BPE**

I token ottenuti con Byte-Pair Encoding tendono a essere:

- **Parole intere molto frequenti**, se presenti spesso nel corpus di training.
- **Morfemi frequenti**, ovvero le **unità minime di significato** in una lingua.  Ad esempio:
    - `-est` (superlativo)
    - `-er` (comparativo o agente)

Un esempio è la parola _unlikeliest_, che può essere tokenizzata in tre **morfemi**:

- `un-` (prefisso negativo)
- `likely` (radice)
- `-est` (superlativo)

Questo mostra come BPE riesca a **catturare la struttura morfologica** delle parole, migliorando la capacità dei modelli NLP di comprendere significato e variazioni linguistiche.