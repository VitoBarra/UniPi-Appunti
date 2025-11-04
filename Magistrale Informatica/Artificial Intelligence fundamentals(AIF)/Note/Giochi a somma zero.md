---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Giochi a somma zero
---
i **giochi a somma zero** (più accuratamente giochi a somma costante) sono una categoria di [[Teoria dei giochi (Game theory)|giochi]] e un caso affrontabile come problemi di [[Ricerca in ambienti competitivi|Ricerca in ambienti competitivi]].
in particolare in questi tipi di giochi ci sono solo 2 **giocatori**, ovvero gli [[Agenti Razionali|agenti]], e i gioco di questa categoria si descrivono come:
- **deterministici**, ogni azione da sempre lo stesso risultato
- **a turno**, i due player non possono fare una mossa in contemporanea ma devono aspettare la mossa del avversario. 
- **a informazione perfetta**: sinonimo di ***fully observable*** e implica che entrambi i giocatori conoscano pienamente lo stato del gioco in ogni momento.
- **a somma zero**: ovvero ogni guadagno di un **giocatore** corrisponde a una **perdita** equivalente per l’altro, sono impossibili gli esiti Win-Win (comportamenti collaborativi)


#### Modello giocatori in giochi zero-sum
I 2 **giocatori** definiti come [[Struttura degli agenti razionali|agenti con utilità]] sono identificati come **MAX** e **MIN**, MAX cerca di massimizzare la sua **funzione di utilità** mentre MIN cerca di minimizzarla, la funzione di utilità è definita dal valore di **minimax**.

l'ipotesi nel modellare i giocatori in questo modo sta nel fatto che entrambi i giocatori fanno sempre scelte ottimali.
Formalmente, 
*sia*
- $s$ è uno stato 
- $A(s)$ l’insieme delle azioni disponibili, 
- $U(s)$ la funzione di utilità (del problema non degli agenti ) valuta il valore terminale di uno stato,
**allora** il valore **minimax** funzione di **utilità del agente** è definito ricorsivamente come:$$
\text{Minimax}(s) = 
\begin{cases}
U(s) & if \  IS-TERMINAL(s) \\
\max_{a \in A(s)} \text{Minimax}(\text{Result}(s, a)) & if \  TO-MOVE(S)= MAX \\
\min_{a \in A(s)} \text{Minimax}(\text{Result}(s, a)) & if\ TO-MOVE(S)= MIN
\end{cases}
$$Nella ricerca del payer **MAX** di una una sequenza di azioni che conduca alla vittoria (**soluzione ottimale**), deve considerare tutte le possibili risposte dell'avversario **MIN**. Questo richiede l’elaborazione di un **piano condizionale** che specifichi la mossa ottimale in ogni contesto generato dalle scelte dell’avversario.


Nei giochi con esito binario (vittoria o sconfitta), tale piano può essere generato mediante la [[Alberi di ricerca AND-OR|ricerca AND–OR]]. In tali contesti, la nozione di strategia vincente coincide con quella di soluzione in un problema di [[Problemi di Ricerca in spazi non deterministici|pianificazione non deterministica]]: è necessario garantire l’esito desiderato indipendentemente dalle azioni dell’avversario.

Per i giochi che presentano più esiti possibili, ciascuno associato a un punteggio (utilità), si utilizza un algoritmo più generale, noto come ricerca [[Ricerca MiniMax|minimax]]. La struttura dell’albero di gioco mostra i nodi in cui **MAX** effettua una scelta (rappresentati come nodi **MAX**) e quelli in cui agisce MIN (nodi **MIN**), i quali rispondono alle mosse dell’avversario.
