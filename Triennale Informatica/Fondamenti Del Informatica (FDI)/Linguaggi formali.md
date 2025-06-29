---
Course: "[[Fondamenti Del Informatica (FDI)]]"
tags:
  - FDI
  - Status/AiGenerated
Area: 
topic: 
SubTopic:
---

# Linguaggi formali
---
I linguaggi formali costituiscono un ambito fondamentale della teoria dell'informazione e della computazione. Si definiscono a partire da un insieme finito di simboli, detto [[Alfabeto]], indicato con la lettera $ \Sigma $. Da tale alfabeto si costruiscono tutte le possibili stringhe finite, le quali appartengono all'insieme $ \Sigma^* $. Ogni linguaggio formale è un sottoinsieme di $ \Sigma^* $, ovvero $ L \subseteq \Sigma^* $.

L'insieme $ \Sigma^* $ comprende tutte le concatenazioni finite di simboli appartenenti all'alfabeto, incluse le stringhe vuote, denotate con $ \varepsilon $. La struttura risultante è dotata dell'operazione di concatenazione, che permette di combinare due stringhe producendo una nuova stringa appartenente a $ \Sigma^* $.

All'interno dei linguaggi formali si distinguono due concetti strettamente connessi: la **sintassi** e la **semantica**. La sintassi descrive l'insieme delle regole formali che determinano le stringhe valide di un linguaggio, ossia la struttura corretta dei simboli. La semantica si riferisce all'interpretazione o al significato associato alle stringhe sintatticamente corrette, in funzione del contesto in cui il linguaggio viene applicato.

Un linguaggio può essere rappresentato formalmente attraverso grammatiche, espressioni regolari o modelli computazionali come gli [[Automa a stati finiti]], ciascuno dei quali consente di analizzare e generare le stringhe che appartengono al linguaggio stesso.

La classificazione dei linguaggi formali segue la gerarchia di Chomsky, che distingue le diverse tipologie in base alla loro potenza espressiva. I linguaggi regolari costituiscono la classe più semplice e sono riconoscibili tramite automi a stati finiti deterministici o non deterministici. I linguaggi liberi dal contesto, più complessi, sono generati da grammatiche context-free e riconoscibili tramite automi a pila. Classi superiori includono linguaggi sensibili al contesto e linguaggi ricorsivamente enumerabili, che richiedono strumenti più potenti come le macchine di Turing.

L'analisi dei linguaggi formali permette di definirne le proprietà di chiusura rispetto a operazioni quali l'unione, la concatenazione e la chiusura di Kleene, formalizzate come segue:

$$
L_1, L_2 \subseteq \Sigma^* \implies L_1 \cup L_2, \quad L_1 \cdot L_2, \quad L_1^* \subseteq \Sigma^*
$$

Dove:
- $ L_1 \cup L_2 $ rappresenta l'unione dei linguaggi
- $ L_1 \cdot L_2 $ indica la concatenazione tra stringhe di $ L_1 $ e $ L_2 $
- $ L_1^* $ è la chiusura di Kleene, cioè l'insieme di tutte le stringhe ottenute concatenando un numero arbitrario, anche nullo, di stringhe appartenenti a $ L_1 $

L'approccio rigoroso dei linguaggi formali consente di modellare il comportamento di sistemi computazionali, applicando strutture e regole precise che permettono di analizzare e controllare linguaggi artificiali, processi di comunicazione, linguaggi di programmazione e sistemi complessi, mantenendo una netta distinzione tra la componente sintattica e quella semantica.
