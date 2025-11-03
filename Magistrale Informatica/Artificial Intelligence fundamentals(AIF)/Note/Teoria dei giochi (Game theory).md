---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Teoria dei giochi (Game theory)

La **game theory** (teoria dei giochi) è la disciplina che studia la **decisione strategica** in presenza di più [[agenti razionali|agenti razionali]] le cui scelte si influenzano reciprocamente. Essa fornisce un modello formale per analizzare situazioni in cui l’esito di una decisione dipende non solo dalle azioni di un singolo agente, ma anche da quelle compiute dagli altri partecipanti.

Un *gioco* è definito da:
- un insieme di **giocatori** (agenti);
- un insieme di **azioni o strategie** disponibili a ciascun giocatore;
- una **funzione di utilità** che assegna un payoff a ogni combinazione di strategie;
- eventuali **regole** che determinano l’ordine delle mosse e l’informazione disponibile.

L’obiettivo di ogni agente è **massimizzare la propria utilità attesa**, tenendo conto delle strategie possibili degli altri. La soluzione tipica di equilibrio, in cui nessun agente ha incentivo a deviare unilateralmente dalla propria strategia, è detta **equilibrio di Nash**.

La teoria distingue diverse classi di giochi:
- **[[Teoria dei giochi - Giochi cooperativi|Cooperative games]]**: è possibile stipulare **accordi vincolanti** tra gli agenti, che possono così coordinarsi stabilmente per massimizzare il beneficio collettivo.
- **[[Teoria dei giochi - Giochi Non-Cooperativi|Non-cooperative games]]**: non esistono accordi vincolanti; ogni agente agisce autonomamente, ma la cooperazione può emergere spontaneamente se risulta vantaggiosa.
- **[[Giochi a somma zero|Zero-sum games]]**: il guadagno di un agente corrisponde esattamente alla perdita dell’altro (es. scacchi, poker).
- **General-sum games**: i payoff non si compensano esattamente; è possibile che più agenti guadagnino simultaneamente o che tutti perdano.
- **Simultaneous games** e **sequential games**: distinguono se le mosse vengono effettuate nello stesso momento o in ordine temporale definito.

La *game theory* trova applicazione in numerosi ambiti, tra cui economia, politica, biologia evolutiva e intelligenza artificiale distribuita. In AI viene utilizzata sia per il **design degli agenti**, che devono pianificare razionalmente in ambienti competitivi, sia per il **mechanism design**, ossia la progettazione delle regole e delle interazioni affinché il comportamento individuale razionale produca un risultato collettivo ottimale.
