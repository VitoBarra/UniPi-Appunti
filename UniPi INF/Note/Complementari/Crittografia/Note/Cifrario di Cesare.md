---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrario di Cesare
---
è un [[Cifrari storici|Cifrario Storico]] usato da giulio cesare ed è il primo di concezione moderna.

#### Definizione
_sia_ $m$ il messaggio in chiaro il crittogramma $c$ è generato sostituendo ad ogni lettera di $m$ la lettera di 3 posizioni avanti nel alfabeto assumendo che questo sia circolare.
![[Pasted image 20230704180529.png]]

#### Generalizzazione
questo si puo generalizzare aumentando lo spazio delle chiavi $K$ 

invece di ruotare l alfabeto di 3 posizioni lo si fa di $k$ posizione con $0<k<26$ dove $0$ e $26$ si evitano siccome lascerebbero il messaggi _invariato_.

in questo modo lo spazio delle chiavi $K$ ha cardinalità $|K|=25$ che è meglio di $1$.

#### Formalizzazione
si da una descrizione formale del cifrario di cesare
_sia_ $pos(x)$ la posizione nel alfabeto con $pos(A)=0$ e $pos(Z)=25$ e sia la chiave $0<k<26$
la [[Cifratura e Decifratura|funzione di cifratura/decifratura]] sulle singole lettere sono definite come
$$
\begin{array}
\mathcal{C}_{i}(x)=(pos(x)+k) \mod 26 \\
\mathcal{D}_{i}(x)=(pos(x)-k) \mod 26
\end{array}
$$
queste due operazioni possono essere immaginate come la rotazione in dischi concentrici.
![[Pasted image 20230704181826.png]]
##### Osservazioni
Questo cifrario gode della proprietà _commutativa_ infatti abbiamo che.
$$
\begin{array}{}
\mathcal{C}(\mathcal{C}(m,k_{1}),k_{2})) & = & \mathcal{C}(m,(k_{1}+k_{2})\mod 25) \\
\mathcal{D}(\mathcal{D}(m,k_{1}),k_{2}) & = & \mathcal{D}(m,(k_{1}+k_{2})\mod 25)  \\ 
\end{array}
$$
inoltre si ha che 
$$
\mathcal{C}(\mathcal{D}(m,k_{1}),k_{2}))  =
\begin{cases}
\mathcal{C}(m,(k_{1}-k_{2})\mod 25)  &  if  & k_{1}\geq k_{2} \\
\mathcal{D}(m,(k_{2}-k_{1})\mod 25)  &  if  & k_{1}<k_{2}\\
\end{cases}
$$
possiamo concludere che una sequenza di $t$ operazioni di cifratura e decifratura si possono ridurre ad unica _Cifratura o decifratura_. 

da qui possiamo dire che comporre piu cifrari di questo tipo _NON_ aumenta la sicurezza.