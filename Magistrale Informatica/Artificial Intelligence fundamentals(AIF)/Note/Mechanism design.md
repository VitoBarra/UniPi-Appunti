---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Mechanism design
---
il **Mechanism design** si occupa di struttura il giusto **gioco** per una collezione di [[agenti razionali|agenti razionali]], si stabiliscono le regole che governano le interazioni tra più agenti razionali. 

Un meccanismo si compone di tre elementi fondamentali: 
- un linguaggio per la descrizione delle strategie ammesse
- un **agente centrale** (il centro) che raccoglie le scelte strategiche e una regola d’esito che determina i pagamenti 
- le **regole del esito** usate dal centro per determinare i payoff agli agenti a seconda della loro strategia.

#### Contract Net Protocol
Il **Contract Net Protocol (CNP)** è uno dei protocolli più noti e studiati per la cooperazione tra [[Agenti Razionali|agenti]] in contesti [[Definizione di Problemi-Ambienti|multiagente]]. Esso fornisce un meccanismo ad alto livello per la condivisione dei compiti, ispirato al modo in cui le aziende utilizzano i contratti. Il protocollo si articola in quattro fasi principali:
1. **Riconoscimento del compito e annuncio**
   - Un agente identifica un compito che richiede cooperazione, perché non possiede le capacità per svolgerlo da solo o perché una soluzione cooperativa può risultare più efficiente.
   - L’agente pubblica un **messaggio di annuncio** contenente informazioni necessarie affinché gli altri agenti possano valutare la propria disponibilità: specifiche del compito, requisiti di qualità o tempi di completamento.
   - L’agente che pubblica l’annuncio assume il ruolo di **manager** del compito.
1. **Valutazione e offerta (bidding)**
   - Gli altri agenti ricevono l’annuncio e valutano la propria capacità e volontà di eseguire il compito.
   - Se un agente decide di partecipare, invia un **bid** (offerta) indicando le proprie capacità rilevanti e le condizioni per svolgere il compito.
1. **Assegnazione del compito (awarding)**
   - Il manager riceve le offerte e seleziona quella più adatta.
   - Il vincitore viene notificato tramite un messaggio di **award** e diventa il **contractor**, assumendosi la responsabilità di completare il compito.
1. **Esecuzione e generazione di sottocompiti**
   - Il contractor esegue il compito e, se necessario, può suddividerlo in sottocompiti, annunciandoli agli altri agenti secondo lo stesso schema.
il CNP è particolarmente efficace in contesti distribuiti in cui l’efficienza cooperativa dipende da una corretta valutazione delle capacità locali. Nonostante la sua semplicità, rappresenta uno dei framework più implementati e studiati per la risoluzione cooperativa di problemi, con applicazioni reali che spaziano dalla robotica ai sistemi di mobilità condivisa.
![[IMG - task allocation protocol.png]]

### Assegnare risorse tramite asta
L’**asta** è un [[Mechanism design|meccanismo]] per l’allocazione di risorse scarse in sistemi [[Definizione di Problemi-Ambienti|multiagente]]. Ogni offerente $i$ possiede un valore privato $v_i$ per il bene, e la propria offerta $b_i$ compete con quelle degli altri, determinando l’esito secondo le regole del tipo d’asta scelto.

Nell’asta ad **offerta crescente** (inglese), il prezzo parte da un minimo iniziale e cresce progressivamente fino a che un solo offerente resta **disposto a pagare**. In questo modo, il bene viene generalmente assegnato a chi lo valutai più, garantendo efficienza allocativa. Tuttavia, collusione tra pochi partecipanti o un numero ridotto di offerenti può ridurre sia l’efficienza sia i ricavi del venditore.

Le **aste a busta chiusa** richiedono meno comunicazione e impediscono accordi impliciti.k Nella versione a primo prezzo, il vincitore paga la propria offerta, mentre nella variante a secondo prezzo (Vickrey) paga il valore della seconda offerta più alta $b_o$. La funzione di utilità di un offerente $i$ può essere espressa come$$
U_i =
\begin{cases}
v_i - b_o & \text{se } b_i > b_o \\
0 & \text{altrimenti}
\end{cases}
$$In questa configurazione, la strategia dominante è **$b_i = v_i$**, rendendo il meccanismo veritiero e compatibile con gli incentivi dei partecipanti.

Secondo il teorema dell’equivalenza dei ricavi, sotto ipotesi standard tutte le aste con valori privati indipendenti generano lo stesso ricavo atteso, rendendo diversi meccanismi equivalenti dal punto di vista del venditore.  

