---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - FDI
  - AIF
Area:
topic:
SubTopic:
---

# Teorema di Herbrand
---
Se $KB \models \alpha$, cioè se $\alpha$ è [[Conseguenza Logica (Deduzione)|conseguenza logica]] di una [[Sistemi di inferenza logica|base di conoscenza]] del [[Logica del primo ordine (FOL)|primo ordine]], allora **esiste una [[Inferenza logica per dimostrazione di teoremi|dimostrazione]] che coinvolge solo un sottoinsieme finito della $KB$ proposizionalizzata**. Anche se la [[Riduzione da FOL ad logica proposizionale|proposizionalizzazione]] può generare infinite istanze a causa di simboli di funzione, il teorema garantisce che solo un sottoinsieme finito è necessario per [[Inferenza logica per dimostrazione di teoremi|provare]] $\alpha$.

Per verificare se $\alpha$ è conseguenza logica, si procede **incrementalmente** generando le istanze dei termini:
1. Creare le istanze usando le **costanti** presenti nella base di conoscenza.  
2. Generare le istanze con **termini di profondità 1**, cioè applicando simboli di funzione una volta ai termini precedenti.  
3. Aumentare progressivamente la profondità di annidamento dei termini fino a ottenere una dimostrazione proposizionale di $\alpha$.


