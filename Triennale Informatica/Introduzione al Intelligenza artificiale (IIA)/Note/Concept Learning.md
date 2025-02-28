---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
  - ML
---

# Concept Learning
---
Il __Concept Learning__ è un campo del [[Machine Learning (ML)|machine learning]] dove si usa il [[Algoritmi di learning supervisionato|learning supervisionato]] per scegliere un __ipotesi__ per fare __classificazione__ di un [[Logica proposizionale|input booleano]] con $t$ o $f$  

Formalmente abbiamo un __[[Insiemi Matematici|insieme]] di dati__ di training $TR$  per la classificazione definito come coppie $(x, y(x))$ dove $x \in X$ ovvero lo lo __spazio delle istanze__ è $y(x): X \rightarrow \{t,f\}$ ovvero una [[Funzioni|funzione]] booleana.
Si ricerca un ipotesi $h \in \mathcal{H}$ con $\mathcal{H}$ lo spazio delle __funzioni booleane__ tale che $$h(x)=y(x) \ \forall x \in TR \implies h(x) = y(x) \ \forall x \in X$$
alcune terminologie sono
- Un’__ipotesi__ $h(x)$ si dice che __soddisfa__ un'istanza $x$ se restituisce il valore $1$, ovvero se $h(x) = 1$.  
- Un'ipotesi $h \in \mathcal{H}$ si dice __consistente__ con il training set $(\mathbf{x_i},y(\mathbf{x_i}))\in TR$ se $h(\mathbf{x_i})=y(\mathbf{x_i}) \forall i$ 

##### Dimensione dello spazio delle ipotesi

![[004017FB-293F-4B89-9116-D53645BD3CB0.jpeg]]
la cardinalità dello spazio delle ipotesi $\mathcal{H}$ che rappresenta le __funzione booleana__ è  $|\mathcal{H}| = 2^{|X|}= 2^{(2^{n})}$ con $n$ il numero di input.

questo numero puo essere ridotto introducendo un [[Algoritmi di Machine Learning|bias di linguaggio]] ricercando le ipotesi $h$ che sono nella  [[Forma normale congiuntiva (CNF)|forma normale congiuntiva]] la cardinalità dello spazio delle ipotesi $\mathcal{H}$ è
- con solo _letterali positivi_:  $|\mathcal{H}|= 2^n$
- includendo i letterali negati $|\mathcal{H}| = 3^n+1$
che è molto meno di $|\mathcal{H}| = 2^{2^{n}}$



### Ordine parziale dal spazio delle ipotesi 
si puo definire un [[Ordinamenti|oridnamento parziale]] sullo spazio del ipotesi delle funzioni booleane $\mathcal{H}$  questo è indicato con $\leq$ o $\geq$ è letto come __meno generale__ o __piu generale__.

l ordinamento è definito come segue:
prese $h_i, h_j \in \mathcal{H}$  due ipotesi definite sullo spazio delle instanze $X$
__allora__ $$h_i \geq h_j  \iff \forall x \in X : \ h_j(x)=t \implies h_i(x)=t$$

### Version Space  
__Version Space__ $VS_{\mathcal{H},TR}$ è il [[Insiemi Matematici|sottoinsieme]] delle __ipotesi__ $h$ che sono __consistenti__ con tutti gli esempi presenti nel training set $TR$.  

per trovare il __Version Space__ si possono analizzare tutte __ipotesi consistenti__ con una ricerca esaustiva (quindi molto costoso) elencando tutte le possibili ipotesi e eliminando quello __non consistenti__, questo algoritmo è chiamato __lista ed elimina__.
Questo pero è applicabile solo se  $\mathcal{H}$ è __finito e piccolo__ cosa non realistica.
Un modo più efficiente nello spazio di ipotesi predefinito con algoritmi più intelligenti, ad esempio l' algoritmo [[Concept learning - Candidate elimination|Candidate elimination]].  


utilizzando l __ordinamento parziale delle ipotesi__ si possono definire dei limiti del __Version Space__ che sono:  
- General Boundary __G__:  le ipotesi __più generali__ e  __consistenti__ con i dati (con poche restrizioni) 
- Specific Boundary __S__: le ipotesi __più specifiche__ (meno generali) e __consistenti__ con i dati  
abbiamo che ogni membro del ___version space___ si trova tra __G__ e __S__$$VS_{\mathcal{H},TR}= \{h\in \mathcal{H}\mid (\exists s \in S)(\exists g \in G).(s \leq h \leq g)\}$$

### Teorema: Unbiased learner  
Un __unbiased learner__ non è in grado di generalizzare su nuove istanze.  

Dimostrazione:  
Ogni istanza non osservata sarà classificata come $t$ dalla metà delle ipotesi $h \in VS$ e come $f$ dall'altra metà.  
Infatti:  
$\forall h$ __consistente__ con $TR$, $\exists h'$ __consistente__ con $TR$  e quindi  $h,h'\in VS_{\mathcal{H},TR}$ per cui vale che $h'(x_{i})\neq h(x_{i})$ con $x_i \in X \ x_i \not \in TR$ 

entrambi $h,h'$ sono ipotesi valide che danno risultati diversi e si ha che in generale ogni __istanza non osservata__ verrà classificata come $t$ da precisamente meta delle ipotesi mentre l altra meta la classificherà come $f$. 