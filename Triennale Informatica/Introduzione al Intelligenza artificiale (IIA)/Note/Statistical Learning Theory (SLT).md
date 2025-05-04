---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Machine Learning (ML)]]"
topic: nota
tags:
  - IA
  - ML
---

# Statistical Learning Theory (SLT)
---
La __Statistical Learning Theory__ (__SLT__) fornisce un approccio teorico per analizzare la capacita di generalizzare di un [[Modelli di dati|modello di macchine learning]] per fare ciò  si cerca di capire come bilanciare __l'errore sui dati di training__ $R_{emp}$ con la __complessità del modello__ in modo da ridurre l [[UniPi-Appunti/Triennale Informatica/Introduzione al Intelligenza artificiale (IIA)/Note/Overfitting e Underfitting|overfitting]]
I concetti chiave includono la __VC-dimension__ e la __Minimizzazione del Rischio Strutturale (SRM)__, che offrono un quadro per selezionare modelli in modo rigoroso.


### Shattering
lo __Shattering__ descrive la capacità di una uno spazio di ipotesi $\mathcal{H}$ di rappresentare tutte le possibili __etichettature__ di un __insieme di punti__ senza errori:

formalmente sia che preso $X$ un insieme di punti a cui si possono associare label arbitrarie 
__allora__ Un'ipotesi $\mathcal{H}$ __"shattera"__ se può __rappresentare__ tutte le possibili __etichettature__ dei punti in $X$
dove per __rappresentare__ si intende che esiste una $h \in \mathcal{H}$ tale che riesca a classificare i punti di $X$ con quella particolare etichettatura senza errori.

è importante notare che la definizione non parla di ogni possibile configurazione di punti ma di ogni disposizione di label per una qualsiasi configurazione di punti, ovvero basta che esista una configurazione di punti per cui ogni disposizione di label sia correttamente separabile  

infatti un esempio è 
Assumendo che le label possibili siano solo $\{-1,1\}$ allora abbiamo che il numero di tutte le possibili [[Combinatoria|disposizioni con ripetizione]] delle label per $X$ è $2^n$ e ognuna di questa è chiamata __dicotomia__.
Prendiamo un insieme $X$ con $n=3$ __allora__ abbiamo che lo spazio delle ipotesi $h \in \mathcal{H}$ con $h(x) = sing(\mathbf{wx}+w_0)$ e $\mathbf{x} \in  \mathbb{R}^2$ ovvero un [[Modelli lineari con LMS|modello lineare]] su  $\mathbb{R}^2$ __shattera__ tre punti perchè esiste almeno una configurazione di punti per cui è possibile __realizzare__ ogni __dicotomia__
![[Schermata del 2025-02-26 16-58-57.png]]
 esistono configurazioni di $3$ punti che non sono linearmente separabili come ad esempio 3 punti [[Vettori Collineari|colineari]]
![[Schermata del 2025-02-26 17-33-57.png]]
invece $\mathcal{H}$ NON __shattera__ di  un insieme con $n=4$ perchè non esiste nessuna configurazione di punti per cui si possono __realizzare__ tutte le possibili __dicotomie__
![[Schermata del 2025-02-26 17-34-51.png]]
Infatti per $4$ punti possiamo sempre disegnare $6$ linee che li collegano tra di loro alcune di queste passeranno l una sul altra e se mettiamo la stessa classe i punti collegati da una linea che si incrocia con un altra allora i punti non saranno [[Linearmente Separabili|linearmente separabbili]]


### VC-Dimension: Complessita del Modello
La __dimensione VC__ è una __misura di complessità__ di uno spazio delle ipotesi $\mathcal{H}$. 

è definita come:
sia $\mathcal{H}$ uno spazio delle ipotesi e $X$ l insieme degli punti 
__allora__ la __VC-dimension__ di $\mathcal{H}$ è la massima cardinalità $|X| = p$ può essere __shatterata__ da $\mathcal{H}$ ovvero $$ \text{VC}(\mathcal{H}) = p \quad $$ se esiste un insieme $X$ con  $|X| = p$  __shatterato__ da $\mathcal{H}$ e non esiste un insieme $X$ con  $|X|=p+1$ __shatterato__ da $\mathcal{H}$.
>[!example]-
> Per iperpiani in $\mathbb{R}^n$, la VC-dimension è $n+1$ come visto prima una linea ($\mathbb{R}^2$) può separare fino a tre punti in tutte le configurazioni, ma non quattro.

nel caso un set $X$ di dimensione arbitraria ma finita può essere sempre __shatterato__ da $\mathcal{H}$ allora si ha che: $$VC(\mathcal{H}) = \infty$$
>[!example]-
> il [[K-Nearest Neighbor (K-NN)|k-NN]] nonostante abbia un solo parametro ha $VC(\mathcal{H}) = \infty$





