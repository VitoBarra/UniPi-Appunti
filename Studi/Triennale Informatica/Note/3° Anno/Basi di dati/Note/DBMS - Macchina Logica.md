---
type: nota
course: Data Base
topic: 
tags:
  - DB
Parent MOC: "[[Data Base (DB)]]"
---

# DBMS - Macchina Logica
---
La _Machina Logica_ di un [[Architettura di un DBMS|architettura di un DBMS]] gestisce

### Macchina logica
La _macchina logica offre_ una visione dei dati permanenti come un insieme di tabelle relazionali sulle quali si opera con gli operatori dell’SQL.
Essa prevede i seguenti
moduli:
- Il gestore delle autorizzazioni per controllare che solo gli utenti autorizzati facciano uso dei dati con le modalità consentite. 
- Il gestore del catalogo per trattare i metadati, ovvero le informazioni sulle caratteristiche logiche e fisiche dei dati presenti.
- Il _gestore delle interrogazioni_ per controllare la correttezza delle interrogazioni e stabilire la strategia migliore per eseguirle con un opportuno algoritmo detto _piano di accesso_.


#### Gestore delle interrogazioni 
La _gestione delle interrogazioni_, è svolta con le seguenti fasi:
1. _Controllo lessicale, sintattico e semantico_ dell’interrogazione e sua rappresentazione in forma di albero logico.
2. Riscrittura algebrica dell’albero logico.
3. _Ottimizzazione fisica_ e generazione del _piano di accesso_.
4. Esecuzione del _piano di accesso_.
Una volta controllata la correttezza dell’interrogazione, essa viene rappresentata con un albero logico, usando i seguenti operatori dell’algebra relazionale estesa per operare su [[Struttura dati - MultiInsieme|multinsiemi]], come accade in [[Linguaggio per Database - SQL|SQL]].
-  Proiezione senza l’eliminazione dei duplicati: $\pi_X^b(O)$, con $X$ alcuni attributi di $O$.
 - Eliminazione dei duplicati da un multinsieme: $\delta(O)$.
- Ordinamento del risultato: $\tau_X(O)$, con $X$ alcuni attributi di $O$.
 - Operatori insiemistici senza l’eliminazione dei duplicati: $O_1 \cup^b O_2, O_1 \cap^b O_2,O_1 -^b O_2$.

Gli operatori dell’[[Modello relazionale - Algebra Relazionale|algebra relazionale]] su insiemi per la restrizione, prodotto, giunzione e raggruppamento con aggregazioni non cambiano per applicarli a [[Struttura dati - MultiInsieme|multinsiemi]].



###### Riscrittura algebrica
Durante la _riscrittura algebrica_ si applicano tecniche di [[Algebra Relazionale - Trasformazione di espressioni|trasformazione dell’interrogazione]], basate sulle proprietà algebriche degli [[Modello relazionale - Algebra Relazionale|operatori relazionali]]

###### Ottimizzatore fisico