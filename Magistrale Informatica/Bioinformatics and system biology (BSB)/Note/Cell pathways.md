---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# Cell pathways
---
I **Cell pathways** sono reti di reazioni biochimiche interconnesse che descrivono un processo cellulare specifico, come metabolismo, trasduzione del segnale o regolazione dell’espressione genica.

Formalmente, un pathway è modellato come una [[Chemical Reaction Network (CRN)|Chemical Reaction Network]] in cui:
- Nodi: specie molecolari (metaboliti, [[proteine|proteine]], complessi, [[RNA|RNA]]).  
- Archi: reazioni chimiche che trasformano un insieme di reagenti in prodotti.  
Una reazione generale ha forma:
$$\ell_1 S_1 + \dots + \ell_\rho S_\rho \xrightarrow{k} \ell'_1 P_1 + \dots + \ell'_\gamma P_\gamma$$
dove $\ell_i$ sono coefficienti stechiometrici e $k$ è la costante cinetica.

Dal punto di vista dinamico, i pathways sono descritti tramite:
- modelli deterministici basati su [[Ordinary Differential Equation (ODE)]], secondo la legge di azione di massa;
- modelli stocastici quando il numero di molecole è basso;
- modelli qualitativi in assenza di parametri cinetici noti.

Caratteristiche strutturali:
- Condivisione di specie: il prodotto di una reazione può essere reagente di un’altra.
- Modularità: sottoinsiemi di reazioni possono costituire moduli funzionali.
- Conservazione: alcune quantità sono vincolate da relazioni stechiometriche.

Dal punto di vista funzionale, i pathways descrivono:
- flussi metabolici (es. degradazione o sintesi di molecole),
- cascata di segnalazione,
- cicli regolatori.
