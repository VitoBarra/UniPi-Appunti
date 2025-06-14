---
Course: "[[Fondamenti Del Informatica (FDI)]]"
tags:
  - FDI
Area: 
topic: 
SubTopic:
---

# Logica del primo ordine (FOL)
---
La **logica del primo** è un generalizazione della [[Logica proposizionale|logica proposizionale]] piu espressiva che include anche **oggetti, relazioni e funzioni**. 
nella logica del **primo ordine** i [[Logica|modelli]] sono una struttura composta da  
- **Oggetti**: che sono le cose di cui vogliamo parlare, ovvero scrivere scrivere e fanno tutti parte del **dominio del modello** $D$ e sono quindi anche detti **domain element**. Il dominio deve essere non vuoto.    
- **[[Relazioni tra insiemi|Relazioni]]**: sono degli **[[Insiemi Matematici|insiemi]] di tuple ordinate** di oggetti, quindi $r \subseteq D \times D \dots \times D$ 
- **[[Funzioni|Funzioni]]**:  mappano gli argomenti ad esattamente un **altro oggetto** ed una relazione **[[Applicazioni tra insiemi|totale]]** e quindi ad ogni elemento del dominio questa funzione deve associare un oggetto corrispettivo, può succede che ci siano funzioni per cui il significato che si vuole rappresentare non ha senso che venga applicata a tutti gli oggetti ma questi si puo risolvere con un formalismo dove tutti gli oggetti per cui non ha senso definire la funzione vengono assegnati ad un oggetto fittizio. 
in piu il modello deve contenere un **interpretazione** che associa a dei **simboli** un dato oggetto o valore. I simboli utilizzati si distinguono in tre categorie: 
- **simboli costanti**, che rappresentano oggetti specifici;
- **simboli predicativi**, che denotano **relazioni** e prendono valori $false$ o $True$ 
- **simboli funzionali**, che descrivono **funzioni**.
 Ciascun simbolo possiede una determinata arità, indicante il numero di argomenti che accetta. 
L’**interpretazione** assegna ciascun simbolo un oggetto preciso all’interno del **modello** e le relazioni tra questi, collegando così il [[Linguaggi formali|linguaggio formale]] alla realtà modellata. l' **interpretazione** che sembra la piu ovvia è detta **interpretazione intesa** ma non è l unica possibile.
ad esempio usando solo due simboli $R,J$ si possono avere **infinite interpretazioni** a seconda del **modello** sottostante:
![[IMG - Logica del primo ordine (FOL) relazione nome oggetti.png]]
Le nozioni di **validità** e [[Conseguenza Logica (Deduzione)|conseguenza logica]], come in [[Conseguenza Logica (Deduzione)|logica proposizionale]], si fondano sull’insieme di tutti i **modelli possibili**.

il linguaggio formale della **logica del primo ordine** è composto da **frasi** che sono composte da **termini**, questi si dividono in:
- **Termini semplici**: constante che indica in modo univoco un **oggetto** una **funzione** o un **predicato**.
- **Termini Complessi**:   sono termini composti da piu termini, ad esempio $f(v_1,v_2, \dots, v_n)$ dove $f$ è un **termine** che indica una funzione $F$ del dominio e $v_i$ indica un oggetto del dominio, il termine nella sua interezza è il termine complesso.
le **frasi** posso essere invece 
- **AtomicSentence** (frasi atomiche): quando sono fatte da un singolo predicato che puo avere come input termini sia **semplici che complessi**.
- **ComplexSentence** (frasi complesse): combinano frasi atomiche con **connettori logici** ($\lnot$, $\land$, $\lor$, $\Rightarrow$, $\Leftrightarrow$) con la stessa semantica della [[logica proposizionale|logica proposizionale]].

il **linguaggio** può essere formalizzato tramite la notazione [[Backus Naur Form (BNF)|Backus–Naur form]]:$$
\begin{array}{ll}
\text{Sentence} &\rightarrow\ \text{AtomicSentence} \mid \text{ComplexSentence} \\[4pt]
\text{AtomicSentence} &\rightarrow\ \text{Predicate} \mid \text{Predicate(Term, ...)} \mid \text{Term} = \text{Term} \\[4pt]
\text{ComplexSentence} &\rightarrow\ (\text{Sentence}) \mid \lnot \text{Sentence} \mid \text{Sentence} \land \text{Sentence} \mid \text{Sentence} \lor \text{Sentence} \mid \text{Sentence} \Rightarrow \text{Sentence} \mid \text{Sentence} \Leftrightarrow \text{Sentence} \mid \text{Quantifier Variable, ... Sentence} \\[4pt]
\text{Term} &\rightarrow\ \text{Function(Term, ...)} \mid \text{Constant} \mid \text{Variable} \\[4pt]
\text{Quantifier} &\rightarrow\ \forall \mid \exists \\[4pt]
\text{Constant} &\rightarrow\ A \mid X_1 \mid \text{John} \mid \cdots \\[4pt]
\text{Variable} &\rightarrow\ a \mid x \mid s \mid \cdots \\[4pt]
\text{Predicate} &\rightarrow\ \text{True} \mid \text{False} \mid \text{After} \mid \text{Loves} \mid \text{Raining} \mid \cdots \\[4pt]
\text{Function} &\rightarrow\ \text{Mother} \mid \text{LeftLeg} \mid \cdots \\[6pt]
\text{Operator Precedence:} &\ \lnot,\ =,\ \land,\ \lor,\ \Rightarrow,\ \Leftrightarrow
\end{array}
$$
I quantificatori costituiscono l'elemento distintivo della logica del primo ordine, consentendo di esprimere proprietà e relazioni generali. 
- Il **quantificatore universale** $\forall$ indica che una proposizione vale per ogni elemento del dominio ovvero  $\forall x\,P(x)$ è vero se  è vero in tutte le **interpretazioni** estese del modello
- **quantificatore esistenziale** $\exists$ afferma l'esistenza di almeno un elemento che soddisfa la proposizione. ovvero  è vero se  è vero in almeno un'**interpretazione** estesa.

L'ordine dei quantificatori influenza profondamente il significato delle frasi. La combinazione di quantificatori diversi genera frasi con struttura annidata, come $\forall x \exists y \, P(x,y)$ e $\exists y \forall x \, P(x,y)$, le quali non sono logicamente equivalenti.

I quantificatori possono essere riscritti l'uno in funzione dell'altro tramite negazione, secondo le regole di **De Morgan** applicate ai quantificatori:$$
\begin{array}{}
\neg \exists x \, P  & \equiv &  \forall x \, \neg P,   \\
\neg \forall x \, P  & \equiv  & \exists x \, \neg P,  \\
\forall x \, P  & \equiv  & \neg \exists x \, \neg P,  \\
\exists x \, P  & \equiv  & \neg \forall x \, \neg P  
\end{array}
$$Poiché $\forall$ rappresenta una congiunzione sull'universo e $\exists$ una disgiunzione, tali equivalenze derivano direttamente dalla struttura logica del linguaggio.

L'uguaglianza $=$ è trattata come un predicato speciale che afferma l'identità tra i referenti di due termini. L'uso della negazione consente anche di esprimere disuguaglianze, indicate con $\neg (x = y)$ o $x \neq y$, necessarie per distinguere oggetti diversi in un modello.


