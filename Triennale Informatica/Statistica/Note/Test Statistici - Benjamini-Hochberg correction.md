---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
Area:
topic:
SubTopic:
---
# Test Statistici - Benjamini-Hochberg correction
---
La **correzione di Benjamini–Hochberg (BH)** è una procedura per il controllo del [[Test Statistici - Test multipli|False Discovery Rate (FDR)]] quando si eseguono $N$ [[Test Statistici|test]] simultanei.

Siano $p_1,\dots,p_N$ i [[Test Statistici - p-value|p-value]] associati alle ipotesi $\mathcal{H}_{0,1},\dots,\mathcal{H}_{0,N}$. Si ordinano in senso crescente $$p_{(1)} \le \dots \le p_{(N)}$$Fissato un livello di **FDR** $q \in (0,1)$ desiderato, si definisce $$k = \max \left\{ i \in \{1,\dots,N\} : p_{(i)} \le \frac{i}{N} q \right\}$$ e si rifiutano tutte le ipotesi $\mathcal{H}_{(1)},\dots,\mathcal{H}_{(k)}$ La procedura quindi controlla la **FDR** sotto [[Indipendenza Stocastica|indipendenza]] o dipendenze deboli tra i test. 


Da questa definizione si puo ricavare il **livello FDR piu piccolo** $q_i^*$ che accetta l ipotesi $i$ in modo che con $q_i> q_i^*$ l ipotesi è comunque accettata e $q_i<q_i^*$  è sempre rifiutata.   $$q_i^*= \frac{N}{i} p_{(i)}$$ Si impone monotonicità non decrescente dal basso $$p^{\text{adj}}_{(i)} = \min  (1,\min_{j \ge i} q_j^*)$$quindi si riporta ogni valore nell’ordine originale.

Un test è significativo al **livello FDR** $q$ se $$p^{\text{adj}}_i \le q$$Il valore $p^{\text{adj}}_i$ rappresenta il minimo **livello di FDR** per cui l’ipotesi verrebbe dichiarata significativa. Se si controlla la FDR a livello $q = 0.05$, la proporzione attesa di falsi positivi tra tutte le ipotesi rifiutate è circa $5\%$ in media.  La FDR è una proprietà dell’insieme dei rifiuti e non del singolo test; non è possibile identificare quali specifici risultati siano falsi positivi.
