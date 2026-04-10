---
Course: "[[Architetture e sistemi operativi (AESO)]]"
topic: nota
tags: AESO
---

# Multiplexer e Decoder
---
[[Componenti]]
## Multiplexer

il multiplexer è un componente che scegli quale lavore dare in uscita tramite un input di selezione detto segnale di controllo

![[UniPi-Appunti/Triennale Informatica/Architetture e sistemi operativi (AESO)/Media/IMG - Multiplexer e Decoder 1.png]]

questi possono essere costruiti utilizzando

- buffer three state

   ![[UniPi-Appunti/Triennale Informatica/Architetture e sistemi operativi (AESO)/Media/IMG - Multiplexer e Decoder 2.png]]

- logica a due livelli

    ![[UniPi-Appunti/Triennale Informatica/Architetture e sistemi operativi (AESO)/Media/IMG - Multiplexer e Decoder 3.png]]


per si possono costruire MUX che sono N:1 a patto che ci siano $log_2N$ bit nel segnale di controllo

i mux si possono usare come tabelle di ricerca (LookUp Table) che non sono altro che i valori già risolti di funzioni logiche selezionabili con il segnale di controllo. un mux con $2^N$ ingressi può realizzare una qualsiasi funzione con $N$ ingressi

---

## Decoder

un decoder è un componente che ha $N$ ingressi e $2^N$ uscite e attiva una delle sue uscite a seconda della combinazione di valori in ingresso

![[UniPi-Appunti/Triennale Informatica/Architetture e sistemi operativi (AESO)/Media/IMG - Multiplexer e Decoder 4.png]]

un decoder può essere usato per realizzare funzioni logiche come se fosse una rete a due livelli

![[UniPi-Appunti/Triennale Informatica/Architetture e sistemi operativi (AESO)/Media/IMG - Multiplexer e Decoder 5.png]]

in generale una funzione ad $N$  ingressi può essere costruita con un decoder $N:2^N$ e una porta OR a $M$ ingressi dove $M$ è il numero degli uno nelle uscite nella tabella di verita

è realizzato con NOT e AND

![[UniPi-Appunti/Triennale Informatica/Architetture e sistemi operativi (AESO)/Media/IMG - Multiplexer e Decoder 6.png]]
