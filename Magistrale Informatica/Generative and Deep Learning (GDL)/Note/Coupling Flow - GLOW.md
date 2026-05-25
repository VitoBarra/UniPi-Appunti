---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area: Modelli Generativi
topic: Flow-based models
SubTopic:
---
# GLOW
---
Le **GLOW** estendono la linea di [[Coupling Flow - NICE]] e [[Coupling Flow - RealNVP]] mantenendo i [[Coupling Flow|coupling flow]], ma rendendo il mixing tra canali piu flessibile e piu adatto alla generazione di immagini ad alta dimensionalita.

L'idea resta quella dei [[Normalizing Flows]] classici:
- trasformazioni invertibili
- likelihood esatta
- sampling ottenuto invertendo il flow

## Blocco architetturale
Un blocco tipico di GLOW combina:
- un passo di normalizzazione attivazionale
- una convoluzione invertibile $1 \times 1$
- un affine coupling layer

La convoluzione invertibile $1 \times 1$ sostituisce in modo piu ricco le semplici permutazioni usate in molti flow precedenti. Invece di riordinare soltanto le coordinate o i canali, GLOW apprende un mixing lineare invertibile tra i canali.
![[IMG - GLOW architettura.png]]

## Perche migliora RealNVP
Le **GLOW** migliorano due limiti pratici dei coupling flow piu semplici:
- il mixing tra componenti non e fissato a mano ma appreso
- la struttura multi-scale viene integrata in un'architettura molto efficace per immagini

Per questo GLOW puo essere visto come una generalizzazione piu potente di RealNVP: la filosofia del coupling flow resta la stessa, ma l'architettura diventa piu espressiva grazie a blocchi invertibili meglio progettati.

## Spazio latente
Una volta addestrato, GLOW consente diverse operazioni interessanti nello spazio latente:
- **sampling**, campionando da una distribuzione base e invertendo il flow
- **interpolazione**, muovendosi tra due codici latenti
- **manipolazione semantica**, modificando direzioni latenti associate a caratteristiche visive

Queste proprieta mostrano bene uno dei vantaggi dei flow-based models: oltre a generare esempi, costruiscono anche una rappresentazione latente invertibile e strutturata.
![[IMG - GLOW sampling.png]]
![[IMG - GLOW interpolation.png]]
![[IMG - GLOW maniulation.png]]
