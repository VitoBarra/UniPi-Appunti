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

 