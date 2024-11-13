---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Machine Learning (ML)]]"
tags:
  - IA
Area: "[[Concetti generali del Machine Learning]]"
topic: 
SubTopic: 
---
# Apprendimento supervisionato
---
l __apprendimento supervisionato__ è una categoria di algoritmi di [[Algoritmi di Macchine Learning|apprendimento]] che utilizza dei dati _Etichettati_. 

__Sia__ il __Training set__, definito come una serie di punti $$(x_1,y_1),(x_2,y_2),\dots,(x_n,y_n)$$ dove ogni punto è generato da una funzione $y_i=f(x_i)+noise$, trovare una funzione $h$, detta ipotesi, che è una approssimazione della funzione vera $f$.



Formalmente, una metrica è una funzione chiamata funzione di loss $l$ e si definisce il valore di loss come 
 $$Loss=\sum_i^nl(f(x_i),h(x_i))$$ 
Il valore di $Loss$ quantifica quanto il modello erra nella predizione dell' output.
Si deve scegliere una funzione di loss adatta al problema che si vuole affrontare in modo che un basso valore di $Loss$ correli con un miglior risultato.
Infatti, un algoritmo di \textit{apprendimento supervisionato} minimizza la loss scelta con l'obiettivo di selezionare un'ipotesi $h$ tra tutte le ipotesi possibili in $\mathcal{H}$. 


I problemi affrontabili con l'\textit{apprendimento supervisionato} si dividono in due classi: 
\begin{enumerate}
    \item \textbf{Classificazione}: dove l'input deve essere mappato in una o più delle $n \in \mathbb{N}$ categorie disgiunte; se le categorie sono due la classificazione viene detta binaria altrimenti ennaria. 
    \item \textbf{Regressione}: dove l'input viene mappato in uno o più numeri continui. 
\end{enumerate}

Per queste due classi di problemi si conoscono delle funzioni di loss adatte alla loro risoluzione. Ad esempio, per la \textit{regressione}, è comunemente usata la \textit{Mean Squared Error} (\textbf{MSE}): $\frac{\sum^n_{i=1}(\hat{y}-y_i)^2}{n}$, mentre, per la classificazione ennaria, si usa la \textit{sparse categorical crossentropy} o la \textit{categorical crossentropy} a seconda dell'encoding delle lable.


I __dati di training__ detti training example formalizzati  come , sono delle associazioni per una funzione sconosciuta  detta target function. con i training example se ne definiscono alcuni punti 
- le associazioni sono dati da un _teacher_ e sono prese per vere e utilizzate per stimare le funzione corretta
_Trova_: un approssimazione di $f$ detta _ipotesi_ che verrà poi utilizzata per predirei il valore dei nuovi dati non visti 


ci sono due tipi problemi risolvibili con questo tipo di apprendimento 
- _Clssificazione_: la funzione $f(x)$ restituisce la classe assunta corretta per $x$
	- $f(x)\in \mathbb{F}^k\times \mathbb{N}$. $f$ è quindi una funzione discreta, e ogni numero intero è una diversa classe 
- _Regressione_: la funzione $f(x)$ restituisce output reali approssimando la funzione reale _target_
- $f(x)$ $\in \mathbb{F}\times\mathbb{R}^k$
	 
![[991D6D4A-9F89-4A4E-BE65-509CB69C0C3C.jpeg]]

>[!example]- Alcuni esempi
>![[84563ACF-1E29-4871-81B7-628DCD565D04.jpeg]]
