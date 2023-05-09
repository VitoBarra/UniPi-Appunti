---
type: nota
course: Calcolo Numerico
topic: 
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Tipi di Errore nel calcolo numerico
---
Analizzando un fenomeno del mondo reale se ne crea il **modello matematico continuo** questo può ci permette di rovarne le proprietà qualitative(esistenza, unicia, regolarita, ecc.)questo pero non ci permette di soluzione una soluzione concreta al problema di consequenza il modello viene aprossimato prendendo solo alcuni suoi punti quindi creando un **modello matematico  discreto**

![[Raccolta UniPi INF/Note/2° Anno/Calcolo Numerico(CN)/Media/Untitled 1.png]]

non tutti i numeri sono rapresentabili con dei valori finiti per esempio $\pi$ o $\sqrt{2}$ ma noi possimo solo calcolare con un aritmetica finita che aprossima la soluzione reale, questo introduce alcuni errori

## Errori

- _Errore di rapresentazione_: generati dall impossibilità di tenere traccia di numeri con infinite cifre
- _Errore  delle operazioni_: generati dalle operazioni su numeri finiti


### Errore Inerente
con $f(x) \not = 0$ SI dice errore inerente o inevitabile generato dal calcolo di 
$$ \epsilon_{in} = \frac{f(\tilde x) - f(x)}{f(x)}$$
-  l _errore inerente_ misura la sensibilità i della funzione e pertanto del  problema matematico considerato rispetto alla perturbazione del dato iniziale. è indipendente dal algoritmo (sequenza di operazioni aritmetiche) utilizzato per il calcolo di $f(x)$ e quindi per la risoluzione del programma matematico associato 
- a secoda del valore del _errore inerente_ si possono definire i problemi in due modi
	-  problema  _mal condizionato_. se l errore inerente è qualitativamente alto in valore assoluto (solitamente viste con i limiti dove $f$ va a 0 o $\infty$)
	- problema _ben condizionato_   l errore inerente è qualitativamente modesto in valore assoluto
il termine  “_qualitativamente_” è qui utilizzato per indicare che la valutazione è dipendente dal contesto applicativo 

### Errore Algoritmo
si diche errore algoritmico generato nel calcolo  tramite [[Aritmetica di Macchina#Operazioni di macchina |l aritmetica di macchina]] di $f(\tilde x) \not =0$ la quantita
$$\epsilon_{alg} =  \frac{g(\tilde x)-f(\tilde x)}{f(\tilde x)}$$
- la Funzione $g(x)$ dipende dal algoritmo utilizzato per calcolare $f(x)$ 
	- ad esempio per $f(x)=\frac{x^2+1}{x}$ potremmo avere  $g(x)=g_1(x)=((x \otimes x)\oplus1) \oslash x$ In generale differenti algoritmi conducono a differenti _errori algoritmici_ 
- a seconda del valore del _errore algoritmico_  si possono definire gli [[Algoritmi|algoritmi]] in  due modi 
	- Numericamente _instabili_: se l errore algoritmico è qualitativamente alto
	- Numericamente _stabili_: se _NON_ sono instabili

in generale è difficile stabilire se un algoritmo è stabile o instabile

### Errore totale
si dice errore totale generato nel calcolo di $f(x) \not = 0$ mediante l algoritmo specificato da $g$ la quantità
$$\epsilon_{tot}= \frac{g(\tilde x)-f(x)}{f(x)}$$
l errore totale misura la differenza relativa tra l output atteso e l output effettivamente calcolato. in un analisi a primo ordine vale

## Teorema
si ha $\epsilon_{tot} \dot=\epsilon_{in}+\epsilon_{alg}$ 
##### Dimostrazione
$$
\begin{align}
\epsilon_{tot}=\\\frac{g(\tilde x)-f(x)}{f(x)}=\\ \frac{g(\tilde x)-f( \tilde x)}{f(\tilde x)}\frac{f(\tilde x)}{f(x)}+ \frac{f(\tilde x)-f(x)}{f(x)}=\\
\epsilon_{alg}(1+\epsilon_{in})+\epsilon_{in} \dot =\\ \epsilon_{alg} + \epsilon_{in}
\end{align}
$$


Il teorema esprime il fatto che nel calcolo di una funzione razionale in un analisi al primo ordine le due fonti di generazione degli errori individuate recentemente forniscono contributi separati che possono essere analizzati _indipendentemente_. l obiettivo  dell analisi numerica è pertanto quelllo di individuare algoritmi numericamente stabili per problemi ben condizionati