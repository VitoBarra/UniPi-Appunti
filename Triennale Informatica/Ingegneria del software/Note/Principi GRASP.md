---
Course: Ingegneria del software
topic: nota
tags: IS
---

Prev: [[Ingegneria Del Software (IS)]]

# Principi GRASP
---
Principi _GRASP_:
- *G*eneral:
- *R*esponsability:
- *A*ssignment:
- *S*oftware:
- *P*atterns:

## Tipo di design
Il design di una classe può essere partizionata in due gruppi
- _Rappresentativo_: ovvero fatto pensando a cosa rappresenta l'oggetto che si sta creando
- _Comportamentale_: non rappresentano nulla nel dominio e sono fatte per la convenienza di utilizzo
	- utilizzate per mantenere alta coesione e basso

## Pure fabrication
è un tipo di [[Paradigma Object Oriented Programming (OOP)#Classi|classe]] di tipo _Comportamentale_ e serve quindi a  mantenere alta coesione e basso
- le classi che implementano il [[Design pattern - Factory|pattern factory]] sono _pure fabrication_
	-  confinare le responsabilità di creazione complesse in oggetto coesi
	- incapsulare la complessità della logica di creazione

