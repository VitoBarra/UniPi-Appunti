---
Course: "[[Ingegneria Del Software (IS)]]"
topic: nota
tags:
  - IS
  - Imm2Text
---

# UML - Diagramma delle classi
---
è un diagramma di [[Unified modeling Language (UML)]] e Rappresenta la struttura delle classi 

## Sintassi 
![[IMG - UML - Diagramma delle classi 1.jpeg]]
![[IMG - UML - Diagramma delle classi 2.jpeg]]
![[IMG - UML - Diagramma delle classi 3.jpeg]]

## Sintassi delle Operazioni 
![[IMG - UML - Diagramma delle classi 4.jpeg]]
![[IMG - UML - Diagramma delle classi 5.jpeg]]


## Relazioni
![[IMG - UML - Diagramma delle classi 6.jpeg]]
![[IMG - UML - Diagramma delle classi 7.jpeg]]

![[IMG - UML - Diagramma delle classi 8.jpeg]]


## aggregazione e composizione 
![[IMG - UML - Diagramma delle classi 9.jpeg]]
![[IMG - UML - Diagramma delle classi 10.jpeg]]
![[IMG - UML - Diagramma delle classi 11.jpeg]]


## generalizazione  
![[IMG - UML - Diagramma delle classi 12.jpeg]]
![[IMG - UML - Diagramma delle classi 13.jpeg]]
![[IMG - UML - Diagramma delle classi 14.jpeg]]


## Dipendenze
![[IMG - UML - Diagramma delle classi 15.jpeg]]
![[IMG - UML - Diagramma delle classi 16.jpeg]]



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
> ![[IMG - UML - Diagramma delle classi 17.jpeg]]


