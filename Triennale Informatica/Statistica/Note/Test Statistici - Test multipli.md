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
Nel contesto dei [[Test Statistici|test statistici]] multipli si considerano simultaneamente $N$ ipotesi $$\mathcal{H}_{0,1},\dots,\mathcal{H}_{0,N}$$ ciascuna associata a un proprio test e [[Test Statistici - p-value|p-value]].

Siano:
- $R$ = numero totale di ipotesi rifiutate  
- $V$ = numero di falsi positivi (false discoveries)  
- $S$ = numero di veri positivi  
- $T$ = numero di falsi negativi  
Vale la relazione $$R = V + S$$ Le quantità $V$ e $R$ sono [[Variabili Aleatorie (Casuali)|variabili aleatorie]]; da esse derivano nuove metriche globali di controllo dell’errore.

La **Family-Wise Error Rate (FWER)** è definita come $$\mathrm{FWER} = \mathcal{P}(V \ge 1)$$ Essa misura la probabilità di commettere **almeno un errore di [[Test Statistici - significativita e potenza di un test|prima specie]]** tra tutti i test effettuati.

Se ogni [[Test Statistici - significativita e potenza di un test|test è condotto al livello]] $\alpha$, la probabilità di commettere almeno un falso positivo cresce con $N$. Se i test sono [[Indipendenza Stocastica|indipendenti]]: $$\mathcal{P}(V\geq 1) = 1-(1-\alpha)^N$$ Per $N$ grande tale probabilità tende rapidamente a $1$, anche per valori piccoli di $\alpha$. Questo fenomeno è detto **inflazione dell’errore di prima specie globale**.

Il **False Discovery Rate (FDR)** è definito come $$\mathrm{FDR} = \mathbb{E}\!\left[\frac{V}{R}\right]$$ convenzionalmente $\frac{V}{R}=0$ se $R=0$. La FDR rappresenta la proporzione [[Variabili aleatoria - Momenti|attesa]] di falsi positivi tra tutte le ipotesi rifiutate.

Se tutte le ipotesi nulle fossero vere, il numero atteso di falsi positivi sarebbe circa $\alpha N$. Se alla soglia $\alpha$ si osservano $R_\alpha$ rifiuti, una stima intuitiva della proporzione attesa di falsi tra i rifiuti è $$\frac{\alpha N}{R_\alpha}$$
