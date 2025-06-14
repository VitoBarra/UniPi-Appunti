---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - IIA
  - AIF
topic: nota
Area: 
SubTopic:
---

# Agenti Razionali
---
un __agente__ è una qualsiasi entità **situata** in un [[Definizione di Problemi-Ambienti|ambiente]] dal quale è in grado di percepirne lo stato è il cambiamento tramite **sensori** quando disponibili e agisce su esso con degli **attuatori** (o **affectors**)
![[IMG - AIF agente.jpeg]]
 Ogni **agente** è caratterizzato dalla sua __sequenza percettiva__ (__percept sequence__), ovvero l’intera ***storia*** delle percezioni prese del [[Definizione di Problemi-Ambienti|ambiente]]. A partire da questa sequenza, l’agente decide l’azione da compiere. Si definisce la __funzione agente__ come una mappatura tra sequenze percettive e azioni:$$
\text{sequenza percettiva} \xrightarrow{f} \text{azione}
$$Tale funzione rappresenta in modo esaustivo il comportamento dell’agente, poiché specifica quale azione intraprendere in risposta a qualsiasi possibile storia percettiva. 

![[IMG - interazione agenti ambienti.png]]
l **implementazione concreta** è detto ___programma agente___, ed opera su un ambiente concreto che puo essere anche fisico e reale. $$Ag: P \rightarrow Az$$dove $P$ sono le percezioni e $Az$ sono le azioni. il Programma del agente implementa la funzione $Ag$


## Agenti Razionali 
Un __agente razionale__ è un __agente__ che compie le azioni “giuste” in base a criteri oggettivi di valutazione. L’efficacia dell’agente si misura attraverso una funzione di prestazione che valuta l’intera sequenza di stati generata dalle sue azioni all’interno dell’[[Definizione di problemi-Ambienti|ambiente]]. 

La razionalità di un agente dipende da quattro fattori principali:
- la **misura di prestazioni**, che rappresenta il criterio di successo;
- la **conoscenza pregressa** dell’ambiente di cui dispone l’agente;
- la **sequenza percettiva**, ovvero l’insieme delle percezioni ricevute dall’agente fino a quel momento;
- le **azioni possibili** che l’agente è in grado di compiere.

A partire da questi elementi, si definisce un **agente razionale** come segue: 
Per ogni possibile sequenza percettiva, un agente razionale deve selezionare l’azione che **massimizza** il [[Variabili aleatoria - Momenti|valore atteso]] della misura di prestazione, dato l’evidenza fornita dalla sequenza percettiva e qualsiasi conoscenza incorporata nell'agente.

Formalmente, 
__Sia__: 
- $U(s)$ è la misura di utilità associata
- $s$ è uno stato
- $\langle p_1, \dots, p_t \rangle$ è la __sequenza di percezioni__ osservata fino al tempo $t$  
- $K$ rappresenta __la conoscenza pregressa__ dell’agente 
l’__agente razionale__ cerca di massimizzare:$$
\mathbb{E}\left[ U(s) \mid \langle p_1, p_2, \dots, p_t \rangle, K \right]
$$
La razionalità non implica __onniscienza__ né __onnipotenza__. 
Le azioni dell’agente sono limitate alle sue capacità e a ciò che è in grado di percepire. Per questo motivo, la razionalità deve essere interpretata come la capacità di prendere decisioni ottimali **con le informazioni disponibili**. Un agente razionale potrebbe scegliere di compiere **azioni esplorative** con lo scopo di incrementare le proprie conoscenze e, dunque, migliorare le decisioni future. Un ulteriore requisito per la razionalità è l’**adattabilità**: l’agente deve essere in grado di modificare il proprio comportamento sulla base dell’esperienza accumulata, cioè delle percezioni passate. Questa caratteristica è strettamente collegata al concetto di **autonomia**.

Un **agente autonomo** è tale nella misura in cui il suo comportamento deriva dall’esperienza acquisita, piuttosto che da conoscenze incorporate a priori dal progettista. Un agente che si basa esclusivamente su conoscenze built-in risulterebbe rigido e scarsamente flessibile. L’autonomia, quindi, è indice della capacità dell’agente di apprendere dall’interazione con l’ambiente e di adattarsi a contesti nuovi o variabili, sviluppando strategie comportamentali non previste esplicitamente in fase di progettazione.

