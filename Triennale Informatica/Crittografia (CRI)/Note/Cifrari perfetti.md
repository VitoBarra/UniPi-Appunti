---
Course: Crittografia
topic: nota
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrari perfetti
---
un _cifrario perfetto_ è un _cifrario_ che ad passaggio di un crittogramma $c$ il crittoanalista non deve riuscire ad ottenere nessuno informazioni in piu sul messaggio $m$ rispetto a quelle che gia possiede. 

Questo tipo di cifrario per quanto abbia una _segretezza_ perfetta è in pratico e si usa solo in situazioni particolari 

#### Formalizzazione
per dare una formalizzazione del _cifrario perfetto_ bisogna formalizzare il concetto di trasmissione crittografica come un modello matematico [[Statistica (STAT)|stocastico]], formalizzando cos è l informazione e la trasmissione.


la comunicazione tra un mittente $mit$ e un destinatario $dest$ è descritto tramite una [[Definizione di Probabilità|variabili aleatore]] $M$ che ha valori nello _spazio dei messaggi_ $Msg$ e le comunicazione sul canale sono descritti da una variabile aleatoria $C$ che assume valori nello spazio e dei _crittogrammi_ $Cri$  
##### Definizione
Sotto l assunzione che il _crittoanalista_  
- Intercetti sempre $c$
- Sappia la [[Distribuzione di probabilità|Distribuzione di probabilità]] dei messaggi $m$ di $Mit$
- Conosca lo _spazio delle chiavi_ $K$
- Conosca il _cifrario utilizzato_

_sia_
- $\mathcal{P}(M=m)$ la [[Definizione di Probabilità|probabilità]] che $mit$ mandi il messaggio $m$
- $\mathcal{P}(M=m|C=c)$ la _[[Definizione di Probabilità|probabilità]] a posteriori_ che il messaggio inviato sia effettivamente $m$ dato che $c$ è il crittogramma in transito.


un cifrario è detto _perfetto_ se $\forall m \in Msg$ e $\forall c \ \in Cri$ vale che $$\mathcal{P}(M=m|C=c) = \mathcal{P}(M=m)$$
con questa equazione stiamo di fatto dicendo l aver intercettato un crittogramma non ha fornito nuove informazioni siccome la probabilità di trasmissione  di un dato messaggio non è cambiata. 

_NON_ fosse cosi e prendendo gli esempi estremi avremmo che 
_dato_ $\mathcal{P}(M=m)=p \ \ \ 0 <p<1$ 
_se_ abbiamo che $\mathcal{P}(M=m|C=c) = 0$ o $\mathcal{P}(M=m|C=c) = 1$
_allora_ il critto analista è riuscito a capire
1. _nel primo_ caso che il messaggi non è per nulla associato al quel crittogramma.
2. _nel secondo_ caso che quel crittogramma è associato esattamente a quel messaggio
3. nei casi intermedi ho che comunque il crittoanalista ha raffinato la sua conoscenza.
in tutti e tre i casi ho che $\mathcal{P}(M=m|C=c) \not= \mathcal{P}(M=m)$ e il critto analista ha nuove informazioni
l'unico modo per evitarlo è avere che$$\mathcal{P}(M=m|C=c) = \mathcal{P}(M=m)$$

### Teorema di shannon
_Sia_ 
- $N_{k}$ il numero delle _chiavi possibili_, ovvero $N_{k}=|K|$ 
- $N_{m}$  il numero dei _messaggi possibili_, ovvero i messaggi tali che $\mathcal{P}(M=m)>0$ 
_Se_ $N_{k}\geq N_{m}$
_Allora_ il cifrario è un _cifrario perfetto_ 

#### Dimostrazione
[[Tipi di dimostrazione|dimostriamo per assurdo]] ponendo $N_m>N_k$

notiamo che ad un crittogramma $c$ con $\mathcal{P}(C=c)>0$ corrispondono $s \leq N_{k}$ messaggi non necessariamente distinti tra loro ottenuti decriptando con tutte le _chiavi possibili_
essendo vero _per ipotesi_ che $N_{m}>N_{k} \geq s$ abbiamo che esiste almeno un messaggio $m$ non raggiungibile da $c$ il che significa che $P(M=m|C=c) = 0 \not =P(M=m)$ il che rende il cifrario _non perfetto_ sotto ipotesi che $M_{m}>M_{k}$
![[Pasted image 20230706150740.png]]






