---
Course: "[[Ingegneria Del Software (IS)]]"
topic: nota
tags:
  - IS
  - Imm2Text
---

# UML - Diagramma delle classi
---
è un diagramma di [[UML]] e Rappresenta la struttura delle classi 

## Sintassi 
![[9E99135D-5513-4D23-9BF2-FC87675BE7E2.jpeg]]
![[C10DE9E4-8C41-46A6-B1E2-25C5EA3B6EF5.jpeg]]
![[AEBA6FB3-D619-4BB3-8C37-633330D819F5.jpeg]]

## Sintassi delle Operazioni 
![[63DFE8CD-1959-44E2-AE98-AF3233012061.jpeg]]
![[DFA40DB6-CF68-4415-B215-1B8EDC858270.jpeg]]


## Relazioni
![[1F50141A-375E-4CDA-A460-3DE7EA46E07B.jpeg]]
![[8E97BBB7-8CE2-4BE6-B6D5-7929B319DDEA.jpeg]]

![[E5D3E275-7A6B-40BB-AD42-55485C89D8E3.jpeg]]


## aggregazione e composizione 
![[8A0F3E7A-C753-409A-8AB7-56CB2DB4B993.jpeg]]
![[0B90A5CF-D33B-45A1-AC33-43F5F04D606E.jpeg]]
![[41CA9D1F-527B-4D46-89B1-EC3B625F3BA1.jpeg]]


## generalizazione  
![[E4C67C34-C8DE-44EA-993F-E0394072FD80.jpeg]]
![[903BC481-34C3-46B5-BE10-3643EAE0BEEC.jpeg]]
![[BCB5ED0A-0A56-4DF3-8CCC-2A3CFD4EB678.jpeg]]


## Dipendenze
![[EDB36BDC-6309-4E6A-BE47-AD0354E747F8.jpeg]]
![[995B8FA6-ABBE-4E21-B7C3-AB9EF136545B.jpeg]]



## Classi di analisi 
#### buone caratteristiche
- astrazione di uno specifico elemento del dominio
- hanno un numero ridotto di responsabilità (funzonalita)
- evitare di definire classi onnipotenti
	- attenzione quando si chiamano “sistema”,”controllore”
- Evitare funzioni travestite da classi
- evitare gerarchie di ereditarietà profonde (>=3)
#### livello di astrazine/dettaglio
- Operazioni e attributi solo quando veramente utili.
- limitare la specifica di tipi,valori,e t.
- non inventare mai niente rispetto a quanto scritto nel documento. confrontarsi con il committente prima.

#### Tecniche per l identificazione
1. _Data Driven_: tipico della fase i di analisi, si indentficano tutti i dati del sistema e si dividono in classi
2. _Responsability driven_: soprattutto durante la fase di progettazione. si indentificano le responsabilità e si dividono in classi.


> [!note] Confronto con Database
> ![[F5F2B0CF-D794-4525-AFAC-F41B0455FCFC.jpeg]]


