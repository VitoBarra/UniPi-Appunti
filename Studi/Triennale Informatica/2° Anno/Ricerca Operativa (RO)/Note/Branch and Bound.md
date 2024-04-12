---
Subject: Ricerca Operativa
topic: nota
tags: RO
---

Prev: [[Ricerca Operativa (RO)]]

# Branch and Bound
---
consideriamo in problema di PLI

$$
\begin{cases}
\max 5x_1 +6x_6 \\
3x_1 +4x_2 \leq 7 \\
x_1 \geq 0, x_2 \geq 0 \\
x \in \mathbb{Z}^2
\end{cases}
$$

I vincoli implicano che $x_1=0 \ \lor x_1=1 \ \lor x_1=2$.

facciamo un [[Partizione di un insieme]] della regione ammissibile $\Omega$ in tre Sottoinsieme:

$$
\Omega = (\Omega \cap \{x_1=0\}) \cup(\Omega \cap \{x_1=0\}) \cup (\Omega \cap \{x_1=0\})
$$

  che corrispondono al primo livello del [[Albero di decisione]]:

![[UniPi-Appunti/Studi/Triennale Informatica/2° Anno/Ricerca Operativa (RO)/Media/Untitled 27.png]]

![[UniPi-Appunti/Studi/Triennale Informatica/2° Anno/Ricerca Operativa (RO)/Media/Untitled 1 21.png]]

- L’enumerazione esplicita è molto costato dal pinta di vista computazionale
- Possiamo pero esaminare e scartare le soluzioni a gruppi anziché singolarmente facendo cosi un enumerazione implicita


![[Untitled 2 14.png]]
![[Untitled 3 10.png]]

---

# Passi del metodo

- Branch(ramificazione): partizionare la regione ammissibile in sotto-regioni
- Bound (valutazione): stimare il valore ottimo di ogni sotto-problema
- Potatura: scarlatta le sotto-regioni che non contengono soluzioni migliori di quella corrente (o chiudere i corrispondenti nodi nel albero decisionale)
- Vista: in quale ordine visitare i nodi dell’ albero decisionale

## Partizione

- Le sotto-regioni si generano aggiungendo vincoli
- il risultato deve essere una partizione della regione ammissibile del problema intero $\Omega$ , per non perdere nessuna soluzione ammissibile che potrebbe essere ottima

![[Untitled 4 6.png]]

![[UniPi-Appunti/Studi/Triennale Informatica/2° Anno/Ricerca Operativa (RO)/Media/Untitled 5 3.png]]

## Valutazione

Una valutazione inferiore del valore ottimo di P è data dal valore della funzione
obiettivo in una qualunque soluzione ammissibile.

Una valutazione superiore del valore ottimo di ogni sotto-problema è data dal
valore ottimo di un suo rilassamento:

- Rilassamento continuo (eliminare i vincoli di interezza sulle variabili)

    $x \in \{0,1\} \implies 0 \leq x \leq 1$

    $x \in \mathbb{Z}_x \implies x \geq 0$

- Eliminazione dei vincoli
- somma di due o più vincoli ???

## Potatura Max

Un nodo $P_i$ del [[Albero di decisione]] può essere chiuso se vale una qualunque delle seguenti condizioni:

- il sotto-problema $P_i$ non ha soluzioni ammissibili
- $V_s(P_i) \leq V_i(P)$,cioè le soluzioni ammissibile di $P_i$ non sono migliori della soluzione ammissibile corrente
- $V_s(P_i) > V_i(P)$ e la soluzione ottima di $P_i$ è ammissibile per $P$. in tal caso si aggiorna $V_i(P) = V_s(P_i)$ e si chiude il nodo

## Potatura Min

Un nodo $P_i$ del albero decisionale può essere chiuso se vale una qualunque delle seguenti condizioni:

- il sotto-problema $P_i$ non ha soluzioni ammissibili
- $V_i(P_i) \leq V_s(P)$, cioè le soluzioni ammissibile di $P_i$ non sono migliori della soluzione ammissibile corrente
- $V_i(P_i) > V_s(P)$ e la soluzione ottima di $P_i$ è ammissibile per $P$. in tal caso si aggiorna $V_s(P) = V_i(P_i)$ e si chiude il nodo

## Visita

### Depth first (profondità)

- Il prossimo nodo da visitare è uno dei figli del nodo attualmente visitato (se
rimasto aperto)
- questa strategia trova rapidamente una soluzione ammissibile, occupa poca
memoria, ma non tiene conto della qualità della soluzione trovata

### Best first

- Il prossimo nodo da visitare e il più promettente, ciò è quello con il massimo
valore di $v_S$
- trova rapidamente una soluzione ammissibile, occupa molto memoria, ma
tiene conto della qualità della soluzione trovata

### Breadth first (ampiezza)

- Si esplorano prima tutti i nodi dello stesso livello
- in generale non fornisce buone prestazioni dal punto di vista computazionale

# Algoritmo

1. Genera il nodo radice $P$ (da visitare), trova una soluzione ammissibile per $P$ e
calcola una $V_I(P)$.
2. Se tutti i nodi sono stati visitati, allora STOP (la soluzione ammissibile
corrente è ottima).
3. Seleziona un nodo $P_i$ da visitare.
4. Se $P_i$ non contiene soluzioni ammissibili, allora chiudi il nodo $P_i$  e torna al
passo 2.
5. (Bound) risolvi un rilassamento di $P_i$ e calcola $V_S (P_i)$.
    - se $V_S(P_i) \leq V_I(P)$ allora chiudi il nodo $P_i$ e torna al passo 2.
    - se $V_S(Pi)  >V_I(P_i)$ e la soluzione ottima del risultato di $P_i$ è ammissibile, poni $V_i(P) = V_S(P_i)$ e torna al passo 2.
6. (Branch) Partiziona la regione ammissibile di $P_i$ in sotto-regioni e genera nuovi nodi da visitare. Torna al passo 2.

![[UniPi-Appunti/Studi/Triennale Informatica/2° Anno/Ricerca Operativa (RO)/Media/Untitled 6 1.png]]
