---
Course: "[[Human Language Technology (HLT)]]"
tags:
  - HLT
Area: 
topic: 
SubTopic: 
Course 2:
---

# Regular expressions (Reg-ex)
---
Una *Regular expression* è un'espressione algebrica che identifica un'insieme di stringhe. 
Vengono usate per specificare quali stringhe vogliamo estrarre da un documento, per la loro ricerca soprattutto quando si ricercano pattern in un [[Words and Corpora|corpus]].

Le regex cercano all'interno di un corpus e restituiscono tutto il testo che fa match con il pattern ricercato. 

Nel ambito del [[Natural Language Processing]] le Regex vengono utilizzate per il pre-processing o come features per i classificatori e possono essere utili a catturare generalizzazioni.

Possono essere molto compatte e specificare pattern complessi.

La regex più semplice è una sequenza di caratteri, tipo una parola o un singolo carattere e si ricerca come `/parola/`.

Le regex son **case sensitive**, quindi `S` è diverso da `s`.


### Disgiunzione 
Si usa per dire: "Voglio il pattern che comprenda questo o quest'altro carattere", oppure un carattere da un'isieme di caratteri. Si usano le parentesi quadre.

- `[Ww]` W maiuscola o minuscola
- `[A-z]` una lettera, maiuscola o minuscola
- `[0-9]` una cifra

### Negazione
Si usa per dire: "Voglio il pattern che non comprenda questo".
Si usano le parentesi quadre con ^ davanti al simbolo da negare. Se ^ è il primo simbolo si nega tutto.

- `[^A-z]` nessuna lettera

### Pipe
Si usa per la disgiunzione. 
- `[Cc]iao|[Ss]ono` : Ciao o ciao o Sono o sono

### Modifiers
`?` : 1 o 0 istanze del carattere o patter prima di quello 
	`colou?r` : color o colour
`*` : La stella di Kleene indica zero o più occorrenze del patter o carattere precedente
	`ah*` : a ah ahh ahhh ahhhh ...
`+` : Kleene+ indica 1 o più occorrenze
	`ah+` : ah ahh ahhh ahhhh ...
`.` : è la wild card che indica un qualunque carattere
	`de.` : del dea dei ...

### Anchors and escape
Le ancore sono caratteri speciali che posizionano le regex in una specifica posizione della stringa. 
`^`: fuori dalle parentesi quadre per non indicare negazione e indica l'inizio della frase
`$`: indica la fine della frase
`\b` e `\B`: \b indica il boundary di una parola e \B il non boundary 
``

### Others operators
![[Regex operators 1.png]]
![[Regex operators 2.png]]
![[Regex operators 3.png]]
![[Regex operators 4.png]]
### Substitution and groups
Un loro uso importante è la *sostituzione* di una stringa con un'altra. In python e in Unix ciò viene fatto come: (sed, re.sub): `s/regexp1/pattern/`.

e.g.: `s/colour/color/`, sostituisce tutte le occorrenze della parola *color* con *colour*.

Di solito è utile per riferirsi ad una specifica sotto parte della stringa che corrisponde al pattern descritto. 

Se si vogliono catturare dei gruppi vengono usate le parentesi tonde, che numera ognuno di questi questi gruppi e lo salva in un registro.
Per richiamare il registro che si vuole usare si usa `<\n>`, dove n si riferisce al numero del registro. 

Per applicare la disgiunzione solo ad un pattern specifico si usano le parentesi tonde che rappresentano l'operatore and.
Racchiudendo un pattern nelle parentesi si possono applicare ai gruppi l'operatore pipe o l'operatore Kleene*.

L'operatore `(.*)` serve per catturare un gruppo. Dopo averlo catturato si può applicare la sostituzione per matchare diverse frasi.

Si hanno due modi per accedere ai registri:
1. `s / ([0-9]+) / <\1> /` 
2. `re.sub (r “([0-9]+)” lambda x: f “<{x.group(0)}>”, “the boxes 35”)`

Si possono anche utilizzare multipli gruppi in multipli registri.
![[Regex groups.png]]

se un non si vuole catturare un gruppo si aggiunge `?:` all'interno della parentesi. In questo modo tale gruppo non viene inserito nei registri 

La sostituzione e il catturare i gruppi sono tecniche molto utili per implementare chatbot che rispondono alla frase detta dall'utente 
Per esempio ELIZA, chatbot per conversazioni che imitano una seduta da un psicoterapeuta, individua i pattern e li inserisce all'internoodelle sue risposte

![[Regex ELIZA.png]]

### Problems
Il processo può andare incontro a due tipi di errori:
- Falsi positivi : trovare stringhe diverse da quelle ricercate
- Falsi negativi : non trovare le vere stringhe

Ciò si può risolvere:
- Aumentando l'accuracy o la precision, minimizzando i falsi positivi
- Aumentando la copertura o il recall, minimizzando i falsi negativi