---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Burrows-Wheeler Transform (BWT)
La **Burrows–Wheeler Transform (BWT)** è una trasformazione reversibile di una stringa che nasce nel contesto della compressione dei dati, ma che ha trovato un ruolo centrale in bioinformatica, in particolare negli aligner basati su FM-index come [[Bowtie2 - Software di allineamento per RNAseq|Bowtie2]].

L’idea fondamentale non è comprimere direttamente la stringa, ma **riorganizzarla** in modo che caratteri simili finiscano vicini tra loro. Questo semplice riordino cambia drasticamente la struttura statistica del testo, rendendolo molto più comprimibile con tecniche standard (run-length encoding, codifica entropica, ecc.).



Supponiamo di avere una stringa $S$.  
Se ordiniamo tutte le sue rotazioni cicliche in ordine lessicografico, accade qualcosa di interessante: rotazioni che condividono prefissi lunghi finiscono una accanto all’altra.  

Poiché ogni rotazione è solo uno “shift” della stringa originale, i caratteri che precedono prefissi simili (cioè quelli che finiscono nell’ultima colonna della matrice ordinata) tendono a coincidere.

Risultato:  
nell’ultima colonna compaiono **blocchi di caratteri ripetuti**.

Ed è proprio questa colonna che costituisce la BWT.

---

## Costruzione passo per passo

Sia $S = s_1 s_2 \dots s_n$.

1. Si aggiunge un simbolo terminale $\$$ tale che:
   $$\$\ < c \quad \forall c \in \Sigma$$Questo simbolo:
   - garantisce che nessuna rotazione sia prefisso di un’altra  
   - rende la trasformazione invertibile  

1. Si costruiscono tutte le rotazioni cicliche di $S\$.
2. Si ordinano lessicograficamente queste rotazioni.
3. Si prende l’ultima colonna della matrice ordinata.  
   Questa è la BWT, indicata con $L$.
Formalmente$$\text{BWT}(S) = L$$La prima colonna della matrice ordinata si indica con $F$.

## Struttura nascosta della trasformazione

C’è una proprietà fondamentale:

- $F$ è semplicemente $L$ ordinata.
- Ogni carattere in $L$ ha una corrispondenza precisa con una posizione in $F$.

Questa corrispondenza è alla base della ricostruzione.

Il punto chiave è che l’ordinamento globale delle rotazioni induce una relazione locale molto forte tra $F$ e $L$.

---

## Perché migliora la compressione

Il motivo è puramente strutturale.

Se molte rotazioni iniziano con la stessa sequenza (cioè condividono un lungo prefisso), allora nel momento in cui vengono ordinate, queste righe saranno consecutive.

Il carattere che precede quel prefisso — cioè quello che finisce in $L$ — sarà spesso lo stesso per molte di quelle righe.

Quindi in $L$ si formano sequenze come:

AAAAAAA…
TTTTTT…
CCCCCC…

Questi blocchi sono altamente comprimibili.

La BWT non elimina ridondanza:  
la **riorganizza**.

---

## Ricostruzione: il Last-to-First Mapping

La trasformazione è completamente invertibile.

Si definiscono:

- $C[c]$ = numero di caratteri in $S\$ strettamente minori di $c$
- $\text{rank}_c(L,i)$ = numero di occorrenze di $c$ in $L[1..i]$

La relazione fondamentale è:
$$
LF(i) = C[L_i] + \text{rank}_{L_i}(L,i)
$$

Interpretazione:

- L’$i$-esima occorrenza di un carattere in $L$ corrisponde all’$i$-esima occorrenza dello stesso carattere in $F$.
- Questa funzione permette di “risalire” la stringa originale un carattere alla volta.

Procedura:
- Si parte dalla riga contenente $\$$.
- Si applica iterativamente $LF$.
- Si ricostruisce la stringa all’indietro.
- Dopo $n+1$ passi si ottiene $S\$.

---

## Collegamento con FM-index

La BWT da sola è interessante, ma il vero salto avviene quando viene combinata con:
- array $C$
- strutture dati per calcolare $\text{rank}$ efficientemente
Nasce così l’**FM-index**, che permette ricerca di pattern tramite backward search:
Dato un pattern $P = p_1 \dots p_m$, si procede da destra verso sinistra aggiornando un intervallo $[l,r]$:

$$
l = C[p_i] + \text{rank}_{p_i}(L,l-1) + 1
$$
$$
r = C[p_i] + \text{rank}_{p_i}(L,r)
$$

Se $l \le r$, il pattern è presente.

La complessità diventa:
- Ricerca: $O(m)$
- Spazio: compresso rispetto al testo esplicito


![vidoe](https://www.youtube.com/watch?v=0qMGAsrYS0g)