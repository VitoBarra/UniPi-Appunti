---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# GRN - Multy-value Networks
---
**Multy-value Boolean Networks** sono una variante delle [[GRN - Boolean Networks|Boolean Networks]] per modellare [[Gene Regulatory Networks (GRN)]]in cui lo stato di un gene non è limitato ai due valori booleani $\{0,1\}$ ma può assumere **più livelli discreti di espressione**, permettendo di rappresentare in modo più realistico la concentrazione delle proteine prodotte da un gene.

In queste reti ogni **gene** $x_i$ appartiene a un dominio discreto $\mathbb{K} = \{0,1,\dots,k_1\}$$$x_i \in \mathbb{K}$$dove i valori rappresentano **livelli di espressione** (ad esempio inattivo, basso, medio, alto).

Lo stato globale della rete è quindi un vettore$$\mathbf{x}(t)=(x_1(t),x_2(t),\dots,x_n(t)) \in \mathbb{K}^n$$Le funzioni di aggiornamento non restituiscono più solo valori **booleani** ma valori nel dominio discreto del gene:$$x_i(t+1)=f_i(x_1(t),\dots,x_n(t))$$ con $f_i:\mathbb{K}^n \to \mathbb{K}$ e la semantica di aggiornamento puo essere **asincrona** o **sincrona** come per le [[GRN - Boolean Networks|boolean netwroks]] 

Le regole di aggiornamento possono essere definite tramite:
Una formulazione comune utilizza **generalized threshold rules**, in cui l’attivazione dipende da una somma pesata delle influenze degli altri geni seguita da una funzione di soglia discreta:$$x_i(t+1)=\phi_i\left(\sum_j w_{ij}x_j(t)\right)$$dove:
- $w_{ij}$ rappresenta l’influenza del gene $j$ sul gene $i$
- $\phi_i$ è una **funzione a soglia multi-livello** che mappa il segnale aggregato nel livello di espressione del gene.

Un’altra modalità per definire le funzioni di aggiornamento sono le **piecewise rules**, in cui il livello di espressione di un gene varia in funzione delle condizioni sui regolatori:
- se l’attivatore $A$ è alto e l’inibitore $B$ è basso, il livello di $x_i$ aumenta
- se $B$ è alto, il livello di $x_i$ diminuisce

Analogamente alle [[GRN - Boolean Networks|Boolean Networks]]:
- lo stato evolve tramite **aggiornamenti sincroni o asincroni**
- la dinamica converge verso **attrattori** (stati stabili o cicli)

I dati di **gene expression** sono spesso misurati come valori **continui o quasi continui**. Le multy-value networks permettono quindi una rappresentazione **coarse-grained** ma più realistica rispetto alle [[GRN - Boolean Networks|Boolean Networks]] strettamente booleane.
Gli **attrattori** delle multy-value networks possono corrispondere a:
- diversi **tipi cellulari**
- diversi **livelli di attivazione di pathway biologici**
- **fenotipi intermedi**

Le multy-value networks preservano quindi la struttura logica delle reti booleane ma permettono di rappresentare **più livelli discreti di espressione**, risultando particolarmente adatte per modellare [[Gene Regulatory Networks (GRN)|GRN]] inferite da dati quantitativi.

Dal punto di vista formale ogni variabile multi-valore $x_i \in \mathbb{K}$ può essere codificata in una [[GRN - Boolean Networks|Boolean Network]] introducendo $\lceil \log_2(k_i+1) \rceil$ variabili booleane e definendo opportune regole di aggiornamento.

Di conseguenza:
- non aumenta la classe delle funzioni rappresentabili
- una multi-valued network può sempre essere simulata da una Boolean network più grande.

Dal punto di vista della modellazione però le multy-value networks sono spesso preferibili perché:
- rappresentano direttamente i **livelli discreti di espressione**
- producono modelli **più compatti**
- risultano **più interpretabili** rispetto alla codifica booleana equivalente.