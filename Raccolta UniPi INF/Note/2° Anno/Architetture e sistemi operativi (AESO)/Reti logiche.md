---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Reti logiche
---

Nel campo dell’elettronica digitale, un **circuito** è una rete elettrica che elabora
variabili a valori discreti. Una rete può essere vista come una scatola nera e ha:

- uno o più ingressi a valori discreti;
- una o più uscite a valori discreti;
- una specifica funzionale che descrive la relazione tra ingressi e uscite;
- una specifica di temporizzazione che descrive il ritardo tra il cambio degli ingressi e la risposta delle uscite.

la rete ha due sotto parti

- elementi che è a sua volta, una rete con ingressi,uscite e specifiche proprie,
- nodi che sono contatti eletrici la cui tensione trasmette una variabile a valore discreto.
    - gli ingressi ricevono valori dal mondo esterno
    - le uscite emettono valori all’esterno
    - nodi interni sono contatti che non sono né ingressi né uscite

![[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Untitled 10.png]]

---

## Categorizazione

### Combinatorie

le reti combinatorie restituiscono un uscita che dipende solo e solamente dagli ingressi, quindi non hanno memoria

Alcuni esempi di rete combinatoria sono le [[Porte Logiche]]

### Composizione combinatoria

per **compisizione combinatoria** si intende combinare elementi per generare una rete combinatorie piu grande

si seguono le seguenti regole:

- ogni elemento circuitale è di per sé combinatorio;
- ogni nodo della rete è un ingresso per la rete oppure è connesso solamente
a un terminale di uscita di un elemento della rete;
- la rete non contiene percorsi ciclici: ogni percorso che la attraversa passa
attraverso ogni nodo al massimo una volta.

### Sequenzioali

Le reti sequenzili sono reti con presenza di memoria. un dato ingresso non necessariamente da lo sempre lo stesso risultato siccome questo diepende daglie ingressi E dallo stato delle memorie presente nella rete.

### Composizione sequenziale sincrona

Le regole di composizione delle reti sequenziali sincrone stabiliscono che
una rete è una rete sequenziale sincrona se è formata da elementi circuitali
interconnessi in modo tale che:

- ogni elemento della rete è o un registro o una rete combinatoria
- deve essere presente necessariamente almeno un registro;
- tutti i registri ricevono lo stesso segnale di clock;
- ogni percorso ciclico contiene almeno un registro

### sequenziali Asincrone

nel pratico non si usano perche troppo complesse da usare, l importante ricordarsi che le reti sequenziali asincrone sono una forma piu generale di quelle sincrone, cosi come quelle digiatli sono una forma piu generale delle reti analogiche


