---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrario a permutazione di colonna
---
è un [[Cifrari storici|cifrario storico]] che secondo la [[Classificazione di cifrari|classificazione]] è un cifrario a _trasposizione_

#### Definizione
é una _generalizzazione_ del [[Cifrario a permutazione semplice|cifrario a permutazione semplice]]
questo cifrario si basa sul utilizzo di una _tabella di lavoro_ $\mathcal{T}$ ha come chiave $k= \langle c,r,\pi\rangle$ dove 
- $c=$ è il numero di colonne  di $\mathcal{T}$
- $r =$ é il numero di righe di $\mathcal{T}$
- $\pi$ è una permutazione degli interi $\{1,2,\dots,c\}$

per crittografare il messaggio si divide il messaggi in $n=\cfrac{|m|}{r\times c}$ blocchi ogni $m_{1},\dots,m_{n}$ blocco viene scritto sulla tabella di lavoro $\mathcal{T}$ in modo regolare da _sinistra verso destra_.
![[Pasted image 20230705154123.png]]
e poi si permutano le colonne secondo la _permutazione_ $\pi$ e si legge il crittogramma dal _alto verso il basso da sinistra verso destra_ .

#### spazio delle chiavi 
non ci sono vincoli sui $r$ e $c$ quindi lo spazio delle chiavi è esponenziale nella dimensione del messaggio.




