---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---

# Sistema di inferenza per PROP
---
è un [[Sistemi di deduzione (o di Inferenza)|Sistema di deduzione]] per il [[Calcolo proposizionale (PROP)|Calcolo Proposizionale]]  utilizzato dal [[Agenti Logici - Calcolo proposizionale|agenti logici con calcolo proposizionale]]
#### Assunzioni
- tutte le espressioni sono in [[Forma normale congiuntiva (CNF)|forma a clausole]] 
#### Regole
- _Regola di risoluzione_
- $$\frac{\{I_1,\dots,I_i,\dots,I_k\} \ \ \ \{m_1,\dots,m_j,\dots, m_n\}}{\{I_1,\dots,I_{i-1},I_{i+1}\dots,I_k,m_1,\dots,m_{j-1},m_{j+1},\dots, m_n\}}$$
- con $I_i$ e $m_j$ lo _stesso letterale_ ma di segno _opposto_
	- In questo caso si può scrivere un unica clausola con i due simboli rimossi
- es :$$\frac{(P\lor Q) \land (\lnot P \lor R)}{(Q \lor R)} \ \ \ \ \ \ \frac{\{P, Q\} \ \ \  \{\lnot P , R\}}{\{Q , R\}}$$
- caso particolare (_Contradizione_):$$\frac{\{P\} \ \ \  \{\lnot P \}}{\{\}}$$
  > [!warning]- un passo alla volta
> è importate fare un passo alla volta altrimenti si potrebbero trovare delle formule non piu conseguenza logica 
> $$\frac{\{P,Q\} \ \ \  \{\lnot P , \lnot Q\}}{\{\}}$$ 
> questo darebbero una contradizione  ma è un errore 
> la risoluzione corretta sarebbe
> $$\frac{\{P,Q\} \ \ \  \{\lnot P , \lnot Q\}}{\{P,\lnot P\}} \ \ \ \ \ \frac{\{P,Q\} \ \ \  \{\lnot P , \lnot Q\}}{\{Q,\lnot Q\}} $$
>  che sono due tautologie possibili


### Teorema di risoluzione
$KB$ è insodisfacibiele $KB \vdash_{res} \{\}$

### Completezza
_non sempre_
dobbiamo dimostrare che $KB \models \alpha$ allora $KB \vdash_{res}\alpha$, ma questo non è vero, è facile trovare il seguenti contro esempio
$KB \models \{A,\lnot A\}$ ma non è vero che $KB \vdash_{res} \{A,\lnot A\}$

### Completezza per insidisfacibilita
utilizzando il ![[Base di conoscenza (KB)#Teorema di refutazione|Teorema di refutazione]] possiamo dire che  la risoluzione è completa per insidisfacibilita
#### Dimostrazione
vediamo cosa succede utilizzando il contro esempio. quindi abbiamo 
$KB \cup FC(\lnot(\lnot A \lor A))$, per dimostrare la completezza dobbiamo fare vedere che questo è insodisfacibile. ma questo è vero perché abbiamo che 
$KB \cup \{A\} \cup \{\lnot A\} \vdash_{res} \{\}$ in un solo passo.


