---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Network science - Modelli generativi delle reti
---
I **modelli generativi** cercano di spiegare come emerge la topologia delle reti reali.

### Erdős–Rényi model
Meccanismo: ogni possibile arco viene creato con probabilità $p$ indipendente.

Topologia risultante:

- distribuzione di grado **Poisson**
- rete omogenea senza hub.

Serve principalmente come **null model**.

### Barabási–Albert model
Meccanismo:

- crescita della rete
- **preferential attachment**

I nodi con molte connessioni hanno maggiore probabilità di riceverne di nuove.

Topologia risultante:

- distribuzione **power law**
- presenza di **hub**.

### Duplication–Divergence model
Modello evolutivo ispirato alla **duplicazione genica**:

1. duplicazione di un nodo
2. divergenza delle connessioni tramite mutazioni.

Produce reti:

- **scale-free**
- **small-world**

ed è particolarmente rilevante per le **reti biologiche**.