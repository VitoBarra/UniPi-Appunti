---
Course: Crittografia
topic: nota
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrario di Vigenere
---
è un [[Cifrari storici|cifraro storico]] 
e secondo la [[Classificazione di cifrari|classificazione dei cifrari]] è un cifrario _a sostituzione, polialfabetico_

#### Definizione
è basato su una _tabella_ $\mathcal{T}$ nota _pubblicamente_. la tabella è $26 \times 26$ e ogni riga contiene l alfabeto ruotato di $i-1$ posizioni verso sinistra dove $0<i<27$ e la chiave $k$ è una frase mnemonica di lunghezza $h$ scelta a piacere. 
Solitamente piu $h$ è alto più la sicurezza è alta ma comunemente si scelgono frasi brevi di senso compiuto. 

per _cifrare_ il messaggio si dispongono messaggio e chiave in righe adiacenti allineate verticalmente 
_sia_ $m$ il messaggio _se_ $k$ è più corta di $m$ _allora_ la chiave si ripete per tutta la lunghezza di $m$
cosi facendo ogni lettera $x$ del messaggio sarà allineata ad una lettera $y$ e la _cifratura_ consiste nel sostituire la lettera con quella che è al incrocio della riga di $\mathcal{T}$ che inizia per $x$ e della colonna di $\mathcal{T}$ che inizia per $y$
![[Pasted image 20230705123324.png]]
per la decrittazione si esegue il procedimento inverso

#### Debolezze
la lunghezza $h$ di una chiave $k$ è solitamente _minore_ della lunghezza del messaggio $m$ il che ci permette di  costruire per ogni intero $i\leq h$ un sotto messaggio di $m$ tale che $m[i]$ siano tutte le lettere in posizione $i,i+h,i+2h,\dots$ 

notiamo che in un _sotto messaggio_ $m[i]$ _lettere uguali_ verrano _cifrate con la stessa lettera nel crittogramma_. questo avviene siccome per costruzione ogni lettera del sotto messaggio  $m[i]$ è allineata con la _stessa lettera della chiave_

In questo modo abbiamo di fatto decomposto il messaggio in piu sotto messaggi cifrati in modo _monoalfabetico_.
Questo ci mostra la debolezza di questo cifrario che ha bassa sicurezza con chiavi corte.

##### Calcolare lunghezza della chiave
Sapendo che ci sono dei _[[Critto analisi Statistica|q-grammi]]_ e _parole ripetute_ posso riuscire a trovare coppie di sotto sequenze uguali. 
_Siano_ $p_{1}, p_{2}$ la posizione in cui iniziano le sotto sequenze identiche _abbiamo_ che la distanza $d=p_{2}-p_{1}$ è la lunghezza $h=d$ della chiave.

se ci sono piu distanze $d',d'',\dots$ la lunghezza $h$ deve essere un loro divisore comune.
