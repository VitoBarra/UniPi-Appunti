# Dipendenze

## Dipendenze logiche

avviene quando due istruzioni consecutive vogliono usare lo stesso registro la prima per scriverci un risultato e la seconda che vuole utilizzare quel risultato un esempio di questo è

```nasm
sub r0,r1,r2
add r1,r0,r2
```

questo codice cercherebbe di legere r0 sul banco dati ma al momento del esecuzione quel dato non è ancora li presente perche non ha ancora finito la fase di write back.

questo problema viene risolto dal pipeline forwarding ovvero invece di leggere il dato dal banco di registri lo si leggee direttamente dal risltato del alu multiplxando con gli altri segnali necessari. i segnali di gestione del farwarding vengono generati da un unita di gestione di dipendenze

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Microarchitetture/ARM V7/Pipeline/Dipendenze/Untitled.png]]

l unita di gestione delle dipendenze utilizza la codifica delle due istruzioni controllando che due registri siano uguali.

### casi non risolvibili con forwarding

quando voglio prima caricare qualcosa in un registro e poi utilizzarlo in una operativa

```nasm
LDR r0,[r1,#4]
SUB r3,r0,r4
```

in questo caso il farwarding non risolve il problema dovrebbe tornare indietro di due stadi e questo non ha senso con se non immettiamo una bolla dove non succede nulla.

## sommario

operativa e operativa $\implies$forwarding

load e operativa $\implies$+1 una bolla (ovvero uno stadio per per un giro sta fermo)

## Altri modi per risolvere il problema delle bolle

per risolvere il problema inrisolvibile con il forwarding sul pipeline  (ovvero load e operativa ) si possono scambiare le operazioni a patto che la semantica non cambi questo si decide con le leggi di Benustein che dice che

invertire due istruzioni e la stessa cosa se

e sono dette

- $R(1)\cap W(2) = \empty$   detta WAR (write afther read ) se non rispettata si configura un anti-dipendenza andrei a scrivere su qualcosa che è gia stato letto quindi potrei fare un cambio di registro e risolvere
- $W(1)\cap R(2) = \empty$  detta RAW (read afther write) se non rispettata si configura  un dipendenza ovvero cerco di leggere qualcosa che è stato scritto la riga prima
- $W(1)\cap W(2) = \empty$ detta WAW (write afther write) se non rispettata si configura una dipendenza sul output questo caso è anomalo  siccome scrivere due volte sullo stesso registro significa nullificare la prima scrittura, si presenta solo in casi di errori

## Dipendenze sul controllo

quando voglio fare un salto devo buttare le operazioni fatte sulle operazioni che non devo eseguire quindi questo poeterebbe a buttare 5 stadi

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Microarchitetture/ARM V7/Pipeline/Dipendenze/Untitled 1.png]]

 per miglioarere le cose si puo fare forwording e mandare il valore del nuovo PC gia calcoalato nello stadio di execute direttamete al PC cosi da ridurre gli stadi da scartare a 2

### Sommario

salto $\implies$ +2 bolle
