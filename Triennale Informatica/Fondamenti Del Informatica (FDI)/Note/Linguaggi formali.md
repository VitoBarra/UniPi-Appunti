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
I **linguaggi formali** costituiscono un elemento fondamentale nello studio della teoria dell'informazione e della computazione, fornendo una base rigorosa per la descrizione di sistemi simbolici e modelli computazionali. La loro definizione si basa su un insieme finito di simboli, denominato [[Alfabeto]] e indicato con la lettera $\Sigma$. A partire da tale alfabeto si generano tutte le possibili stringhe finite, che appartengono all'insieme $\Sigma^*$. Ogni linguaggio formale si definisce come un sottoinsieme di $\Sigma^*$, ovvero $L \subseteq \Sigma^*$.

L'insieme $\Sigma^*$ comprende tutte le concatenazioni finite dei simboli contenuti nell'alfabeto, incluse le stringhe vuote, rappresentate con il simbolo $\varepsilon$. Tale struttura è dotata dell'operazione di concatenazione, che consente di combinare due stringhe per produrre una nuova stringa appartenente ancora a $\Sigma^*$.

Nel contesto dei linguaggi formali si distinguono due aspetti principali: la **sintassi** e la **semantica**. La sintassi specifica l'insieme delle regole che determinano quali stringhe di simboli sono considerate ben formate all'interno del linguaggio, ovvero quali stringhe rispettano le regole strutturali. La semantica riguarda invece il significato attribuito alle stringhe sintatticamente corrette, che varia in base al contesto applicativo del linguaggio.

La rappresentazione dei linguaggi formali avviene tramite strumenti teorici come le [[Grammatiche formali]], le espressioni regolari e modelli computazionali come gli [[Automa a stati finiti]]. Le grammatiche, in particolare, permettono di generare e descrivere formalmente le stringhe che appartengono al linguaggio, specificandone la struttura in modo preciso.

La classificazione dei linguaggi formali segue la gerarchia di Chomsky, che ordina le diverse tipologie di linguaggi in funzione della loro complessità espressiva. I linguaggi regolari, che costituiscono la classe più semplice, possono essere riconosciuti mediante automi a stati finiti deterministici o non deterministici. Una classe più complessa è costituita dai linguaggi liberi dal contesto, generati da grammatiche context-free e riconoscibili tramite automi a pila. A livelli superiori si collocano i linguaggi sensibili al contesto e i linguaggi ricorsivamente enumerabili, per la cui definizione e riconoscimento si utilizzano modelli computazionali più potenti come le macchine di Turing.

Lo studio dei linguaggi formali include anche l'analisi delle proprietà di chiusura rispetto a operazioni fondamentali, quali l'unione, la concatenazione e la chiusura di Kleene, formalizzate nel modo seguente:

$$
L_1, L_2 \subseteq \Sigma^* \implies L_1 \cup L_2, \quad L_1 \cdot L_2, \quad L_1^* \subseteq \Sigma^*
$$

dove:
- $L_1 \cup L_2$ rappresenta l'unione dei due linguaggi;
- $L_1 \cdot L_2$ indica la concatenazione tra stringhe appartenenti a $L_1$ e $L_2$;
- $L_1^*$ è la chiusura di Kleene, cioè l'insieme di tutte le stringhe ottenute concatenando un numero arbitrario, anche nullo, di stringhe di $L_1$.

Attraverso l'impiego di strumenti formali e modelli teorici, i linguaggi formali permettono di analizzare, generare e controllare linguaggi artificiali, sistemi di comunicazione, linguaggi di programmazione e modelli di sistemi complessi, garantendo la distinzione tra la componente sintattica e il significato semantico associato alle stringhe.
