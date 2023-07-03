---
type: nota
course: Calcolo Numerico
topic: 
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Tipi di Errore nel calcolo numerico
---
Analizzando un fenomeno del mondo reale se ne crea il **modello matematico continuo** questo può permetterci di trovarne le proprietà qualitative( esistenza, unica, regolarità, ecc.) ma non ci permette di trovare una soluzione concreta al problema di conseguenza il modello viene approssimato prendendo solo alcuni suoi punti creando quindi un **modello matematico discreto**

![[UniPi INF/Note/2° Anno/Calcolo Numerico(CN)/Media/Untitled 1.png]]
non tutti i numeri sono rappresentabili con dei valori finiti. ad esempio $\pi$ o $\sqrt{2}$ non sono _rappresentabili finitamente_.
posiamo solo calcolare con un aritmetica finita che approssima la soluzione reale, questo introduce alcuni errori

## Errori
- _Errore di rappresentazione_: generati dal impossibilità di tenere traccia di numeri con infinite cifre
- _Errore  delle operazioni_: generati dalle operazioni sui [[Insieme dei numeri di macchina|numeri di macchina]]


### Errore Inerente
_sia_ $f(x) \not = 0$ si dice errore _inerente o inevitabile_ la quantità
$$ \epsilon_{in} = \frac{f(\tilde x) - f(x)}{f(x)}$$
-  l _errore inerente_ misura la sensibilità i della funzione e pertanto del  problema matematico considerato rispetto alla perturbazione del dato iniziale. è indipendente dal algoritmo (sequenza di operazioni aritmetiche) utilizzato per il calcolo di $f(x)$ e quindi per la risoluzione del programma matematico associato 
- a seconda del valore del _errore inerente_ si possono classificare i problemi in due modi
	-  problema  _mal condizionato_. se l errore inerente è qualitativamente alto in valore assoluto (solitamente viste con i limiti dove $f$ va a $0$ o $\infty$)
	- problema _ben condizionato_   l errore inerente è qualitativamente modesto in valore assoluto
il termine  “_qualitativamente_” è qui utilizzato per indicare che la valutazione è dipendente dal contesto applicativo 

### Errore Algoritmo
_sia_ $f(\tilde x) \not =0$ si diche _errore algoritmico_ generato nel calcolo tramite [[Aritmetica di Macchina#Operazioni di macchina |l aritmetica di macchina]] la quantità
$$\epsilon_{alg} =  \frac{g(\tilde x)-f(\tilde x)}{f(\tilde x)}$$
- la Funzione $g(x)$ dipende dal algoritmo utilizzato per calcolare $f(x)$ 
	- ad esempio per $f(x)=\cfrac{x^2+1}{x}$ potremmo avere  $g(x)=g_1(x)=((x \otimes x)\oplus1) \oslash x$ In generale differenti algoritmi conducono a differenti _errori algoritmici_ 
- a seconda del valore del _errore algoritmico_  si possono classificare gli [[Algoritmi|algoritmi]] in  due modi 
	- Numericamente _instabili_: se l errore algoritmico è qualitativamente alto
	- Numericamente _stabili_: se _NON_ sono instabili

in generale è difficile stabilire se un algoritmo è stabile o instabile

### Errore totale
si dice _errore totale_ generato nel calcolo di $f(x) \not = 0$ mediante l algoritmo specificato da $g$ la quantità
$$\epsilon_{tot}= \frac{g(\tilde x)-f(x)}{f(x)}$$
l errore totale misura la differenza relativa tra l output atteso e l output effettivamente calcolato. in un analisi a _primo ordine_ vale
#### Teorema
si ha $\epsilon_{tot} \dot=\epsilon_{in}+\epsilon_{alg}$ 
##### Dimostrazione
Osserviamo che le definizione di errore algoritmico e inerente si possono riscrivere come 
1. $\epsilon_{in} = \cfrac{f(\tilde{x})}{f(x)}-1 \ \iff \epsilon_{in}+1 = \cfrac{f(\tilde{x})}{f(x)}$
2. $\epsilon_{alg} = \cfrac{g(\tilde{x})}{f(\tilde{x})}-1 \ \iff \epsilon_{alg}+1 = \cfrac{g(\tilde{x})}{f(\tilde{x})}$
e da qui possiamo precedere con la dimostrazione come

$$
\begin{array} {}
\epsilon_{tot} & = \\
\cfrac{g(\tilde x)-f(x)}{f(x)} & = &  \\
 \left(\cfrac{g(\tilde x)}{f(\tilde{x})}-\cfrac{f(x)}{f(\tilde{x})}\right) \cfrac{f(\tilde{x})}{f(x)} & = & \text{mol per} \cfrac{f(\tilde{x})}{f(\tilde{x})}  \\
\left(\epsilon_{alg}+1-\cfrac{1}{\epsilon_{in}+1}\right)(\epsilon_{in}+1)  & = &  \text{sostitusico} \\
\epsilon_{alg}+\epsilon_{alg}\epsilon_{in}+\epsilon_{in} +1 -1& \dot =\\
\epsilon_{alg} + \epsilon_{in}
\end{array}
$$
Il teorema esprime il fatto che nel calcolo di una funzione razionale in un analisi al primo ordine le due fonti di generazione degli errori individuate recentemente forniscono contributi separati che possono essere analizzati _indipendentemente_. l obiettivo del analisi numerica è pertanto quello di individuare algoritmi numericamente stabili per problemi ben condizionati