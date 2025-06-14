---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Energia Molecolare
---
Un sistema [[Concetti base della chimica|chimico]], costituito da insiemi di [[Molecole|molecole]], possiede un’**energia interna**, legata alla natura delle interazioni tra le particelle e ai loro moti. Questa energia si può suddividere in due componenti principali: 
- **Energia potenziale**: associata alle interazioni bonding e non-bonding tra le molecole.  
- **Energia cinetica**: legata ai moti casuali delle molecole.
![[IMG - energia delle molecole.png]]
Quando una molecola cambia conformazione, deve superare una configurazione ad **energia più elevata**, chiamata **stato di transizione**. Questa rappresenta la barriera energetica che separa due conformazioni diverse.

Al diminuire dell’energia di una conformazione, aumenta la popolazione relativa del corrispondente conformero all’equilibrio. In condizioni di equilibrio, la distribuzione relativa dei conformeri è determinata dalle **differenze di energia** che li separano secondo la [[Distribuzione di Boltzmann|distribuzione di Boltzmann]]:

$$P_i \propto e^{-E_i/RT}, \quad \sum_i P_i = 1$$
![[IMG - zoltzmann equetion for 2 conformers.png]]

## Esempi di conformazioni

### Cicloesano
Il cicloesano è un anello di sei [[Struttura Atomica|atomi]] di [[Elementi chimici|carbonio]]. La sua analisi conformazionale evidenzia due minimi di energia principali: la **conformazione a sedia** e quella a **twist-boat**.
![[IMG - possibili conformanti.png]]
La differenza energetica tra i due conformeri è di circa 22.5 kJ/mol (5.5 kcal/mol) a favore della sedia. Applicando la [[Distribuzione di Boltzmann|distribuzione di Boltzmann]], la popolazione relativa risulta:
- **Sedia**: ~99.9%  
- **Twist-boat**: ~0.1%

![[IMG - livelli di energia conformanti.png]]

### Metilcicloesano
Nel metilcicloesano sono presenti cinque conformazioni principali: due a sedia e tre twist-boat. Considerando come riferimento energetico il conformero a energia minima (sedia con il metile in posizione equatoriale), le differenze di energia e le popolazioni relative sono:

| Conformer | Posizione del metile | Differenza di energia (kJ/mol) | Popolazione (%) |
|-----------|--------------------|--------------------------------|----------------|
| chair     | equatoriale        | 0                              | 95.4787        |
| chair     | assiale            | 7.5                            | 4.5085         |
| boat      | bowsprit           | 22.7                           | 0.0085         |
| boat      | plane              | 24.6                           | 0.0038         |
| boat      | flagpole           | 30.0                           | 0.0004         |

![[IMG - esempi di coformanti.png]]
Le due conformazioni a sedia rappresentano quindi quasi la totalità della popolazione (~99.9%), mentre le conformazioni twist-boat sono trascurabili. Tutti i valori di popolazione sono calcolati rispetto al conformero di minima energia usando la distribuzione di Boltzmann.
