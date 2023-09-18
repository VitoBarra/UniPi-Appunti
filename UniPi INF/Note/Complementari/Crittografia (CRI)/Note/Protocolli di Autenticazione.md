---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Protocolli di Autenticazione
---
Supponendo la comunicazione tra _mitt_ e _dest_ i protocolli di _autenticazione_ risolvono il [[Identificazione, autentificazione, Firma digitale|problema di autenticare]] il messaggio $m$ accentandosi del identità del mittente _mitt_ e garantirne l interita del messaggio.

Per ottenere ciò i meccanismi di autenticazioni si servono di un valore chiamato _message Authentication Code_ ($MAC$) indicato con $\mathcal{A}(m,k)$ la chiave $k$ è una chiave usata _appositamente per l autenticazione_
il $MAC$ e allegato al messaggio in caso non sia richiesta la confidenzialità viene inviato $\langle m,\mathcal{A}(m,k)\rangle$ altrimenti $\langle\mathcal{C}(m,k'),\mathcal{A(m,k)}\rangle$ con $k,k'$ chiavi _diverse_. Una volta ricevuto il messaggio e il $MAC$ il _dest_ potrà ricalcolare $\mathcal{A}(m,k)$ e se questo coccide con quello che gli è arrivato allora il messaggio è _autenticato_.


Per rendere questo scambio del _MAC_ economico abbiamo che questo deve essere molto più piccolo del messaggio a cui è associato.
per fare cio abbiamo che lo spazio dei MAC è molto più piccolo dello spazio dei messaggi possibili e quindi abbiamo che la funzione $\mathcal{A}(m,k)$ non è [[Funzioni#Funzione Iniettiva|iniettiva]] e quindi non è [[Funzioni#Funzioni Invertibili|invertibile]].
non possiamo cioè risalire al messaggio $m$ a partire dal valore di $\mathcal{A}(m,k)$ siccome non c è un _associazione univoca_ tra i due


### Realizazioni
per realizzare i protocolli di autenticazioni solitamente si sceglie una _funzione_ [[Funzioni Hash One-Way|hash-one way]] e quindi abbiamo che 
$$\mathcal{A}(m,k)=h(mk)$$
scagliando $h$ tra le _funzioni hash crittograficamente_ sicure come SHA256 e MD5.


Esiste uno _MAC_ che è dal punto di visto teorico inattaccabile chiamato _One-time MAC_ che riprendere i concetti del [[Cifrario One-time Pad|cifrario one time pad]].


#### Con CBC
_Se_ il cifrario utilizza una [[Cifrario a Composizione di blocchi|cifratura a blocchi concatenata]](_CBC_)  si puo utilizzare l ultimo blocco  della cifratura come _MAC_.
questo siccome l ultimo blocco è funzione di tutto il messaggio.




