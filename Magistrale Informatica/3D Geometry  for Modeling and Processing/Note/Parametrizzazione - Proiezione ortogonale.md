---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Parametrizzazione - Proiezione ortogonale
---
per applicare die **tagli** in per una [[Parametrizzazione|prametrizzazione]] di una [[Mesh Poligonali|mesh]]  si puo sfruttare la [[Applicazione lineare - Proiezione Ortogonale|Proiezione Ortogonale]]

Un approccio pratico, sebbene empirico, consiste nell'**osservazione dell’oggetto da più punti di vista**, ad esempio da sei direzioni cardinali come quelle associate alle facce di un cubo. Per ciascun triangolo, si selezionano le regioni da cui esso è meglio visibile, ipotizzando che in queste porzioni la distorsione della parametrizzazione sia minore. La visibilità parziale da ogni direzione implica che l’intera superficie non venga coperta da un’unica proiezione, ma ciò risulta comunque utile perché consente una copertura quasi completa della superficie con distorsioni localmente contenute.
![[IMG - proiezione ortogonale di un oggetto in spazio parametrico.png]]
A questo primo metodo si può affiancare una tecnica più sistematica ispirata al **depth peeling**, un algoritmo originariamente sviluppato per il rendering corretto di superfici semitrasparenti. In questo metodo si effettuano più passate di rendering; durante ogni passata, si rimuove la "buccia" più esterna della superficie visibile da una data direzione, registrando progressivamente strati interni sempre più profondi. Questo comportamento può essere visualizzato, ad esempio, considerando un oggetto come un elefante: al primo step si ottiene la superficie esterna, al secondo l’interno, e così via, fino ad arrivare a parti che sono schermate da più strati, come la schiena nascosta dietro l’orecchio. Con un numero sufficiente di passate, ogni triangolo viene visto da almeno una direzione.
![[IMG - deepth pealing effetti elefante.png]]

Combinando questo metodo con la visibilità direzionale, è possibile costruire una mappa di proiezione per ogni triangolo della mesh, che può poi essere riassemblata per costruire una parametrizzazione globale. Questo approccio si rivela particolarmente utile nelle applicazioni di **fotogrammetria**, dove si vogliono ottenere parametrizzazioni coerenti con fotografie mappate sull’oggetto tridimensionale.
