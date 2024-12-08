---
Course: "[[Programmazione e Algoritmica (PEA)]]"
tags:
  - PEA
topic: Strutture Dati
---
# Struttura dati - Lista linkata
---
La **lista linkata** è una [[Strutture Dati|Strutture Dati]] utilizzata per rappresentare una sequenza di elementi in modo dinamico. È composta da nodi, dove ciascun nodo contiene un valore (detto **dato** o **valore**) e un puntatore al nodo successivo nella sequenza.

## **Tipologie di Liste Linkate**

### 1. **Lista Singolarmente Linkata (Singly Linked List)**  
Ogni nodo punta solo al nodo successivo. È unidirezionale.  

**Struttura di un nodo**:  Nodo: | Dato | Puntatore al Successivo |

- **Pro**: Utilizzo efficiente della memoria, semplice da implementare.  
- **Contro**: Accesso ai dati non sequenziale e difficile da scorrere al contrario.

---

### 2. **Lista Doppiamente Linkata (Doubly Linked List)**  
Ogni nodo ha due puntatori: uno al nodo successivo e uno al nodo precedente.  

**Struttura di un nodo**:  Nodo: | Puntatore al Precedente | Dato | Puntatore al Successivo |

- **Pro**: Permette di scorrere avanti e indietro, maggiore flessibilità.  
- **Contro**: Occupa più memoria per via del doppio puntatore.

---

### 3. **Lista Circolare**
- Può essere singolarmente o doppiamente linkata.  
- L'ultimo nodo punta al primo (lista circolare singola) o è collegato al primo in entrambi i sensi (lista circolare doppia).

---

## **Operazioni Principali**
1. **Inserimento**
   - In testa
   - In coda
   - In posizione specifica

2. **Cancellazione**
   - Del primo elemento
   - Dell'ultimo elemento
   - Di un elemento in posizione specifica

3. **Ricerca**
   - Sequenziale per trovare un valore specifico.

4. **Aggiornamento**
   - Modifica del dato di un nodo specifico.

---

## **Vantaggi**
- Allocazione dinamica della memoria: nessun limite fisso sulla dimensione.
- Efficiente per l'inserimento e la cancellazione di elementi.

## **Svantaggi**
- Accesso ai dati non sequenziale (tempo O(n) per cercare un elemento).
- Maggiore utilizzo di memoria rispetto agli array per via dei puntatori.



