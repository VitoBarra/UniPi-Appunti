---
Course: "[[Algebra Lineare (AL)]]"
topic: nota
tags:
  - AL
---
# Algoritmi per trovare basi
---

## Algoritmo di completamento

Abbiamo definito la dimensione di uno spazio vettoriale $V$ come il numero di elementi in una sua base. Adesso abbiamo bisogno di algoritmi concreti per determinare una base di $V$ in vari contesti. Iniziamo con una proposizione utile.

**Proposizione 2.3.20.** Sia $V$ uno spazio vettoriale e $v_1, \dots, v_k \in V$ dei vettori indipendenti. Sia $v_{k+1} \in V$. Allora:

$$
v_1, \dots, v_{k+1} \text{ sono indipendenti } \iff v_{k+1} \notin \operatorname{Span}(v_1, \dots, v_k).
$$

Dimostrazione.

- $(\Rightarrow)$ Se per assurdo $v_{k+1} \in \operatorname{Span}(v_1, \dots, v_k)$, allora otteniamo

$$
v_{k+1} = \lambda_1 v_1 + \cdots + \lambda_k v_k,
$$

quindi i vettori $v_1, \dots, v_{k+1}$ sono dipendenti.

- $(\Leftarrow)$ Supponiamo che

$$
\lambda_1 v_1 + \cdots + \lambda_{k+1} v_{k+1} = 0.
$$

Se $\lambda_{k+1} = 0$, otteniamo una combinazione lineare nulla dei primi $v_1, \dots, v_k$, quindi $\lambda_1 = \cdots = \lambda_k = 0$. Se $\lambda_{k+1} \neq 0$, dividiamo tutto per $\lambda_{k+1}$ ottenendo una dipendenza di $v_{k+1}$ dai precedenti, che e assurdo.

Descriviamo adesso l'algoritmo di completamento a base. Sia $V$ uno spazio vettoriale di dimensione $n$. Siano $v_1, \dots, v_k \in V$ dei vettori indipendenti qualsiasi, con $k < n$. Possiamo sempre completare $v_1, \dots, v_k$ ad una base di $V$ nel modo seguente. Siccome $k < n$, i vettori $v_1, \dots, v_k$ non sono una base di $V$, in particolare non generano $V$. Allora esiste un $v_{k+1} \in V$ tale che

$$
v_{k+1} \notin \operatorname{Span}(v_1, \dots, v_k).
$$

Aggiungiamo $v_{k+1}$ alla lista, che adesso diventa $v_1, \dots, v_{k+1}$. La nuova lista e ancora formata da vettori indipendenti per la proposizione precedente. Continuiamo finche non otteniamo $n$ vettori indipendenti $v_1, \dots, v_n$. Questi devono essere una base per il Lemma 2.3.18.

**Esempio 2.3.21.** Consideriamo i vettori indipendenti in $\mathbb{R}^3$

$$
v_1 = \begin{pmatrix}1\\1\\0\end{pmatrix},
\qquad
v_2 = \begin{pmatrix}1\\0\\1\end{pmatrix}.
$$

Per completare la coppia $v_1, v_2$ ad una base di $\mathbb{R}^3$ e sufficiente aggiungere un terzo vettore qualsiasi che non sia contenuto nel piano $\operatorname{Span}(v_1, v_2)$. Ad esempio, $v_3 = e_1$ funziona. Ricordiamo che se $e_1, e_2, e_3$ sono i vettori della base canonica di $\mathbb{R}^3$, allora $v_1, v_2, e_1$ e una base di $\mathbb{R}^3$.

## Algoritmo di estrazione

Descriviamo adesso l'algoritmo di estrazione di una base. Sia $V$ uno spazio vettoriale e siano $v_1, \dots, v_m$ dei generatori di $V$. Vogliamo estrarre da questo insieme di generatori una base per $V$.

L'algoritmo funziona nel modo seguente. Se i generatori $v_1, \dots, v_m$ sono indipendenti, allora formano gia una base per $V$ e siamo a posto. Altrimenti, esiste almeno un $v_i$ che puo essere espresso come combinazione degli altri. Se lo rimuoviamo dalla lista, otteniamo una lista di $m - 1$ vettori che continuano a generare $V$. Dopo un numero finito di passi otteniamo una lista di vettori indipendenti, e questi sono una base di $V$.

**Esempio 2.3.22.** Consideriamo i vettori di $\mathbb{R}^3$

$$
v_1 = \begin{pmatrix}1\\1\\0\end{pmatrix},
\qquad
v_2 = \begin{pmatrix}0\\1\\1\end{pmatrix},
\qquad
v_3 = \begin{pmatrix}-1\\1\\1\end{pmatrix},
\qquad
v_4 = \begin{pmatrix}0\\0\\1\end{pmatrix}.
$$

