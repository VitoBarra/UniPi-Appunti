---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
Area:
topic:
SubTopic:
---

# Test Statistici - Test multipli
---
Nel contesto dei [[Test Statistici|test statistici]] multipli si considerano simultaneamente $N$ ipotesi $$\mathcal{H}_{0,1},\dots,\mathcal{H}_{0,N}$$ ciascuna associata a un proprio [[Test Statistici - p-value|p-value]] $p_i$. Come nel caso di un singolo test, scegliere una soglia $t$ equivale a rifiutare $\mathcal{H}_{0,i}$ quando $p_i\leq t$; la differenza è che questa decisione viene ripetuta $N$ volte e l'errore va quindi valutato sull'insieme dei rifiuti.

Quando $\mathcal{H}_{0,i}$ è vera e il p-value è calibrato correttamente, $p_i$ è uniforme in $(0,1)$; in particolare $$\mathcal{P}(p_i\leq t\mid\mathcal{H}_{0,i}\text{ vera})=t$$ Un p-value piccolo è dunque evidenza contro la rispettiva ipotesi nulla, ma non è né la probabilità che essa sia vera né, da solo, la probabilità che il risultato sia un falso positivo. Nei test multipli anche alcuni p-value molto piccoli possono comparire per caso, perciò la loro interpretazione richiede una correzione o una procedura di controllo globale.

Siano:
- $R$ = numero totale di ipotesi rifiutate  
- $V$ = numero di falsi positivi (false discoveries)  
- $S$ = numero di veri positivi  
- $T$ = numero di falsi negativi  
Vale la relazione $$R = V + S$$ Le quantità $V$ e $R$ sono [[Variabili Aleatorie (Casuali)|variabili aleatorie]]; da esse derivano nuove metriche globali di controllo dell’errore.

La **Family-Wise Error Rate (FWER)** è definita come $$\mathrm{FWER} = \mathcal{P}(V \ge 1)$$ Essa misura la probabilità di commettere **almeno un errore di [[Test Statistici - significativita e potenza di un test|prima specie]]** (falso positivo) tra tutti i test effettuati.

Se ogni [[Test Statistici - significativita e potenza di un test|test è condotto al livello]] $\alpha$, la probabilità di commettere almeno un falso positivo cresce con $N$. Se i test sono [[Indipendenza Stocastica|indipendenti]]: $$\mathcal{P}(V\geq 1) = 1-(1-\alpha)^N$$ Per $N$ grande tale probabilità tende rapidamente a $1$, anche per valori piccoli di $\alpha$. Questo fenomeno è detto **inflazione dell’errore di prima specie globale**.

Per esempio, la [[Test Statistici - Bonferroni correction|correzione di Bonferroni]] sostituisce la soglia non corretta $\alpha$ con $\alpha/N$: in termini di p-value, si rifiuta solo se $p_i\leq\alpha/N$, oppure, in modo equivalente, se il p-value aggiustato $p_i^{\mathrm{adj}}=\min(1,Np_i)$ è al più $\alpha$.

Il **False Discovery Rate (FDR)** è definito come $$\mathrm{FDR} = \mathbb{E}\!\left[\frac{V}{R}\right]$$ convenzionalmente $\frac{V}{R}=0$ se $R=0$. La FDR rappresenta la proporzione [[Variabili aleatoria - Valore atteso|attesa]] di falsi positivi tra tutte le ipotesi rifiutate.

La FDR è quindi legata alla **soglia sui p-value** usata per rifiutare le ipotesi nulle. Se si fissa una soglia $t$, si rifiutano tutte le ipotesi con $p_i\leq t$; indicano con $R(t)$ il loro numero, sotto un'ipotesi nulla vera vale $\mathcal{P}(p_i\leq t)=t$. Se $N_0$ è il numero (ignoto) di ipotesi nulle realmente vere, il numero atteso di falsi positivi alla soglia $t$ è $$\mathbb{E}[V(t)] = N_0t$$ Perciò, quando $R(t)>0$, una stima intuitiva della frazione di falsi positivi tra i rifiuti è $$\frac{N_0t}{R(t)}\approx\frac{Nt}{R(t)}$$ dove l'ultima espressione usa l'approssimazione conservativa $N_0\approx N$.

Non bisogna però identificare $t$ con la FDR desiderata: $t$ è la soglia applicata ai singoli p-value, mentre la FDR è un tasso globale, dipendente anche da quanti rifiuti si ottengono. Abbassare $t$ tende a ridurre i falsi positivi, ma riduce anche la potenza e quindi il numero di scoperte. In alternativa a una soglia sui p-value grezzi, si possono usare i [[Test Statistici - Benjamini-Hochberg correction|p-value aggiustati BH]]: $p_i^{\mathrm{adj}}\leq q$ significa che l'ipotesi è significativa al livello FDR obiettivo $q$.

Il metodo di [[Test Statistici - Benjamini-Hochberg correction|Benjamini-Hochberg]] parte invece da un livello FDR obiettivo $q$: ordinati i p-value $p_{(1)}\leq\dots\leq p_{(N)}$, cerca il massimo indice $k$ tale che $$p_{(k)}\leq\frac{k}{N}q$$ e rifiuta le ipotesi corrispondenti a $p_{(1)},\dots,p_{(k)}$. La soglia effettiva è dunque $t=p_{(k)}$, scelta dai dati per controllare la FDR a livello $q$ (sotto le consuete condizioni di indipendenza o di dipendenza positiva).
