---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrario a permutazione semplice
---
è un [[Cifrari storici|cifrario storico]] e scodo la [[Classificazione di cifrari|classificazione]] è un cifrario a _trasposizione_ 


#### Definizione
l idea di base si basa sulla permutazione de messaggio e  quindi 
fissato un intero $h$ si ha che la permutazione $\pi=\{1,2,\dots,h\}$ fa da chiave per il cifrario 

la cifratura avviene dividendo il messaggio in $n=\frac{|m|}{h}$ blocchi se la _lunghezza_ del messaggio $m$ non é [[Divisibilità tra numeri|divisibile]] per $h$ si aggiungono lettere a caso per raggiungere il prossimo multiplo di $h$, questa aggiunta è chiamato _padding_ 
![[Pasted image 20230705142601.png]]
#### Dimensione della chiave
questo cifrario ha tante chiavi quanto le permutazioni possibili di $h$ elementi quindi lo spazio delle chiave è $|K| = h!-1$ dove il -1 è per evitare la permutazione identica.
