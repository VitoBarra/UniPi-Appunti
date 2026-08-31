---
Course: "[[Human Language Technology (HLT)]]"
Course 2: 
tags:
  - HLT
Area: "[[Emotion Recognition in Conversation (ERC)]]"
topic: 
SubTopic:
---
# Lexicons for Sentiment, Affect, and Connotation
_Tratto da: Speech and Language Processing – Jurafsky & Martin (2025)_

---

## 🧠 Concetti Chiave di Significato Affettivo

- **Affective meaning**: emozione, sentimento, personalità, umore, atteggiamenti.
- Tipologia di **Scherer (2000)**:
  - **Emozione**: episodi brevi e intensi (es. rabbia, gioia)
  - **Umore**: stato affettivo duraturo e diffuso (es. depresso, irritabile)
  - **Stile interpersonale**: approccio emotivo verso gli altri
  - **Atteggiamento**: opinioni affettive su oggetti/persone
  - **Tratti di personalità**: tendenze stabili (es. ansioso, geloso)

---

## 🧾 Lessici Affettivi (Sentiment Lexicons)

Strumenti che associano parole a dimensioni affettive (valenza, arousal, dominanza).

### 🔹 Lessici Binari (Positivo/Negativo)
- **General Inquirer (1966)**: 1915 parole positive, 2291 negative
- **MPQA Subjectivity Lexicon**: include soggettività debole/forte
- **Hu & Liu (2004)**: da recensioni di prodotto, via WordNet

### 🔹 Lexicon Valence-Arousal-Dominance
- **NRC VAD (Mohammad, 2018a)**: 20.000 parole con punteggi di valenza, attivazione, dominanza
- **NRC EmoLex**: 8 emozioni base di Plutchik (es. gioia, paura, rabbia)

### 🔹 Altri Lessici
- **LIWC**: 73 categorie psicologiche e linguistiche (es. rabbia, famiglia)
- **Lexicon Concreteness**: da Brysbaert et al. (2014), per parole astratte vs concrete

---

## 🧑‍🏫 Creazione di Lessici: Human Labeling

### EmoLex
- Annotazione in due fasi:
  1. Domanda su sinonimi per disambiguazione del senso
  2. Associazione della parola con emozioni (scala: nulla → forte)

### NRC VAD
- Metodo **Best-Worst Scaling**: scelta della parola più e meno associata a una dimensione.

---

## ⚙️ Semi-Supervised Lexicon Induction

### 🔹 Semantic Axis (An et al., 2018)
1. Si definiscono parole seme positive e negative
2. Si costruisce un asse semantico con word embeddings
3. Si misura la somiglianza di ogni parola all’asse via **coseno**

### 🔹 Sentiment Propagation (SentProp)
1. Si crea un grafo dei vicini più simili (embedding cosine)
2. Si propagano polarità da seed words tramite random walks
3. Si calcola uno score di polarità e una stima di confidenza (bootstrap)

### Altri metodi:
- **Congiunzioni sintattiche**: “fair and legitimate” vs “fair but brutal”
- **Negazioni morfologiche**: happy/unhappy
- **WordNet**: sinonimi e contrari (SentiWordNet → polarità a livello di synset)

---

## 📈 Supervised Learning

Utilizza recensioni con punteggio numerico (es. 1–5 stelle):
- Si stima la distribuzione di una parola su tutte le classi di rating
- **Potts Score**: rappresenta la parola come una distribuzione su classi
- Visualizzazioni: J-shape (fortemente positivi), reverse J (negativi), hump (moderati)

### 🔸 Log Odds Ratio con Dirichlet Prior (Monroe et al., 2008)
- Identifica parole più usate in una classe rispetto ad un’altra
- Usa corpus di background per stabilire un prior realistico
- Calcola **[[Z-score|z-score]]** per stabilire significatività

---

## 🤖 Uso dei Lessici per Sentiment Recognition

### 🔹 Metodo Rule-Based (no supervision)
```python
f+ = somma dei pesi delle parole positive nel testo
f- = somma dei pesi delle parole negative

Se f+/f- > λ → positivo
Se f-/f+ > λ → negativo
Altrimenti → neutro```

### 🔹 Metodo Supervisionato

- I lessici diventano feature per classificatori (SVM, logistic, etc.)
- Possono essere combinati con n-gram, frequenze, PMI, etc.
 

## 👥 Affect Centrico sull’Entità (Entity-Centric Affect)

Metodo di **Field & Tsvetkov (2019)**:

- Usa embeddings contestuali (es. BERT)
- Addestra regressori per ottenere:
    - **Sentiment** (Valence)
    - **Agency** (Arousal)
    - **Power** (Dominance)
- Associa punteggi alle **menzioni di entità** (es. personaggi di un film)

## 🧩 Connotation Frames

- I verbi esprimono connotazioni sugli argomenti (es. “X survived Y”)
- Annotano:
    - **Simpatia del writer**
    - **Valore, effetto, stato mentale degli attori**
    - **Differenze di potere e agency**
- Creati manualmente o via apprendimento supervisionato (Rashkin et al.)
