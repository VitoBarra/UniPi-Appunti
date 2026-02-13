---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
Area:
topic:
SubTopic:
---

# Test Statistici - Bonferroni correction
---
La **correzione di Bonferroni** è una procedura per il controllo della [[Test Statistici - Test multipli|Family-Wise Error Rate (FWER)]] quando si eseguono $N$ [[Test Statistici|test]] simultanei.

Siano $p_1,\dots,p_N$ i [[Test Statistici - p-value|p-value]] associati alle ipotesi $\mathcal{H}_{0,1},\dots,\mathcal{H}_{0,N}$.  
Se ogni test è condotto al livello $\alpha$, la probabilità di commettere almeno un errore di prima specie cresce con $N$.

La correzione consiste nel sostituire il livello $\alpha$ con $$\alpha^* = \frac{\alpha}{N}$$ e rifiutare $\mathcal{H}_{0,i}$ solo se $$p_i \le \frac{\alpha}{N}$$
da questi si possono definire definire i **p-value aggiustati Bonferroni** come $$p_i^{\text{adj}} = \min(1, N p_i)$$ Un test è significativo al livello globale $\alpha$ se $$p_i^{\text{adj}} \le \alpha$$La procedura garantisce $$\mathrm{FWER} \le \alpha$$senza richiedere [[Indipendenza Stocastica|indipendenza]] tra i test.


La correzione di Bonferroni è semplice e sempre valida, ma tende a essere conservativa quando $N$ è grande, riducendo la potenza del test rispetto a procedure che controllano la [[Test Statistici - Benjamini-Hochberg correction|FDR]].
