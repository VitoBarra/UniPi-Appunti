---
Course: "[[Fondamenti Del Informatica (FDI)]]"
tags:
  - AIF
  - FDI
Area:
topic:
SubTopic:
---

# Riduzione da FOL ad logica proposizionale
---
Nel contesto della [[Logica del primo ordine (FOL)|logica del primo ordine]], la **riduzione a logica proposizionale** consiste nel trasformare una base di conoscenza $KB$ contenente **quantificatori e variabili** in un insieme di enunciati della [[logica proposizionale|logica proposizionale]], in cui tutte le variabili sono sostituite con **termini ground**. 
La trasformazione si basa sull’uso delle regole di **istanziazione**, che sostituiscono i quantificatori con termini ground utilizzando il [[FOL - Sostituzione|concetto di sostituzione]] indicato con $SUBST(\{x/h\},\alpha)$.


l'**Universal Instantiation rule**  
**Sia**  
- $g$ un **termine ground**  
- $\alpha$ un enunciato  
**Allora**  $$
\frac{\forall x\,.\,\alpha}{\text{SUBST}(\{x/g\}, \alpha)}
$$La **regola di Universal Instantiation** consente di derivare da una proposizione universale $\forall x\,.\,\alpha$ una versione specifica della formula in cui la variabile $x$ è sostituita da un termine concreto $g$. In altre parole, ciò permette di passare da un'affermazione generale su tutti gli elementi del dominio a un'affermazione specifica su un elemento particolare. Questa regola può essere applicata **più volte**, usando termini **ground diversi**.


l'**Existential Instantiation rule**  
**Sia**  
- $k$ una **costante di Skolem**  
- $\alpha$ un enunciato esistenziale $\exists x\,.\,\alpha$  
**Allora**  $$
\frac{\exists x\,.\,\alpha}{\text{SUBST}(\{x/k\}, \alpha)}
$$La **costante di Skolem** $k$ è un nuovo simbolo che rappresenta un oggetto specifico la cui esistenza è garantita dalla formula esistenziale. Essa **assegna un nome a un oggetto indefinito**, permettendo di sostituire la variabile esistenziale con un termine concreto senza alterare la correttezza logica della formula. È importante che $k$ non compaia già nella base di conoscenza, per evitare conflitti con altri oggetti.  


l'**Skolem Function rule**  
**Sia**  
- $p(x_1, \dots, x_n)$ una **funzione di Skolem**  
- $\alpha$ un enunciato $\forall x_1 \dots \forall x_n\,.\,\exists y\,.\,\alpha$  
**Allora**  
$$
\frac{\forall x_1 \dots \forall x_n\,.\,\exists y\,.\,\alpha}{\forall x_1 \dots \forall x_n\,.\,\text{SUBST}(\{y/p(x_1, \dots, x_n)\}, \alpha)}
$$

La **funzione di Skolem** $p(x_1, \dots, x_n)$ viene introdotta quando un quantificatore esistenziale si trova **nel dominio di uno o più quantificatori universali**. A differenza della costante di Skolem, qui l’oggetto esistenziale può dipendere dalle variabili universali presenti nel contesto. Gli argomenti della funzione di Skolem sono **tutte le variabili universali nel cui ambito appare il quantificatore esistenziale**, garantendo che ogni istanza della variabile universale possa avere il proprio oggetto specifico.  

In questo modo, si preserva la corretta semantica della formula originale: ogni individuo può essere associato a un oggetto diverso.




Se le costanti nella base di conoscenza sono finite, applicando le regole di istanziazione si può ottenere una $KB$ completamente in [[logica proposizionale|logica proposizionale]], poiché il numero di istanze è limitato. Tuttavia, l’introduzione di **simboli di funzione** può generare un insieme **infinito di termini ground**, poiché le funzioni possono essere applicate ricorsivamente ai propri risultati:$$
P_1(a),\ P_1(P_1(a)),\ P_1(P_1(P_1(a)))\,\dots
$$In questo caso, la proposizionalizzazione non produce un insieme finito di formule.
