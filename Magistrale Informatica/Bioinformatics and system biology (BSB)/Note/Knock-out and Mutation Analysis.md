---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Knock-out and Mutation Analysis
---
La **Knock-out and Mutation Analysis** studia la risposta di un modello dinamico a perturbazioni strutturali o cinetiche, simulando alterazioni genetiche o biochimiche all’interno del sistema.

L’obiettivo è valutare come la modifica o la rimozione di un componente influenzi la dinamica globale del network, la stabilità degli stati stazionari o l’attivazione di specifici target.

Un modello dinamico può essere rappresentato come:
$$
\dot{x} = f(x,p)
$$
dove $x$ sono le variabili di stato e $p$ i parametri cinetici. Le perturbazioni possono agire:
- sulla struttura del modello (rimozione di un termine),
- sui parametri (modifica di una costante cinetica),
- sulle condizioni iniziali.

**Knock-out**  
Simula la perdita completa della funzione di un gene o di un enzima.  
Nel modello ciò può essere implementato:
- ponendo a zero la concentrazione iniziale della specie,
- eliminando il termine di produzione,
- annullando la costante cinetica associata a una reazione.

Formalmente, se una reazione dipende da una costante $k$, il knock-out può essere modellato come:
$$
k = 0
$$
oppure rimuovendo direttamente il termine corrispondente da $f(x,p)$.

**Mutation**  
Simula una perdita o un guadagno parziale di funzione.  
Si implementa modificando un parametro:
$$
k \rightarrow \alpha k
$$
con $\alpha > 1$ (gain-of-function) oppure $0 < \alpha < 1$ (loss-of-function).

Applicazioni principali:
- Predizione degli effetti di mutazioni genetiche.
- Studio dei meccanismi molecolari di malattia.
- Identificazione di nodi essenziali.
- Analisi di robustezza di pathway biologici.
- Validazione di ipotesi meccanicistiche.

### Esempio: pathway EGFR

Contesto biologico: il recettore EGFR può essere iper-attivato in presenza di mutazioni, causando fosforilazione persistente di ERK e proliferazione incontrollata.

Piano di analisi:

1. Simulare il pathway wild-type con parametri nominali.
2. Simulare una mutazione aumentando la costante di legame:
   $$
   k_{on} \rightarrow 3 k_{on}
   $$
3. Confrontare dinamica temporale e stato stazionario delle proteine target.

Interpretazione: un aumento di $k_{on}$ può produrre livelli sostenuti di proteine attivate anche in presenza di stimolo basso, indicando un comportamento iperattivato.

---

### Esempio: knock-out di MEK

Ipotesi: il knock-out di MEK impedisce la fosforilazione di ERK.

Implementazione nel modello:
$$
k_{MEK \rightarrow ERK} = 0
$$

Confronto tra dinamica wild-type e knock-out:
- nel wild-type si osserva attivazione transiente o sostenuta di ERK,
- nel knock-out l’attivazione di ERK è assente.

Interpretazione: MEK agisce come nodo essenziale nella cascata di segnalazione.