Si verifica facilmente che questi generano $\mathbb{R}^3$, ma non sono indipendenti, ad esempio

$$
v_1 - 2v_2 + v_3 + v_4 = 0.
$$

Ciascuno dei quattro vettori e esprimibile come combinazione degli altri tre: rimuovendo uno qualsiasi di questi quattro vettori otteniamo una base di $\mathbb{R}^3$.

Concludiamo con una proposizione che risulta utile in molti casi concreti quando dobbiamo mostrare che un certo insieme di vettori e una base. In generale, per dimostrare che $n$ vettori sono una base di $V$, dobbiamo dimostrare che generano e che sono indipendenti. La proposizione seguente dice che, se sappiamo gia che $\dim V = n$, allora una qualsiasi delle due proprieta e sufficiente, perche implica l'altra.

### Preposizioni Interessante

Siano $v_1, \dots, v_n \in V$ e $\dim(V) = n$. I fatti seguenti sono tutti equivalenti:

- $v_1, \dots, v_n$ generano $V$
- $v_1, \dots, v_n$ sono indipendenti
- $v_1, \dots, v_n$ sono una base per $V$

Dimostrazione.

- $(3) \Rightarrow (2)$ e ovvio.
- $(2) \Rightarrow (1)$ e il Lemma 2.3.18.
- $(1) \Rightarrow (3)$. Se $v_1, \dots, v_n$ non fossero indipendenti, potremmo estrarre da questi una base con meno di $n$ vettori, in assurdo per il Teorema 2.3.16.

Usando questo criterio possiamo dimostrare agevolmente il fatto seguente.

---

I vettori

$$
v_1 = \begin{pmatrix} a_{11}\\0\\0\\\vdots\\0
\end{pmatrix},
\quad
v_2 = \begin{pmatrix} a_{12}\\a_{22}\\0\\\vdots\\0
\end{pmatrix},
\quad
v_3 = \begin{pmatrix} a_{13}\\a_{23}\\a_{33}\\\vdots\\0
\end{pmatrix},
\quad \cdots \quad,
\quad
v_n = \begin{pmatrix} a_{1n}\\a_{2n}\\a_{3n}\\\vdots\\a_{nn}
\end{pmatrix}
$$

sono una [[Base di uno spazio vettoriale|base]] di $K^n$ se e solo se i numeri $a_{11}, \dots, a_{nn}$ sono tutti diversi da zero.

Dimostrazione. Mostriamo che

$$
v_1, \dots, v_n \text{ sono indipendenti } \iff a_{11}, \dots, a_{nn} \neq 0.
$$

Supponiamo che

$$
\lambda_1 v_1 + \cdots + \lambda_n v_n = 0.
$$

Questa uguaglianza tra vettori e equivalente al sistema lineare omogeneo

$$
\begin{cases}
a_{11}\lambda_1 + a_{12}\lambda_2 + a_{13}\lambda_3 + \cdots + a_{1n}\lambda_n = 0, \\
a_{22}\lambda_2 + a_{23}\lambda_3 + \cdots + a_{2n}\lambda_n = 0, \\
a_{33}\lambda_3 + \cdots + a_{3n}\lambda_n = 0, \\
\qquad \vdots \\
a_{nn}\lambda_n = 0.
\end{cases}
$$

Mostriamo per induzione su $n$ che

$$
\exists! \text{ soluzione } \lambda_1 = \cdots = \lambda_n = 0 \iff a_{11}, \dots, a_{nn} \neq 0.
$$

Per $n = 1$ il sistema e semplicemente l'equazione $a_{11}\lambda_1 = 0$ ed e chiaro che se $a_{11} \neq 0$ allora $\lambda_1 = 0$ e l'unica soluzione, mentre se $a_{11} = 0$ allora qualsiasi numero $\lambda_1 \in \mathbb{K}$ e soluzione.

Supponiamo l'asserzione vera per $n - 1$ e dimostriamola per $n$. Se $a_{nn} \neq 0$, allora l'ultima equazione $a_{nn}\lambda_n = 0$ implica che $\lambda_n = 0$. Sostituendo $\lambda_n = 0$ in tutte le equazioni precedenti ci riconduciamo al caso $n - 1$ e concludiamo per ipotesi induttiva. Se invece $a_{nn} = 0$, allora $\lambda_1 = \cdots = \lambda_{n-1} = 0$, ma esiste almeno una soluzione non banale con $\lambda_n \neq 0$. In questo caso non e vero che il sistema ha un'unica soluzione. Abbiamo concluso.