Il meccanismo **Vickrey–Clarke–Groves** (VCG) generalizza l’idea di veridicità e ottimalità sociale, massimizzando l’utilità complessiva $\sum_i v_i$ e imponendo a ciascun vincitore una tassa pari alla perdita di utilità che la sua partecipazione provoca agli altri agenti. Questo incentiva ogni partecipante a dichiarare il proprio valore reale, poiché qualsiasi deviazione sarebbe subottimale, rendendo il meccanismo truthful e socialmente ottimale.


### Voting
Nella **teoria della scelta sociale**, la decisione collettiva si fonda sulla combinazione delle preferenze individuali in un ordinamento sociale complessivo. 
Si consideri un insieme di [[Agenti Razionali|agenti]] $N = \{1, \dots, n\}$, detti **elettori**, e un insieme di **alternative** $\Omega = \{\omega_1, \omega_2, \dots\}$, che rappresentano gli esiti possibili. 
Ogni agente $i$ definisce una relazione di preferenza $\omega \succ_i \omega'$, esprimendo un ordinamento qualitativo tra le alternative. Il problema centrale consiste nel derivare da tali preferenze un ordinamento collettivo $\omega \succ^* \omega'$ o, in forma ridotta, un insieme di vincitori mediante una funzione di scelta sociale.

Questo pero puo incontrare casi paraddossali infatti facendo ilcaso di $\Omega = \{\omega_a,\omega_b,\omega_c\}$ e $N=\{1,2,3\}$ poiché può accadere che le preferenze siano distribute 
- $\omega_a \succ_1 \omega_b \succ_1 \omega_c$
- $\omega_c \succ_a \omega_b \succ_2 \omega_b$
- $\omega_b \succ_1 \omega_c \succ_1 \omega_a$ 
e quindi non si puo fare una scelta che accontenti la magioranza. Tale risultato, noto come **paradosso di Condorcet**.

Le proprietà desiderabili di una funzione di benessere sociale comprendono: 
- **la condizione di Pareto**: secondo cui se ogni elettore preferisce $\omega_i$ a $\omega_j$, allora $\omega_i \succ^* \omega_j$; 
- **la condizione del vincitore di Condorcet**: che impone di collocare al primo posto un’alternativa che prevale su tutte le altre nei confronti a coppie;
- **l’indipendenza dalle alternative irrilevanti**:, per cui la posizione relativa di $\omega_i$ e $\omega_j$ non deve variare se cambia la valutazione di alternative diverse; 
- **no dittature**: che esclude il predominio delle preferenze di un singolo agente sul gruppo. Tuttavia
il **teorema di Arrow** dimostra che nessuna regola di aggregazione può soddisfare simultaneamente tutte queste condizioni quando il numero delle alternative è $n>2$

I principali meccanismi di voto propongono differenti modalità di aggregazione:
- **Il voto di maggioranza** si applica nel caso di due alternative e seleziona quella preferita dalla maggioranza assoluta. Il voto di pluralità considera soltanto la prima scelta di ciascun elettore e assegna la vittoria all’alternativa con il maggior numero di preferenze principali. 
- **Il metodo di Borda**, invece, attribuisce punteggi decrescenti da $k$ a $1$ in base alla posizione nell’ordinamento individuale, producendo un risultato che tiene conto dell’intera distribuzione delle preferenze.
- **Il voto di approvazione** consente a ciascun elettore di indicare le alternative approvate, selezionando come vincitori quelle con il maggior numero di consensi.
- **il voto a eliminazione progressiva** (**instant runoff**) elimina successivamente i candidati con meno preferenze di primo posto, aggiornando a ogni turno le classifiche fino all’ottenimento di una maggioranza.
- **la regola di maggioranza vera**: confronta ogni coppia di alternative e identifica come vincente quella che prevale in tutti i confronti diretti, qualora tale alternativa esista.

Un ulteriore limite strutturale dei meccanismi di voto è espresso dal **teorema di Gibbard-Satterthwaite**, che stabilisce l’impossibilità di costruire una funzione di scelta sociale non manipolabile e non dittatoriale per domini con più di due alternative. Ogni procedura che rispetti il principio di Pareto ammette quindi, in alcuni casi, la possibilità che un elettore tragga vantaggio strategico dal dichiarare preferenze diverse da quelle reali, evidenziando la tensione tra razionalità individuale e coerenza collettiva nel processo decisionale.


