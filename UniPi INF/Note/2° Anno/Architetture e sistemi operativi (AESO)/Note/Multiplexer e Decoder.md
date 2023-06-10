---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Multiplexer e Decoder
---
[[Componenti]]
## Multiplexer

il multiplexer è un componente che scegli quale lavore dare in uscita tramite un input di selezione detto segnale di controllo

![[UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 13.png]]

questi possono essere costruiti utilizzando

- buffer three state

   ![[UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 1 5.png]]

- logica a due livelli

    ![[UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 2 4.png]]


per si possono costruire MUX che sono N:1 a patto che ci siano $log_2N$ bit nel segnale di controllo

i mux si possono usare come tabelle di ricerca (LookUp Table) che non sono altro che i valori già risolti di funzioni logiche selezionabili con il segnale di controllo. un mux con $2^N$ ingressi può realizzare una qualsiasi funzione con $N$ ingressi

---

## Decoder

un decoder è un componente che ha $N$ ingressi e $2^N$ uscite e attiva una delle sue uscite a seconda della combinazione di valori in ingresso

![[UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 3 4.png]]

un decoder può essere usato per realizzare funzioni logiche come se fosse una rete a due livelli

![[UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 4 3.png]]

in generale una funzione ad $N$  ingressi può essere costruita con un decoder $N:2^N$ e una porta OR a $M$ ingressi dove $M$ è il numero degli uno nelle uscite nella tabella di verita

è realizzato con NOT e AND

![[UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 5 1.png]]