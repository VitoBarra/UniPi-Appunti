---
Course: "[[Parallel and Distributed System - Model and Paradigms (SMP)]]"
tags:
  - "#SMP"
Area: 
topic: 
SubTopic:
---
# Parallel Computing Concetti generali
---
__Parallel computing__ is the practice of using multiple processors in parallel to solve
problems more quickly than with a single processor.

It implies the capability of:
- identifying and exposing parallelism in algorithms and software systems
- Finding parts of a problem that can run at the same time
- Finding dependencies between different parts
- understanding the costs, benefits, and limitations of a chosen parallel approach
- Communication overhead
- Scalability and resource usage


### Parallel machines (examples):
- Compute Cluster: multiple independent computers
connected with one or more high-speed networks
(Gigabit Ethernet, Infiniband, Omnipath, …)
- Beowulf compute cluster made by «inexpensive» PCs
connected to a small LAN usually Linux-based
- SMP (Symmetric Multi-Processor): multiple
processor chips connected to a shared memory
hierarchy
- CMP (Chip Multi-Processor aka Multicore):
multiple compute units (called cores) packed on a
single chip





# 📌 Uso dell'esplicito parallelismo per ridurre il consumo energetico

## 📌 Formule chiave
**Potenza dinamica**:  $$Power_{dynamic} \approx \frac{1}{2} \cdot C \cdot V^2 \cdot F$$
 **Prestazioni**:  $Perf = N_{cores} \cdot F$

## 📌 Definizioni
- **V** = Tensione  
- **C** = Capacità  
- **F** = Frequenza di clock  

## 📌 Osservazioni
- Poiché $V \approx F$, si ha:  
  $$ Power_{dynamic} \approx C \cdot F^3$$
- Se raddoppiamo \( N_{cores} \), raddoppiamo anche le prestazioni \( Perf \) ma aumentiamo il consumo energetico.
- Se raddoppiamo $N_{cores}$ e dimezziamo sia $V$ che $F$, manteniamo le stesse prestazioni $Perf$ ma **riduciamo la potenza di un fattore 4**:

  $$  2 \cdot \frac{1}{2} \cdot C \cdot \left(\frac{V}{2}\right)^2 \cdot \left(\frac{F}{2}\right) = \frac{Power_{dynamic}}{4}$$

🔹 **Conclusione**: L'uso del parallelismo permette di ridurre il consumo energetico senza compromettere le prestazioni.  


# 📌 Il problema della scalabilità e le tendenze dei processori CMP

## 📌 Il problema della densità di potenza e la fine del clock scaling

Patrick Gelsinger e la previsione sul consumo energetico
> **"Business as usual will not work in the future"**  
> *(Intel VP Patrick Gelsinger, primi anni 2000)*  

Gelsinger avvertì che, se la scalabilità della frequenza di clock fosse continuata senza cambiamenti, si sarebbero raggiunti livelli di **densità di potenza estremi**:
- **2005**: Densità di potenza simile a un reattore nucleare ☢️  
- **2010**: Densità di potenza pari a un ugello di razzo 🚀  
- **2015**: Densità di potenza paragonabile alla superficie del Sole ☀️  

🔹 **Problema chiave**: Continuare ad aumentare la frequenza porta a un consumo energetico insostenibile.


![[IMG - Pawer Density.png]]
---

## 📌 La transizione ai processori multicore (CMPs)

Con l'aumento della densità di potenza, i produttori hanno dovuto **cambiare strategia**, portando a:
- **Integrazione di più core su un singolo chip**  
- **Stop dell'incremento della frequenza di clock**  
- **Validità della Legge di Moore considerando il numero di core**  
- **Aumento delle unità cache integrate**  
- **Rallentamento delle prestazioni per singolo thread**  

### 🔹 Fine dell'era del "Free Lunch"

🔹 **Conclusione**: Il miglioramento delle prestazioni ora deriva dal parallelismo (più core) piuttosto che dall'aumento della frequenza.

![[IMG - Processor Tread.png]]
