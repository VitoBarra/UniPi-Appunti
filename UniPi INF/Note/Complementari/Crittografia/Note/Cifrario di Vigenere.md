---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrario di Vigenere
---
è un [[Cifrari storici|cifraro storico]] 
e secondo la [[Classificazione di cifrari|classificazione dei cifrari]] è un cifrario _a sostituzione, polialfabetico_

#### Definizione
è basato su una tabella $\mathcal{T}$ nota pubblicamente. la tabella è $26 \times 26$ e ogni riga contiene l alfabeto ruotato di $i-1$ posizioni verso sinistra dove $0<i<27$ e la chiave $k$ è una frase mnemonica di lunghezza $h$ scelta a piacere. 
Solitamente piu $h$ è alto piu la sicurezza è alta ma comunemente si scelgono frasi brevi di senso compiuto. 

per creare il crittogramma si dispongono messaggio e chiave in righe adiacenti allineate in verticale 
sia $m$ il messaggio se succede che $k$ è piu corta di $m$ allora la chiave si ripete per tutta la lunghezza di $m$
cosi facendo ogni lettera $x$ del messaggio sarà allineata ad una lettera $y$ e la crittazione consiste nel sostituire la letta con quella che è al incrocio della riga di $\mathcal{T}$ che inizia per $c$ e della colonna di $\mathcal{T}$ che inizia per $y$
![[Pasted image 20230705123324.png]]
per la decrittazione si esegue il procedimento inverso

#### Osservazioni
essendo solitamente la lunghezza della chiave $k$ un numero $h$ solitamente minore del numero di lettere del messaggio $m$ possiamo costruire per ogni intero $i\leq h$ un sotto messaggio di $m$ tale che $m[i]$ siano tutte le lettere in posizione $i,i+h,i+2h,\dots$ 

notiamo che in quelle posizioni se le lettere del messaggio sono uguali queste verranno cifrate con la stessa lettera nel crittogramma, questo avviene siccome quelle lettere saranno allineate con la stessa lettera della chiave

in questo modo abbiamo di fatto decomposto il messaggio in sotto messaggi cifrati in modo _monoalfabetico_.
questo ci mostra la debolezza di questo cifrario che ha bassa sicurezza con chiavi corte.

