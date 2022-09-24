# Macchine a stati finiti

Le macchine a stati finiti costituiscono un metodo sistematico di progettazione delle reti sequenziali sincrone e sono caratterizata dalla posibilita di salvare $2^k$ stati con $k$ registri che riscevono lo stesso segnali di clock.

una macchia a stgati finit (FSM) è composta da un [[Registro]] che immagazzina lo stato e due blochi di logica combinatoria, logica di stato prossimo e logica d’uscita,

possono essere di due tipo

### Machina di  Moore

macchine alla Moore, le uscite dipendono esclusivamente dallo stato presente della macchina

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Untitled 21.png]]

### Machina di  Mealy

macchine alla Mealy le uscite dipendono sia dallo stato presente della macchina sia
dagli ingressi attuali.

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Untitled 1 8.png]]

## Codifica

i $k$ stati delle macchine a stati possono essere codificati con $log_2k$ bit di stato oppure utilizando 1 solo bit per strato.

| log | 1 bit |
| --- | --- |
| 01 | 001 |
| 10 | 010 |
| 11 | 100 |

utilizare il sistema a 1 bit potrebbe rendere la macchina piu semplice e quindi richidere meno hardwere ma questo dipende dalla specifica FSM che si vuole realizare

---

Status : #NotSet

Tag: [Aeso](../Architetture%20e%20sistemi%20operativi%20(AESO)%201e0e264228a748feabc5de07d5a770db.md)
