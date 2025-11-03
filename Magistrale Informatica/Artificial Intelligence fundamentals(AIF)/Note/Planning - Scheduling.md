---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Planning - Scheduling
---
il **planning con scheduling** è una variante della [[Planning|pianificazione]] che tiene conto **durata delle azioni** e **del momento** in cui devono essere eseguite delle azioni per raggiungere un **goal**.
Per affrontare questi aspetti, è necessario introdurre concetti di **scheduling** e gestione delle **risorse**.

Un approccio comune consiste nel separare la pianificazione dalla schedulazione, adottando la strategia "**plan first, schedule later**". 
- la fase di **pianificazione** si selezionano le azioni con vincoli di ordine parziale necessari per raggiungere gli obiettivi, 
- la fase di **schedulazione** si assegnano tempi di inizio e fine delle azioni rispettando sia i vincoli temporali sia quelli sulle risorse, calcolando eventualmente la durata complessiva del piano, detta **makespan**.  

Ogni azione $A$ possiede una durata $Duration(A)$ e requisiti specifici di risorsa. Le risorse possono essere **consumabili**, cioè non più disponibili dopo l’uso, oppure **riutilizzabili**, liberandosi automaticamente al termine dell’azione. La rappresentazione delle risorse può essere effettuata tramite **quantità aggregate**, ossia un singolo numero per ciascun tipo di risorsa, in modo da ridurre la complessità della ricerca evitando di distinguere le singole istanze.

La schedulazione temporale **senza vincoli sulle risorse** può essere affrontata mediante il **Critical Path Method (CPM)**. Si costruisce un **grafo diretto**, in cui i nodi rappresentano le azioni e gli archi indicano vincoli di precedenza $A \prec B$. Per ciascuna azione si definiscono:
- **Tempo di inizio più presto** $ES(A)$  
- **Tempo di inizio più tardi** $LS(A)$  
mentre lo **slack** di un’azione è definito come:
$$
\text{slack}(A) = LS(A) - ES(A)
$$
e rappresenta il margine temporale disponibile per l’esecuzione dell’azione. Il **percorso critico** è la sequenza di azioni per cui lo slack è zero, e determina la **durata totale** del piano.

Dato un [[Ordinamenti|ordinamento parziale]] delle azioni, per ottenere uno scheduling con il **makespan minimo** è sufficiente calcolare i tempi di inizio più presto ($ES$) e più tardi ($LS$) per tutte le azioni. Questo calcolo può essere effettuato iterativamente tramite le formule:$$
\begin{aligned}
&ES(\text{Start}) = 0 \\
&ES(B) = \max_{A \prec B} \big( ES(A) + Duration(A) \big) \\
&LS(\text{Finish}) = ES(\text{Finish}) \\
&LS(A) = \min_{B \succ A} \big( LS(B) - Duration(A) \big)
\end{aligned}
$$Si procede iterando queste formule fino a quando $ES$ e $LS$ sono assegnati a tutte le azioni. Questa operazione può essere implementata tramite [[Programmazione Dinamica|programmazione dinamica]] con una [[Complessita|complessità]] pari a $O(Nb)$, dove $N$ è il numero di azioni e $b$ è il massimo branching factor, ovvero il numero massimo di azioni direttamente precedenti o successive a ciascuna azione nel grafo di ordinamento.  
un esempio:
![[IMG - Esmpio Scheduling.png]]


L’introduzione di **vincoli sulle risorse** aggiunge complessità, poiché azioni concorrenti che richiedono la stessa risorsa non possono sovrapporsi. Questo comporta vincoli di tipo disgiuntivo, rendendo il problema [[Complessita|NP-hard]]. La soluzione ottimale richiede quindi di considerare sia le precedenze temporali sia la disponibilità delle risorse, con possibili ritardi rispetto alla durata minima calcolata senza vincoli di risorsa.  Per affrontare problemi complessi di scheduling si possono adottare euristiche come la **minimum slack**, che pianifica per prima l’azione non ancora schedulata con minor margine, aggiornando iterativamente $ES$ e $LS$ delle azioni influenzate. In scenari più articolati, può essere vantaggioso integrare pianificazione e schedulazione, considerando durate e sovrapposizioni già durante la costruzione del piano, riducendo così la probabilità di conflitti e aumentando l’efficienza complessiva
![[IMG - Planning - Scheduling esempio con risorse.png]]