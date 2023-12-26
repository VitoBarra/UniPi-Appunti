---
type: nota
course: Elementi di calcolabilita e complessita
topic: 
tags: ECC
---

Prev: [[Elementi di Complessità e Calcolabilità (ECC)]]

# Macchina di Turing
---
## Definizione
la macchina di Turing è un modello di calcolo ed è definita dalla quadrupla è una [[Automa a stati finiti|macchina a stati]]

$$M=(Q,\Sigma,\delta,q_0)$$

- $Q(\ni q_i)$ è l’insieme finito degli stati, con $h \not\in Q$ 
	- con lo stato speciale h indicheremo il caso di un arresto “corretto” di un calcolo di M 
- $\Sigma$ è l’insieme finito dei simboli (alfabeto) 
	- con $\#,\rhd \in \Sigma$ carattere bianco e marca di inizio stringa 
	- $L, R, − \not\in \Sigma$ 
- $q_0 \in Q$ è lo stato iniziale 
- $\delta \subseteq (Q \times \Sigma) \times (Q \cup \{h\}) \times \Sigma \times \{L, R, -\}$ è la relazione di transizione, tale che
$$(q, \rhd, q′ , \sigma, D) \in \delta \implies \sigma  = \ \rhd, D = R$$
detto a parole significa che se si è nello stato iniziale $\rhd$ si può spastare il cursore solo a destra.



La relazione $\delta$  si può restringere e farla diventare una funzione dove i parametri sono i primi 2 elementi della quintupla. questo rende _Deterministica_ la macchina di Turing. si può scrivere quindi 
$$\delta(q,\sigma) =(q',\sigma',D')$$
questa è una notazione più intuitiva per indicare il passaggio da uno stato $q$ che ha simbolo $\sigma'$ ad un altro stato $q'$ con simbolo $\sigma'$ con l operazione $D \in \{L,R,-\}$

![[Pasted image 20221011231009.png]]
La macchina di Turing come idea passa da usare una pila di fogli illimitata  per rappresentare le istruzioni, da li si passa ad usare un foglio illimitato orizzontalmente e verticalmente foglio mappando le caselle del foglio con gli indici $(i,j)$ . Successivamente si passa a una striscia di istruzioni

>[!info]
> questa macchina di Turing semplice è espressiva come tutte le altre varianti. 



## Computazione
una computazione della macchina di Turing è una sequenza di configurazioni ognuna ottenuta dalla precedente in accordo con la definizione della funzione di transizione $\sigma$


una configurazione $\mathcal{C}$ è definita come una quadrupla 
$$(q, u, \sigma, v) \in (Q \cup \{h\}) \times \Sigma^* \times \Sigma \times \Sigma^F$$
dove
- $q$ è lo stato corrente
- $u$ è la stringa di caratteri a sinistra del simbolo corrente σ 
	- questa può essere vuota $(\epsilon)$ solo se $\sigma =\ \rhd$
- $\sigma$ è il carattere corrente
- $v$ è la stringa di caratteri a destra del simbolo corrente σ
	- $\Sigma^F=\Sigma^* \cdot (\Sigma \backslash\{\#\}) \cup \{\epsilon\}$ ovvero le stringhe con tutti i simboli a destra del ultimo $\sigma \not= \#$ rimossi

uno semplificazione di questa natazione sarà 
$$(q,u\sigma v)$$
una computazione e

$$
(q_0,w) \rightarrow^*(q',w')
$$

Dove $\rightarrow^*$ e la chiusi a riflessiva e transitiva di $\rightarrow$
se la computazione impiega $n$ passi si può scrivere
$$
(q_0,w) \rightarrow^n(q',w')
$$

^f06de7

Le computazioni :
- _Termina_ se la computazione converge ($\downarrow$) ad una $w$ se $q'=h$ dopo un numero arbitrario di passi finiti
- _**NON** termina_ se la computazione diverge ($\uparrow$) ovvero posso sempre fare un altro passo e quindi vale sempre $q' \not=  h$
- _Stallano_ se non sappiamo eseguire il passo se  $\delta$ non è totale ci si potrebbe trovare in una configurazione in cui non esiste un modo per andare avanti

> [!note] 
>le computazioni della macchina di Turing sono una logica cieca ma possiamo dare un significato a queste operazioni associando per esempio ai valori del alfabeto un significato, ad esempio un  alfabeto   $\Sigma = \{I,II,III\}$ possiamo dargli un senso di 1,2,3 e usando le transizioni possiamo utilizzarlo per sommare dei numero. Ovviamente e estendibile a qualsiasi simbolo e significato.

## Rispeseti l intuizione di algoritmo
la macchina di Turing soddisfa le ipotesi della definizione di [[Nozione di Calcolabilità|un algoritmo]]

1. ) $\delta$ basandosi si un alfabeto finito $\Sigma$ e un numero di stati finiti $Q$ non può essere un insieme infitto quindi è verificato
2. verificato per stessa ragione sopra
3. ogni passi di computazione [[Macchina di Turing#^f06de7|^]] restituiscono un solo risultato
4. ogni passi di computazione [[Macchina di Turing#^f06de7|^]] con lo stesso passo restituisce sempre la stessa computazione
5. non c è limite e per dimostrarlo basta creare una macchina che non converge per nessuno ingresso (e quindi ha sempre infiniti passi)
	![[Pasted image 20221012004606.png]]