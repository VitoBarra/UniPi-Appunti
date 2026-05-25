---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area: Modelli Generativi
topic: Flow-based models
SubTopic:
---
# Residual Flows
---
I **Residual Flows** sono una famiglia di [[Normalizing Flows]] che costruisce la trasformazione invertibile come una mappa residua:

$$y = x + g_{\theta}(x)$$

Questa forma richiama direttamente le [[ResNets]], perché il modello applica una correzione al dato invece di ridefinirlo completamente da zero.
![[IMG - ResNets.png]]

## Idea di invertibilita
Una mappa residua arbitraria non e automaticamente invertibile. Per garantire l'invertibilita si impone in genere che $g_{\theta}$ sia una contrazione o comunque sufficientemente regolare, per esempio con costante di Lipschitz minore di $1$.

In questo caso la trasformazione $$f_{\theta}(x)=x+g_{\theta}(x)$$ resta invertibile perché la perturbazione introdotta dal blocco residuo non puo deformare lo spazio in modo troppo aggressivo.
![[IMG - Contraction mappign.png]]

## Interpretazione geometrica
Dal punto di vista geometrico, i **Residual Flows** descrivono una sequenza di piccole deformazioni dello spazio. Invece di costruire una grande trasformazione discreta, il campione viene spostato attraverso molte correzioni residue successive.

Questa visione li rende concettualmente piu vicini anche alla prospettiva continua che poi riappare nei modelli di [[Score and Flow-Matching]].
![[IMG - traiettoria del cambio di variabile.png]]

## Differenza rispetto ad altre famiglie
Rispetto ai [[Coupling Flow|coupling flow]], i residual flows non lasciano esplicitamente una parte delle variabili invariata. Rispetto agli [[Autoregressive Flows]], non impongono una struttura triangolare coordinata per coordinata.

Il compromesso e diverso:
- meno struttura rigida sul singolo layer
- piu attenzione necessaria per controllare stabilita e invertibilita

Quindi i **Residual Flows** ampliano il panorama dei normalizing flows: mostrano che si puo ottenere invertibilita non solo con split strutturati o dipendenze autoregressive, ma anche con trasformazioni residue sufficientemente regolari.
