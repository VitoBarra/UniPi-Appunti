---
Subject: "[[Computer Grafica (CG)]]"
Area: 
topic: 
SubTopic: 
tags:
  - CG
---

# Rasterizazione VS Ray Tracing
---
il confronto tra il [[Ray Tracing|ray tracing]] e la [[Pipeline di Rasterizazione|rasterizzazione]] per determinare quale è il _[[Algoritmi di renderizzazione|paradigma di rendering]]_ migliore è un dibattito acceso, come al solito la risposta è _dipende_

**Ray Tracing**:
- Il _ray tracing_ prende in considerazione gli effetti _globali dell'illuminazione_ in modo _naturale_, inclusi trasparenze, ombre e rifrazioni
- Può utilizzare qualsiasi rappresentazione di superfici se si puo fare il _test di intersezione_
- È _relativamente_ semplice da implementare, ma può essere difficile da _ottimizzare_.

**Rasterizzazione**:
- La _rasterizzazione_ ha tempi di rendering più prevedibili, poiché elabora ogni poligono in modo _indipendente_.
- gestisce l'_[[Aliasing e Anti-Aliasing|antialiasing]]_ in modo naturale.
- Storicamente, l'hardware grafico è stato sviluppato per la _rasterizzazione_, ma l'hardware moderno è più versatile e può essere utilizzato per qualsiasi calcolo parallelo e quindi  anche per il _ray tracing_ 