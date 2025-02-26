---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Reti neurali approccio costruttivo Cascade Correlation
---
l algoritmo __Cascade Correlation__ è un __approccio costruttivo__ per scegliere il numero di unita in una [[Reti Neurali (NN)|rete neurale]]. 




## Descrizione dell'algoritmo

Si parte con una rete neurale **N₀**, ovvero una rete senza unità nascoste. Si procede nel seguente modo:

1. **Addestramento di N₀**: si calcola l'errore per la rete **N₀**.
2. Se **N₀** non è in grado di risolvere il problema, si passa alla rete **N₁**.
3. In **N₁**, viene aggiunta un'unità nascosta in modo tale che la correlazione tra l'output dell'unità e l'errore residuo della rete **N₀** sia massimizzata (mediante l'addestramento dei suoi pesi).
4. Dopo l'addestramento, i pesi della nuova unità vengono congelati (non possono essere riaddestrati nei passi successivi), mentre i pesi rimanenti (strato di output) vengono riaddestrati.
5. Se la rete ottenuta **N₁** non risolve il problema, si aggiungono progressivamente nuove unità nascoste, collegate a tutti gli input e alle unità nascoste precedentemente installate.
6. Il processo continua fino a quando gli errori residui dello strato di output soddisfano un criterio di arresto specificato (ad esempio, gli errori scendono al di sotto di una soglia prestabilita).

L'algoritmo costruisce dinamicamente una rete neurale e termina quando è stato trovato un numero sufficiente di unità nascoste per risolvere il problema.
![[Schermata del 2025-02-26 22-19-07.png]]

## Definizione della Funzione di Ottimizzazione

L'algoritmo alterna:

- La minimizzazione della funzione di errore totale (LMS), ad esempio tramite un semplice addestramento con **backpropagation** dello strato di output.
- La massimizzazione della correlazione **non normalizzata**, cioè della covarianza, tra la nuova unità nascosta (candidata) e l'errore residuo.

La funzione di costo è definita come:

S=∑k∣∑p(op−meanp(op))⏟oˉ(Ep,k−meanp(Ep,k)⏟Eˉ)∣S = \sum_k \left| \sum_p \underbrace{(o_p - mean_p(o_p))}_{\bar{o}} (E_{p,k} - \underbrace{mean_p(E_{p,k})}_{\bar{E}}) \right|

dove:

- Ep,kE_{p,k} è l'errore residuo con op,ko_{p,k} allo strato di output.
- pp è un pattern di input, kk è l'unità di output.
- oo (nella formula per SS) rappresenta il candidato all'output.

### Derivazione

**Esercizio**: derivare la formula (schizzo alla lavagna)

- Suggerimenti: d∣f∣/dx=sign(f)df/dxd|f|/dx = sign(f) df/dx; assumere che le variazioni di opo_p non influenzino oˉ=meanp(op)\bar{o} = mean_p(o_p).

Risultato della derivata rispetto al peso wjw_j:

∂S∂wj=∑ksgnSk∑p(Ep,k−meanp(Ep,k))f′(netp,h)Ip,j\frac{\partial S}{\partial w_j} = \sum_k \text{sgn} S_k \sum_p (E_{p,k} - mean_p(E_{p,k})) f'(net_{p,h}) I_{p,j}

dove:

- hh è l'indice del candidato (non necessario poiché si considera un solo candidato alla volta).
- Ip,jI_{p,j} è l'input associato.

### **Aggiornamento dei Pesi**

Perché si aggiorna con +dS/dwj+ dS/dw_j?

## **Ruolo delle Unità Nascoste**

- L'obiettivo principale delle unità nascoste è ridurre l'errore residuo dell'output.
- Ogni unità risolve un sottoproblema specifico.
- Ogni unità diventa un **rilevatore di caratteristiche permanente**.

## **POOL di Unità Nascoste**

- Poiché la massimizzazione della correlazione viene ottenuta utilizzando una tecnica di **gradiente ascendente** su una superficie con diversi massimi locali, si addestra un **pool** di unità nascoste e si seleziona la migliore.
- Questo aiuta ad evitare la convergenza a **massimi locali**.

## **Algoritmi Greedy**

- Consentono di ottenere una convergenza facile.
- Possono trovare un numero minimo di unità, ma possono portare a **overfitting**, richiedendo regolarizzazione.

## **Funzione di Perdita (Loss)**

- Non necessariamente si massimizza SS.