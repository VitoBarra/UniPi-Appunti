---
type: nota
course: Intelligenza Artificiale
topic: 
tags: IA
---

Prev: [[Introduzione Intelligenza Artificiale (IIA)]]

# Sistema di inferenza per FOL
---
è un [[Sistemi di deduzione (o di Inferenza)|Sistema di deduzione]] per il [[Logica del primo ordine (FOL)|calcolo della logica del primo ordine]]  utilizzato dal [[Agenti Logici - Logica del primo ordine|agenti logici con FOL]]

## Riduzione ad inferenza proposizionale
per fare inferenza si cerca di ridurrà la formula dalla logica del primo ordina alla [[Logica proposizionale|Logica proposizionale]] in modo da poter utilizzare  il [[Sistema di inferenza per PROP|Sistema di inferenza per PROP]]

#### Regola di  eliminazione del $\forall$
$$\frac{\forall x . A[x]}{A[x/g]}$$
dove g è un termine ground e $A[x/g]$ è il risultato della sostituzione di $g$ per $x$ in $A$
es: 
$$\frac{\forall x.Re(x) \land Avido(x) \implies Malvagio(x)}{Re(gio) \land Avido(gio) \implies Malvagio(gio)}$$
#### Regola di eliminazione del $\exists$
$$\begin{array}{c:c}\frac{\exists x . A[x]}{A[x/k]} &\frac{\forall x.\exists y . A[x,y]}{A[x/k,\ y/p(x)]}
\end{array}$$
dove $k$ è una nuova costante detta _costante di Skolem_  che rapresenta un elemento del domino ma non una nello specifico.

##### Skolenizazione
1. Se $\exists$ non è nel ambito di un $\forall$ si sostituisce con una _costante di skolem_  
2. altrimenti con una _Funzione di Skolem_ $p(x)$
quindi sta ha che
$$\begin{array}{c:_c}
\exists x . P_1(x,G) & P_1(K,G) \\
\forall x \exists y. P_1(x,y) & \forall x.P_1(x,p(x))
\end{array}$$
#### Problematica
- dobbiamo fare il grounding per ogni oggetto mensionato
	- questo va bene siccome le costanti sono in numero finito
- se ci sono funzioni il numero di _istanza_ cresce al infinito siccome posso sempre riapplicare quella funzione al suo risultato. 
$$P_1(a),P_1(P_1(a)),\dots$$
## Teorema di Herbard
Se $KB \models \alpha$ una [[Base di conoscenza (KB)|Base di conoscenza]] allora c è una dimostrazione che coinvolge solo un sottoinsieme finito della $KB$ proposizionalizata

quindi per capire se $\alpha$ è conseguenza logica si procede incrementalente
1. Crea le instanza con le constanti
2. Creare poi quella ad un solo livello di annidamento 
3. Aumentare progressivamente il numero  gli annidamenti
se pero $KB \not \models \alpha$ allora l algoritmo non termina, questo siccome il problema è [[Calcolabilità|semidecidibile]]



## Metodi di risoluzione per FOL

#### Assunzione
- tutte le espressioni sono in [[Forma normale congiuntiva (CNF)#Algoritmo per la trasformazione a clausole|forma a clausole]]

### Unificazione
Operazioni mediante la quale si determina se due espressivo possono essere rese identiche mediante una sostituzione di termi a variabili.

il risultato è la sostituzione che rende le due espressioni identiche dell’età _unificatore_ o FAIL se le espressioni non sono unificabili

#### Sostituzione
un si è e finito di associanzio tra variabili e termini, in cui ogni variabile compare una sola volta sulla sinistra

Sostituzione  sbagliate
- $\{x / f(x)\}$ , $x$ presente sia a sinistra che a destra _sostituzione circolare_ 
	- Il controllo di questa condizione è chiamato _occurr check_
- $\{x/g(y),y/z\}$ sostituzione non normalizzata y è sia a sinistra che a destra 
	- la sua versione _normalizzata_ è $\{x/g(z),y/z\}$


Sia $\sigma$ uan sostituzione e $A$ un espressione
- $A\sigma$ è è l istanza generata dalla _sostituzione_ 
- tutte le variabili vengono sostituite _simultaneamente_ ovvero c è un unico passo di sostituzione 


per ogni copia di espressione esistono più unificatori ma ne esiste uno che è _unico_ che è il piu _generale_ ovvero che istanza meno ed è detto _Most general unifier_ (MGU)


### Algoritmo di risoluzione 
dati due insieme di clausole $\Phi= \{\dots A \dots\}$ e $\Psi = \{\dots \lnot B \dots\}$ e $\gamma = MGU(A,B)$ l unificatore allora si ottiene
$$((\Phi \backslash \{A\})\cup(\Psi \backslash \{\lnot B\}))\gamma$$
dove $\backslash$ è la [[Insiemi|differenza insimistica]]

#### Problema dei fattori
![[49181201-D9BA-46C1-8E0C-D64D453F554B.jpeg]]

### Analisi
la deduzione per risoluzione è _corretta_
ma _non è completa_
- $\{\} \models \{P,\lnot P\}$ ma non $\{\} \vdash_{RES} \{P, \lnot P\}$
diventa completo con il [[Base di conoscenza (KB)#Teorema di refutazione |Teorema di refutazione]]

 
