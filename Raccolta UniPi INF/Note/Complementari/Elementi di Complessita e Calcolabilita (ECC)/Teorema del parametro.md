---
type: nota
course: Elementi di calcolabilita e complessita
topic: 
tags: ECC
---

Prev: [[Elementi di Complessità e Calcolabilità (ECC)]]

# Teorema del parametro o $\large S^m_n$
---
## Teorema
il teorema dice che $\forall m,n\geq 0 \ \exists$ una funzione [[Nozione di Calcolabilità|calcolabile]] totale e iniettiva $s_n^m,$ con $m+1$ argomenti tale che $\forall_i,x_1,\dots,x_m$ 
$$\varphi_{s^1_1(i,x)}^{(n)} = \lambda y_1,\dots,y_n.\varphi_i^{(m+n)}(x_1,\dots,x_m,y_1,\dots,y_n)$$
dove $\varphi^{(x)}$ indica il numero di parametri della funzione.

questo teorema è la base per la valutazione parziale delle funzioni che in informatica sono particolarmente utili siccome ci permetto di riscrivere programmi generali e inefficienti in programma specifici più efficienti 

### Esempio particolare $S^m_n$ con $n=m=1$
esiste una funzione [[Nozione di Calcolabilità|calcolabile]] totale e iniettiva $s_1^1$ con due argomenti tale che $\forall_i,x$
$$\varphi_{s^1_1(i,x)}(y) = \lambda y.\varphi_i(x,y) $$
ad esempio valutando se $\varphi_i(x,y) = x \times f(y)$ se valutiamo $j=s(i,2)$ allora otteniamo in modo effettivo l indice della funzione che calcola $\varphi_j(y)=2 \times y$ 

#### Dimostrazione
per calcolare $\varphi_{s^1_1(i,x)}(y)$ si prende la [[Macchina di Turing]] $M_i$ ([[Tesi di Church-Turing|o un formalismo equivalente]]) decodificando la $i$ con paramenti $M_i(x,y)$ é predisponi i valori iniziali fissando $x$ in anticipo. questa è una procedura effettiva ovvero algoritmica che termina sempre quindi per la [[Tesi di Church-Turing]] esiste una funzione $s = s^1_1$ totale.
questa potrebbe non essere iniettiva ma basta creare una funzione $s'$ con $\varphi_{s'(i,x)}=\varphi_{s(i,x)}$ tale che $s'(i_0,x_0)>s'(i_1,x_1)$ se la codifica della prima coppia è maggiore della seconda. ciò significa che la funzione che genera indici è strettamente crescente e una funzione strettamente crescente è iniettiva. gli indici generati esistono sempre perché gli indici sono $|\N|$ come dimostrato nel [[Padding Lemma]]