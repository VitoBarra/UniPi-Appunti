---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
Area:
topic:
SubTopic:
---

# Indipendenza condizionata
---
La nozione di **indipendenza condizionata** costituisce un’estensione del concetto di [[Indipendenza Stocastica]] e si definisce rispetto a una variabile aggiuntiva che funge da condizione.  
**siano**  
- $X$, $Y$ e $Z$ tre [[Variabili Aleatorie (Casuali)|variabili aleatorie]]  
**allora** si dice che $X$ e $Y$ sono **condizionatamente indipendenti** [[Probabilita condizionata|dato]] $Z$ se si ha che:$$
P(X,Y \mid Z) = P(X \mid Z)\, P(Y \mid Z)
$$Questa relazione esprime che, una volta nota l’informazione contenuta in $Z$, la conoscenza di $X$ non influisce sulla probabilità di $Y$ e viceversa. In modo equivalente, l’**indipendenza condizionata** può essere espressa anche nelle seguenti forme:$$
P(X \mid Y, Z) = P(X \mid Z) \quad \quad \quad
P(Y \mid X, Z) = P(Y \mid Z)
$$Queste formulazioni equivalenti ribadiscono che, una volta fissata la condizione $Z$, la conoscenza di una delle due variabili non modifica la distribuzione condizionata dell’altra.