### VC-Bound
si vuole di approssimare una  [[Funzioni|funzione]] sconosciuta  $f(\mathbf{x})$ usando un $TR=\{(x_\ell,d_\ell)\dots x_\ell,d_\ell\}$ e scelta una funzione di __loss__ $L$ si vuole scegliere un ipotesi $h\in \mathcal{H}$ tale che in modo da minimizzare la funzione di rischio $R$ che rappresenta l' errore __vero__ su tutti i dati definita da:$$R=\int L(d,h(\boldsymbol x))dP(\boldsymbol x,d))$$ 
 dove $P(\mathbf{x},d)$ è  la [[Distribuzione di probabilita|Distribuzione di probabilita]] di valore $d$

Per scegliere $h$ pero abbiamo solo un insieme finito  $TR$ e quindi possiamo solo minimizzare il __rischio empirico__ $R_{emp}$ (gli errori sul $TR$) allora si vuole usare $R_{emp}$ per  approssimare $R$.


Per fare ciò si definisce il __VC-bounds__ che mette in relazione l errore reale $R$ e quello empirico $R_{emp}$ definito come:$$R \leq R_{emp}+\epsilon\left (\frac{1}{l},VC,\frac{1}{\delta}\right)$$ dove 
- $\delta$ è la [[Intervalli di fiducia|confidenza]] con cui si decide che la maggiorazione regga
- $1-\delta$ è una certa [[Definizione di Probabilita|probabilità]] per cui il bound resta vero
- $\epsilon$ è una funzione detta ___VC-confidence___ 
	- cresce con il crescere di __VC-dimension__ 
	- decresce al crescere di $\ell$ (numero di dati) e $\delta$ 
-  $R_{emp}$ decresce con modelli con alto VC-dimension.

Intuizioni:
-  $\ell$ più alto (piu dati) $\rightarrow$ VC-confidence più bassa e bound più vicino a $R$
- modello troppo semplice (VC-dim bassa) $\rightarrow$ $R_{emp}$ troppo alto (__undefitting__) 
- modello complesso  (VC-Dimension alta) $\rightarrow$ basso $R_{emp}$ ma __VC-conf__ si alza il che può portare ad $R$ alto. (__overfitting__)


da questo bound possiamo dedurre che l __[[UniPi-Appunti/Triennale Informatica/Introduzione al Intelligenza artificiale (IIA)/Note/Overfitting e Underfitting|overfitting]]__ dipende sia dalla __complessità__ del modello sia dal numero dei dati utilizzati infatti abbiamo che:   ![[AD987627-2D22-47F8-B3ED-7EC8512A4295.jpeg]]
![[11752980-DCE7-4DC2-8E9B-1C39288F32A0.jpeg]]


Questa è una formulazione del __VC-bound__ è generale ma per ogni diverso $\mathcal{H}$ si può trovare un bound più specifico.  


### Structural Risk minimization (SRM)
la __Structural Risk minimization__ si concentra nel selezionare un modello che minimizzi il __VC-bound__ cercando giusto trade off tra $R_{emp}$ sul $TR$ e $\varepsilon$.


Assumendo __VC-Dimension__ finita si può definire una ordinamento tra gli spazzi degli ipotesi in modo da avere che valga $$
\begin{array}{l}
     \mathcal{H}_1 \subseteq \mathcal{H}_2 \subseteq \dots \subseteq \mathcal{H}_n \\ 
    VC(\mathcal{H}_1) \leq \dots \leq VC(\mathcal{H}_n)
\end{array}
$$
allora si puo scegliere un modello in modo da minimizzare il __vc-bound__
![[Schermata del 2025-02-26 18-51-25.png]]

![[Schermata del 2025-02-26 19-37-33.png]]


>[!note]
>nonostante i [[Modelli lineari con LMS|modelli lineare]] e [[Alberi di decisione|alberi di decisione]] siano stati formalizzati prima della SLT vedere come questi applicano entrambi i principi di questa teoria. che infatti è l astratto di quello che viene detto in questi modelli


### Considerazioni Pratiche
Nonostante i limiti teorici siano utili per comprendere i principi generali, presentano alcune limitazioni nella pratica:
- I limiti basati sulla __VC-dimnsion__ tendono a essere molto conservativi, fornendo stime pessimistiche dell'errore.
- La difficoltà di calcolare la __VC-dimnsion__ per modelli complessi può limitare l'applicazione diretta della teoria.
- La SRM è più spesso utilizzata per guidare la selezione dei modelli rispetto a calcolare stime predittive precise.