---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Sequenziamento Sanger
---
la **Sanger sequencing** è la **Prima generazione** di [[Tecnologie di sequenziamento|sequencing technologies]], Determine una sequenza di [[DNA Struttura e funzionalità|DNA]] sfruttando la [[Polymerase chain reaction (PCR)|PCR]]. il DNA che si vuole sequenziare chiamato **template** viene duplicato partendo da un **primer** fino a raggiungere un [[Nucleotidi|di-deoxy nucleotides (ddNTPs)]] con una base specifica. a quel punto si interrompe il processo di copiatura e si usano i frammenti di lunghezze diverse  per fare il sequenziamento.

per rendere un neclotide terminare basta sostituire nella posizione 3' il gruppo -OH con -H cosi da impedire la reazione che attacca il prossimo nucleotide.
![[IMG - PCR per la sequenzazione.png]]

per aumentare il Throughput del processo si puo attaccare ad ogni [[Nucleotidi|ddNTP]] un colore che viene emesso quando viene incorporato.  in questo modo un sensore puo leggere le lunghezze d [[Fisica- Luce|onda della luce]] e ricostruire la sequenza. 
![[IMG - color-tagging ddNTP.png]]
in piu si puo copiare una sequenza in entrambi le direzione aumentando cosi ancora di piu le sequenza disponibili per il sequenziamento 
![[IMG - sense and antisense strand sequncing.png]]
dopo le letture va fatto l [[Problema Sequence Assembly|allineamento]] da cui si puo ottenere una singola sequenza da $10^3$ [[Nucleotidi|Nucleotidi]]

