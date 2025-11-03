---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area:
topic:
SubTopic:
---


# Giochi Non-Cooperativi - Social Welfare
---
nel contesto dei [[Teoria dei giochi - Giochi Non-Cooperativi|giochi noncooperativi]] il **Social Welfare** introduce una prospettiva esterna alla logica individuale dei giocatori, orientata alla **valutazione collettiva degli esiti**. Invece di analizzare il gioco dal punto di vista di [[Agenti Razionali|agenti]] che **massimizzano la propria utilità**, si assume la posizione di un osservatore benevolo che mira a scegliere l’esito complessivamente migliore per la società.

per scegliere la l esito migliore c è bisogno di alcuni creteri che quindini la scelta
- **ottimalita di pareto**: Un esito è detto di **Pareto ottimale** se **non** esiste un altro esito che **migliori la condizione di un giocatore senza peggiorare quella di nessun altro**. la **pareto ottimalita** impedisce al sistema di **sprechino utilità** ogni configurazione non di pareto ottimo implica uno spreco di utilità potenziale, in quanto si potrebbe incrementare il benessere di almeno un agente senza ridurre quello degli altri.
- **benessere sociale utilitaristico**, definito come la somma delle utilità individuali associate a un determinato esito: $U = \sum_i u_i$. Tale misura valuta il rendimento complessivo del sistema, ma ignora la distribuzione dell’utilità tra i giocatori e presuppone un’unica scala di misura comparabile per tutti. In presenza di preferenze soggettive, la comparabilità delle utilità diventa problematica, portando a paradossi distributivi, come quello del cosiddetto “mostro dell’utilità”, un individuo che attribuisce un valore sproporzionato ai propri guadagni.

Per affrontare il tema dell’equità, la teoria introduce criteri di benessere sociale egualitario. Un approccio [[Ricerca MiniMax|maximin]] propone di massimizzare l’utilità del giocatore peggiore, ovvero $\max \min_i u_i$, garantendo il miglior esito possibile al più svantaggiato. Altri indicatori, come il coefficiente di Gini, misurano il grado di disuguaglianza nella distribuzione dell’utilità. Tuttavia, tali criteri possono ridurre il benessere complessivo per ottenere una maggiore uniformità, sacrificando efficienza per equità.