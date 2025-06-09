---
Course: "[[Human Language Technology (HLT)]]"
Course 2: 
tags:
  - HLT
Area: 
topic: 
SubTopic:
---
# Words and Corpora
---
Un **Corpus*** è una collezione organizzata di testi con determinate funzionalità linguistiche che rispettano i criteri di analisi linguistica. Ogni *corpus* viene creato seguendo criteri in base ai suoi futuri usi. 

I **Corpora** servono come fonti di dati linguistici, rappresentando il linguaggio inalterato. Possono essere derivanti da libri (romanzi, poesie e non romanzi), giornali, pagine web, emails, pubblicità, chats, tweets, o da trascrizioni di conversazioni parlate.

I principali criteri di selezione dei testi per un corpus sono:
-**I principali criteri di selezione dei testi per un corpus sono:**

- **Generalità:**
    - **Corpus specializzato (corpus di sotto-linguaggio):** descrive una varietà linguistica specifica (giornalistica, infantile, giuridica, medica, ecc.)
    - **Corpus generale o di riferimento:** è trasversale a diversi ambiti e rappresenta la maggior parte degli aspetti linguistici
        
- **Modalità:**
    - **Corpus scritto:** contiene testi in lingua scritta
    - **Corpus parlato:** comprende trascrizioni del linguaggio parlato
    - **Corpus misto:** include entrambi i tipi in proporzioni variabili
    - **Corpus audio:** contiene campioni di lingua parlata in forma di segnale acustico
        
- **Cronologia:**
    - **Corpus sincronico:** rappresenta una fase specifica (periodo di tempo) della lingua
        
- **Lingua:**
    - **Corpus monolingue:** tutti i testi appartengono a una sola lingua
    - **Corpus bi/multilingue:** contiene testi in due o più lingue
        
- **Integrità:**
    - Il corpus può contenere testi interi o porzioni di lunghezza variabile, definite in anticipo
        
- **Corpus annotato:**
    - Contiene informazioni codificate sulla struttura linguistica a vari livelli di rappresentazione (morfologico, sintattico, semantico, ecc.)


# Parole in una frase

Per definire il numero di parole in una frase, o *utterance*, bisogna analizzarla e capire cosa si intende con parola.

![[Words in utterance.png]]
Bisogna analizzare le disfluenze, come le parole frammentate (uh, main-). Queste parole vengono chiamate fillers o filled pauses. Dipendentemente dal contesto di applicazione possono essere considerate parole oppure ignorate. 

Quando si analizza un corpus linguistico, è importante distinguere tra due unità:
- **Token**: ogni singola occorrenza di una parola nel testo. È il numero totale di parole, comprese le ripetizioni.
- **Tipo (Type)**: ogni parola distinta presente nel corpus. Ogni parola viene contata una sola volta, indipendentemente da quante volte appare.
  
Per esempio, se in una frase compare due volte la stessa parola, questa sarà **due token ma un solo tipo**.

Inoltre, parole composte come _San Francisco_ possono essere considerate come **due token (San, Francisco)** o come **un solo token**, a seconda delle convenzioni adottate.

## Misurare la dimensione del vocabolario

Per misurare la dimensione del vocabolario si tiene conto di 3 elementi:
- **N**, il numero totale di **token** (cioè le parole effettivamente usate nel corpus).
    
- **V**, l'insieme dei **tipi**, ovvero il **vocabolario**.
    
- **|V|**, la **dimensione del vocabolario**

### Heaps’ Law (o Legge di Herdan)
Man mano che la dimensione del corpus aumenta (cioè aumentano i token), cresce anche il numero di tipi distinti ($|V|$), ma **non in modo lineare**. Questa relazione è descritta dalla **Legge di Heaps (o di Herdan)** :
$$|V|=kN^\beta$$
dove:

- **k** e **β** sono costanti positive,
- **β** è compreso tra 0 e 1 (tipicamente tra 0.67 e 0.75).

Questa legge riflette il fatto che, anche se leggiamo o ascoltiamo molti più testi, la quantità di parole nuove (tipi) cresce sempre più lentamente.


Another measure of the number of words in the language is the number of lemmas instead of wordform (full inflected or derived form of the word) types. Dictionaries can help in giving lemma counts; dictionary entries or boldface forms are a very rough upper bound on the number of lemmas. Type-Token Ratio (TTR) = |V| / N


### Lemmi e forme flesse
Un'altra possibile misura della quantità di parole è data dai **lemmi**, ovvero le forme base delle parole (es. _correre_ è il lemma di _corro, correvi, correrò_).

Contare i **lemmi** è un modo per **normalizzare** le forme flesse o derivate.

I dizionari tradizionali possono offrire una stima del numero di lemmi, ma solo come approssimazione.

### Indice di Ricchezza Lessicale: Type-Token Ratio (TTR)
Un indicatore importante è la **Type-Token Ratio (TTR)**, che misura la varietà lessicale di un testo:

$$TTR = \frac{|V|}{N}$$​

Più alto è questo rapporto, **più ricco è il vocabolario** del testo (o del parlante/scrittore), ma è anche influenzato dalla lunghezza del testo: testi brevi tendono ad avere un TTR più alto.