---
type: nota
course: Data Base
topic: 
tags:
  - DB
Parent MOC: "[[Data Base (DB)]]"
---

# Schemi relazionali - Dipendenze funzionali
---
Le _dipendenze funzionali_ sono una _formalizzazione_ del concetto di vincolo dei dati su un altro dato.
questo _formalismo_ è necessario per analizzare la qualità di un [[Introduzione ai Data Base|Database]] e per poterlo trasformare in [[Normalizzazione di schemi relazionali|forma normale]]  

#### Dipendenza funzionale (Definizione)
_Sia_ 
- una _[[Modello dati - Modello Relazionale|schema di relazione]]_ $R(T)$
- $r$ un instanza valida di $R(T)$ 
- $X$ e $Y$ sottoinsiemi di attributi di $T$ 
_allora_ una _dipendenza funzionale_ è un [[Aspetti della modellazione della conoscenza#Conoscenza concreta|vincolo di integrita]] sulle istanze della relazione tale che$$ 
\begin{array}{}
X \rightarrow Y  & \iff &  \forall t_{1},t_{2} \in  r,t_{1}[X]=t_{2}[X] \\
 & \implies &  t_{1}[Y]=t_{2}[Y] 
\end{array}
$$ 
una _dipendenza funzionale_ $X \rightarrow Y$  specifica che, per ogni _istanza valida_ $r$ di $R(T)$, $\pi_{XY}(r)$ è una [[Funzioni|funzione]] con _dominio_ $X$ e codominio $Y$.

 in una _dipendenza funzionale_ $X \rightarrow Y$, si dice che 
 -  $X$ determina $Y$,
-  $Y$ è _determinato_ da $X$. 

_Sia_  $F$  un _insieme di dipendenze funzionali_ su $R(T)$, 
_allora_  $r$ è un’_istanza valida_ di $R(T)$, _rispetto_ ad $F$, 
_se_ per ogni $X \rightarrow Y \in F$  è rispettata _definizione di dipendenza funziona_

le _dipendenze funzionali_: 
- _sono definite solo_ all’interno di uno _schema di relazione_, non possono esistere fra attributi appartenenti a _relazioni diverse_
- sono proprietà _intensionali_, legate al _significato dei fatti_ che si rappresentano; non è quindi possibile _inferirle_ dall’osservazione di alcune istanze della relazione. 



> [!note]
> Le _dipendenze funzionali_ sono uno strumento per la verifica della validità della base di dati e per la sua [[Normalizzazione di schemi relazionali|normalizazione]].
>  Sono cosi importanti che i schemi relazionali sono Indicato con $R\langle T,F\rangle$ dove $F$ è una insieme di _dipendenza funzionali_ su $T$