### Bargaining
Nel modello di negoziazione ad offerte alternate, due agenti interagiscono in una sequenza di turni successivi. Al turno iniziale, l’agente $A_1$ formula una proposta; l’agente $A_2$ può accettarla, determinando così l’accordo, oppure respingerla, innescando un nuovo turno in cui i ruoli si invertono. Il processo continua finché non si raggiunge un accordo o finché entrambi gli agenti persistono nel rifiuto, caso in cui si verifica l’esito di conflitto, meno desiderabile per entrambi. Si assume che gli agenti preferiscano sempre un accordo finito al conflitto indefinito.

Si consideri un bene indivisibile di valore unitario, rappresentato come una risorsa divisibile in proporzioni $(x, 1 - x)$, dove $x$ è la quota destinata ad $A_1$ e $1 - x$ quella ad $A_2$. Lo spazio delle possibili offerte, o insieme di negoziazione, è quindi descritto da $\{(x, 1 - x) : 0 \leq x \leq 1\}$. Quando non si impone un limite ai turni, si ottiene una molteplicità di equilibri di Nash, poiché ogni proposta $(x, 1 - x)$ può essere sostenuta da una coppia di strategie coerenti con tale equilibrio. Per ridurre l’indeterminatezza, si introduce il concetto di impazienza: gli agenti valutano meno favorevolmente i guadagni futuri rispetto a quelli immediati. Questa caratteristica viene modellata tramite un fattore di sconto $\gamma_i$, con $0 \leq \gamma_i < 1$, che determina il valore attualizzato di una porzione $x$ ricevuta al tempo $t$, pari a $\gamma_i^t x$. Maggiore è $\gamma_i$, maggiore è la pazienza dell’agente e più elevata la sua capacità di ottenere una quota superiore dell’accordo finale. In equilibrio, con due agenti aventi fattori di sconto $\gamma_1$ e $\gamma_2$, la quota spettante ad $A_1$ risulta $1 - \dfrac{\gamma_2}{1 - \gamma_1 \gamma_2}$, mentre ad $A_2$ spetta la parte residua.

Nelle negoziazioni orientate ai compiti, l’oggetto della trattativa è l’assegnazione di un insieme di attività $T$ a due agenti, a partire da una distribuzione iniziale $(T_1^0, T_2^0)$. Ogni sottoinsieme di compiti $T'$ comporta un costo $c(T')$, crescente con la numerosità dei compiti e nullo per l’insieme vuoto. Un’offerta $(T_1, T_2)$ è accettabile se è individualmente razionale, ossia se per ogni agente $i$ si ha $U_i((T_1, T_2)) = c(T_i^0) - c(T_i) \geq 0$. L’insieme di negoziazione, in tal contesto, è costituito dalle allocazioni che risultano al tempo stesso individualmente razionali e Pareto ottimali.

Il protocollo di concessione monotona regola il processo negoziale in turni simultanei, in cui ciascun agente propone un accordo. L’intesa è raggiunta se uno dei due considera la proposta altrui almeno equivalente alla propria. In assenza di accordo, ciascun agente deve nel turno successivo mantenere o migliorare la proposta a favore dell’altro, effettuando così una concessione. Se entrambi cessano di concedere, la negoziazione termina con il ritorno all’allocazione iniziale. Poiché lo spazio delle possibili offerte è finito, la procedura non può protrarsi indefinitamente, anche se il numero di turni può crescere esponenzialmente con la dimensione di $T$.

La strategia di Zeuthen fornisce un criterio comportamentale per questo protocollo. Essa misura la propensione di un agente a rischiare il conflitto, definita come il rapporto tra l’utilità che perderebbe concedendo e quella che perderebbe non concedendo e incorrendo nel conflitto:
$$
\text{risk}_i^t = \frac{\text{utilità persa concedendo e accettando l’offerta di } j}{\text{utilità persa non concedendo e subendo il conflitto}}.
$$
Valori alti di $\text{risk}_i^t$ indicano minore disponibilità alla concessione, poiché l’agente ha poco da perdere dal conflitto. A ogni turno, deve concedere l’agente con minore rischio, cioè quello che avrebbe più da perdere in caso di fallimento. La concessione deve essere minima, sufficiente a invertire la situazione di rischio. Se entrambi presentano uguale rischio, la scelta di chi concede è decisa casualmente. In tali condizioni, l’accordo risultante è individualmente razionale, Pareto ottimale e in equilibrio di Nash, pur richiedendo un numero potenzialmente elevato di valutazioni del costo per la determinazione delle proposte ottimali.
