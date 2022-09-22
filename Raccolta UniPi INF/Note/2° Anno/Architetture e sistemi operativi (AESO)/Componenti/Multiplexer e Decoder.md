# Multiplexer e Decoder

## Multiplexer

il multiplexer è un componente che scegli quale lavore dare in uscita tramite un input di selezione detto segnale di controllo

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Componenti/Multiplexer e Decoder/Untitled.png]]

questi possono essere costruiti utilizzando

- buffer three state

    [[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Componenti/Multiplexer e Decoder/Untitled 1.png]]

- logica a due livelli

    [[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Componenti/Multiplexer e Decoder/Untitled 2.png]]


per si possono costruire MUX che sono N:1 a patto che ci siano $log_2N$ bit nel segnale di controllo

i mux si possono usare come tabelle di ricerca (LookUp Table) che non sono altro che i valori già risolti di funzioni logiche selezionabili con il segnale di controllo. un mux con $2^N$ ingressi può realizzare una qualsiasi funzione con $N$ ingressi

---

## Decoder

un decoder è un componente che ha $N$ ingressi e $2^N$ uscite e attiva una delle sue uscite a seconda della combinazione di valori in ingresso

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Componenti/Multiplexer e Decoder/Untitled 3.png]]

un decoder può essere usato per realizzare funzioni logiche come se fosse una rete a due livelli

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Componenti/Multiplexer e Decoder/Untitled 4.png]]

in generale una funzione ad $N$  ingressi può essere costruita con un decoder $N:2^N$ e una porta OR a $M$ ingressi dove $M$ è il numero degli uno nelle uscite nella tabella di verita

è realizzato con NOT e AND

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Componenti/Multiplexer e Decoder/Untitled 5.png]]

---

Status : #NotSet

Tag: [Aeso](../../Architetture%20e%20sistemi%20operativi%20(AESO)%201e0e264228a748feabc5de07d5a770db.md)
