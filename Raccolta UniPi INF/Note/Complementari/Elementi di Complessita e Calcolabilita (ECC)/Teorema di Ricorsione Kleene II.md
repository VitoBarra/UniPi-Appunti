---
type: nota
course: Elementi di calcolabilita e complessita
topic: 
tags: ECC
---

Prev: [[Elementi di Complessità e Calcolabilità (ECC)]]

# Teorema di Ricorsione Kleene II
---

### Teorema
$\forall f$ funzione calcolabili totali $\exists n$  tale che $$\varphi_n=\varphi_{f(n)}$$ tale indice $n$ viene chiamato punto fisso non rispetto al valore della funzione $f$ ma rispetto alla semantica dei programmi

intuitivamente questo teorema ci dice che esiste una funzione che trasforma un programma in un altro programma senza cambiarne la semantica, un esempio concreto di questo teorema sono i [[Compilatori]]. 

#### Dimostrazione

Definiamo una funzione 
1. $$\begin{equation} 
\psi(u,z)=\varphi_{d(u)}(z)=
\begin{cases}
\varphi_{\varphi_u(u)}(z) &se \ \varphi_u(u) \downarrow \\
indefinito
\end{cases} 
\end{equation}
$$
per il [[Teorema del parametro]] sappiamo che $d(u)$ totale e [[funzione iniettiva|iniettiva]]. 

Dati $f$ una funzione totale e calcolabile $f \circ d$ funzione calcolabili e sia $v$ un indice tale che
2. $$\varphi_v(x) =f(d(x))$$
 questa funzione é totale perché f e d e quindi abbiamo che $\varphi_v(v) \downarrow$
 e per la definizione 1 abbiamo che $\varphi_{d(v)} =\varphi_{\varphi_v(v)}$

poniamo 
3. $$n=d_(v)$$
questi sono sempre valori diversi per l iniettivita di $d$
e prossimo dire in fina che 
$$\varphi_n\stackrel{3}{=}\varphi_{d(v)}\stackrel{1}{=}\varphi_{\varphi_v(v)}\stackrel{2}{=}\varphi_{f(d(v))}\stackrel{3}{=}\varphi_{f(n)}$$

## Prosperità
nelle ipotesi del teorema di ricorsione
- il punto fisso è calcolabile mediante una [[Funzioni totali|funzione totale]] e [[funzione iniettiva|iniettiva]] $g$ a partire dal indice di $f$
- ci sono $|\N|$ punti fissi di $f$
#### Dimostrazione
1. dato h(x) calcolabile e totale tale $\forall n$ 
$$\varphi_{h(x)}(n)=\varphi_x(d(n)) \implies g(x)=d(h(x))$$
2. conseguenza del [[Padding Lemma]]

>[!warning]
>(senza considerare l iniettivita di g questa è una dimostrazione incompleta presa pari dal libro)
>