# Calcolabilità

# Calcolabilita (da invertire )

- Modelli di calcolo Per formalizzare le procedure di passi FINITI
    - cosa posso calcolare senza limiti di risorse (es tempo, numeri)
- Esistono problemi incalcolabili ben definiti e interessanti

I problemi formano delle classi e le classi formano delle gerarchie

Relazioni tra le classi di problemi

Proprietà che classificano i problemi in risolvibili e inrisolvibili

- come le determino se e possibile

# Procedure dette algoritmo

Un algoritmo e :

- composto di un insieme finito di istruzion
- Ciascuna istruzione vengono da un insieme Finito e sono rappresentabili finitamente  ovvero (x=y) posso cambiare y in modo infinito  ma e rappresentato in soli due termini
- Le istruzione hanno un effetto sui dati Discreti
- Una computazione e una serie di passi e i passi hanno un effetto limitato sui dati
- Applicare un passo prende un tempo finito
- Ogni passo si prende in modo non dipendente dalla dibustrazione  di Bernoulli (stat link)dai passi precedenti e dai dati attivi
- Non c e limite al numero di passi ne allo spaio per contenere i dati (finché siano finuti)

# Modelli di calcolo

### Machina di turing

E una quaterna

Dove Sigma e detto respingente e # bianco

$$
M(Q,\Sigma,q_a,\delta) \\
\Delta , \#  \in \Sigma

$$

$$
Q = \text{ e un alfabeto degli stati  (insieme finito)}\\
\Sigma = \text {alfabeto dei simbili} \\
q_0 = \text{stato iniziale  non e davvero uno  stato ma lo considerimo come tale come segnale di finine calcolo} \\
\delta = \text{funzione di transizione}\\
\delta : Q \times \Sigma \implies Q \cup\{h\} \times \Sigma \times \{L,R,- \} \\
\delta(q,\Delta) = (q',\Delta,R)
$$

La funzione $\delta$  rappresenta le istruzioni sono finite

 La macchina di Turing come idea passa da usare una pila di fogli illimitata  per rappresentare le istruzioni, da li si passa ad usare un foglio illimitato orizzontalmente e verticalmente foglio mappando le caselle del foglio  con gli indici $(i,j)$ . Successivamente si passa a una striscia di istruzioni

( aggiungere immagine Machina di Turing)

[[httpswww.notion.so]]

regole di inferenza per un strigna??

$$
-\over{\epsilon \in \Sigma *}
$$

$$
{\sigma \in \Sigma}\over{\sigma \in \Sigma^*}
$$

$$
s \in \Sigma^* \ s'\in \Sigma^* \over{s \cdot s' \in \Sigma *}
$$

Stringhe accettate dalla macchia di turing

$$
\Sigma^F=\Sigma^* (\Sigma \backslash\{\#\}) \cup \{\epsilon\}
$$

Esempio Passo di stati

$$
(q,v\underline{a}u)\rightarrow(q'v\underline{b}u) \ se\  \delta(q,a)=(q',b,-)
$$

$$
(q,vc\underline{u}n) \rightarrow (q',vc\underline{b}u) \ se \ \delta(q,u) = (q',b,R)
$$

Il concetto e che uno stato q e na stringa cambia se la funzione della transizione indica che in quello stato con il carattere c il risultato della valutazione e un nuovo stato q’ che contiene il valore appartenente al alfabeto a destra o a sinistra o nella posizione dello stato precedente.

una Computazione e

$$
M(x) = (q_o,\Delta x) \rightarrow^*(q,w)
$$

Dog $\rightarrow^*$ e la chiusi a riflessiva e transitiva

Le computazioni sono di due tipo

- terminano  è vero M(x) converge
- Non terminano  se c e sempre un altro passo che posso fare
- Stallo se non sappiamo eseguire il passo. Ad esempio gamma non e totale

Le operazioni sule macchine di Turing sono una logica ceca ma possiamo dare un significato a queste operazioni associando per esempio ai valori del alfabeto un significato, ad esempio un  alfabeto   \sigma = {I,II,III } possiamo dargli un senso di 1,2,3 e usando le transizioni possiamo utilizzarlo per sommare dei numero. Ovviamente  e estendibile a qualsiasi simbolo e significato.

## Sintassi astratta

$$
E:= n  | X | E_1 + E_2 | E_1 *E_2 | E_1 /  E_1| E_1 - E_2 \\
B := b | E_1-E_2 | \neg b | B_1 \lor B_2 \\
C := skip | x=E | C_1;C_2 | if\  B \ then \ C_1 \ else \ C_2 | \ while \ B \ do\  C | \ for \ x=E \ to \ E_1 \ do\  C
$$

Un linguaggio e composto da espressioni comandi mantiene dati che dipendono dal linguaggio questo booleani e naturali

Sodisfacibilita e calcolabilita: una espressione e soddisfacibile se esiste un procedura di un numero finiti di passi per calcolare l espressione
