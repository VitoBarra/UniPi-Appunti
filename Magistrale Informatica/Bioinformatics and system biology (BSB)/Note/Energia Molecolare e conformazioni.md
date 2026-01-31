---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# Energia Molecolare e conformazioni
---
Un sistema [[Concetti base della chimica|chimico]], costituito da insiemi di [[Molecole|molecole]], possiede un’**energia interna**, determinata sia dalla natura delle interazioni tra le particelle sia dai loro moti.  
In particolare, l’energia interna di una molecola deriva da due contributi fondamentali:
- **Energia potenziale**, associata alle interazioni *bonding* e *non-bonding*  
- **Energia cinetica**, legata al moto termico casuale delle molecole  
Poiché la [[Geometrica Molecolare|geometria tridimensionale]] influenza direttamente tali interazioni, diverse disposizioni spaziali della stessa molecola possono corrispondere a valori energetici differenti.  
Ogni diversa disposizione ottenuta senza rottura di legami chimici, attraverso rotazioni attorno a legami singoli, è detta **conformazione** della [[Molecole|molecola]]. 
![[IMG - energia delle molecole.png]]
Le **conformazioni** più stabili, corrispondenti a un **minimo energetico** sulla superficie di energia potenziale, sono dette **conformeri**.
la trasformazione tra **conformero** ad un altro richiede che la molecola attraversi una configurazione a energia più elevata, detta **stato di transizione**, che costituisce la **barriera energetica** tra due minimi **conformazionali** ![[IMG - bariera energetica tra conformeri.png]]

I **conformeri** non sono presenti in quantità uguali: la popolazione relativa dipende dalla loro energia relativa.
- energia più bassa → più popolati  
- energia più alta → meno popolati  
All’equilibrio la distribuzione tra conformeri segue la [[Distribuzione di Boltzmann|distribuzione di Boltzmann]]: $$P_i \propto e^{-E_i/RT}, \quad \sum_i P_i = 1$$ dove $P_i$ è la popolazione del conformero $i$, $E_i$ la sua energia, $T$ la temperatura assoluta e $R$ una costante statistica. 

Nel caso di due conformeri il rapporto tra le popolazioni è: $$\frac{P_2}{P_1}=e^{-(E_2-E_1)/RT}$$ e questo porta al seguente distribuzione della popolazione
![[IMG - zoltzmann equetion for 2 conformers.png]]



## Esempi di conformazioni

### Cicloesano
Il cicloesano è un anello a sei [[Struttura Atomica|atomi]] di [[Elementi chimici|carbonio]] e costituisce uno dei casi più importanti di analisi conformazionale.  
La sua superficie energetica mostra due minimi principali:
- **Conformazione a sedia** (più stabile)  
- **Conformazione twist-boat** (meno favorevole)  
![[IMG - possibili conformanti.png]]
La differenza energetica tra i due conformeri è di circa **22.5 kJ/mol** (5.5 kcal/mol) a favore della sedia 
Applicando la distribuzione di Boltzmann:
- **Sedia**: ~99.9%  
- **Twist-boat**: ~0.1%  

![[IMG - livelli di energia conformanti.png]]

### Metilcicloesano
Nel metilcicloesano l’introduzione di un sostituente metilico produce un insieme più ricco di conformazioni accessibili.  

Sono presenti cinque conformeri principali:
- 2 conformazioni **chair**  
- 3 conformazioni **twist-boat**  
Il conformero più stabile è quello con il metile in posizione equatoriale, mentre la posizione assiale comporta un aumento energetico dovuto a interazioni steriche sfavorevoli.

| Conformer | Posizione del metile | Differenza di energia (kJ/mol) | Popolazione (%) |
| --------- | -------------------- | ------------------------------ | --------------- |
| chair     | equatoriale          | 0                              | 95.4787         |
| chair     | assiale              | 7.5                            | 4.5085          |
| boat      | bowsprit             | 22.7                           | 0.0085          |
| boat      | plane                | 24.6                           | 0.0038          |
| boat      | flagpole             | 30.0                           | 0.0004          |
|           |                      |                                |                 |

![[IMG - esempi di coformanti.png]]

Le due conformazioni a sedia rappresentano quindi quasi la totalità della popolazione complessiva, mentre le forme twist-boat risultano trascurabili all’equilibrio 
