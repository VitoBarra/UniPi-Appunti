---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# GRN - inferenza - ARACNE
---
**ARACNE (Algorithm for the Reconstruction of Accurate Cellular Networks)** è un metodo per l’[[GRN - inferenza|inferenza]] delle [[Gene Regulatory Networks (GRN)|GRN]] basato su concetti di **information theory**. L’obiettivo del metodo è identificare **interazioni regolatorie dirette** tra geni a partire da dati di espressione genica.

Il metodo utilizza come misura di dipendenza tra due geni la **[[mutual information (MI)|mutual information (MI)]]** e nel contesto delle [[Gene Regulatory Networks (GRN)|GRN]]:
- $X$ e $Y$ rappresentano i livelli di espressione di due geni
- un valore elevato di $I(X;Y)$ indica una forte dipendenza statistica tra i due geni

Il primo passo dell’algoritmo consiste nel calcolare la **mutual information** per tutte le coppie di geni presenti nella **expression matrix**. Questo produce una rete completamente connessa pesata: $$G=(V,E,w)$$dove:
- $V$ è l’insieme dei geni
- $E$ contiene tutte le coppie di geni
- $w_{ij}=I(X_i;X_j)$ rappresenta la dipendenza tra i geni $i$ e $j$

Il problema principale delle reti basate su correlazione o mutual information è la presenza di **dipendenze indirette**. Ad esempio, se:$$X \rightarrow Y \rightarrow Z$$allora $X$ e $Z$ possono risultare statisticamente dipendenti anche se non esiste una regolazione diretta.

Per eliminare queste interazioni indirette ARACNE utilizza la **[[Data Processing Inequality (DPI)|Data Processing Inequality (DPI)]]**, una proprietà dell’information theory che afferma:
**se** la relazione tra le variabili segue la catena$$X \rightarrow Y \rightarrow Z$$ allora **vale che**: $$I(X;Z) \leq \min\{I(X;Y), I(Y;Z)\}$$

L’algoritmo **ARACNE** analizza quindi tutte le triplette di geni $(X,Y,Z)$ e rimuove l’arco con **mutual information** più bassa tra i tre siccome probabilmente indica una relazione indiretta.

Dopo l’applicazione della DPI la rete risultante contiene principalmente **interazioni dirette** tra geni rappresentate da un grafo indiritto siccome la **mutual information** è simmetrica.

**ARACNE** è particolarmente efficace nel ridurre i **falsi positivi** dovuti a correlazioni indirette, migliorando l’accuratezza della rete inferita rispetto ai metodi basati solo su correlazione, pero e sensibile alla qualità della stima della **mutual information**