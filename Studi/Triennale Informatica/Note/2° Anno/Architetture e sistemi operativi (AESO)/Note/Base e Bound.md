---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Base e Bound
---
Questa realizzazione di[[ Memoria Virtuale]] si basa sul utilizzo di due registri sul processore che indicano l inizio e la fine dello spazio di indirizzamento di un processo. Il sistema operativo può controllare che le operazioni eseguite da un processo tocchino solo la sua memoria

![[Astrazione_Kernel_3.png]]

## Traduzione indirizzi

tradurre gli indirizzi comporta una semplice adizione di base + indirizzo virtuale rendendo quindi la traduzione molto semplice

![[Untitled 41.png]]

### Vantaggi

- semplice da realizzare
- poco overhead

### Problematiche

- **Difficile espandere l Heap e lo Stack**: i due indirizzi sono fissi quindi non è possibile espandere le due regioni di memoria
- **Condividere memoria tra processi**: non si può condividere memoria siccome la memoria del processo deve essere continua
- **Frammentazione di memoria**: con l andare avanti del tempo i programmi iniziano a lasciare dei “buchi” nella memoria e con questo metodo non si possono creare blocchi discontinui di conseguenza potrebbe succedere che nonostante ci sia abbastanza memoria in totale non c è ne sia abbastanza contigua
- **supporto protezione memoria**: per quanto supporti la protezione degli indirizzi fuori dal suo spazio di indirizzamento non supporta un protezione fine-grane ma solo del intero blocco di memoria di conseguenza può scrivere liberamente nel suo blocco codice
