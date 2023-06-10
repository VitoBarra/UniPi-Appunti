---
type: nota
course: Calcolo Numerico
topic: 
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Metodo della bisezione
---
questo metodo per carcere gli _zeri_ di una [[Funzioni|funzione]] $f:[a,b]\rightarrow \mathbb{R}$ si può applicare sotto le _ipotesi_ che 
- $f(a)f(b) < 0$. ovvero che i segni agli estremi del intervallo siano discordi.
- $f \in C^{0}([a,b])$ ovvero che $f$ sia _[[Continuità di una funzione|continua]]_ 
questo ci dice che _esiste almeno_ una soluzione dove $f(x)=0$. non possiamo dire quante. 
invece se la funzione è [[Funzione Monotona|Funzione Monotona]] esiste un unica soluzione.

il metodo consiste di fare una [[Ricerca Binaria]] su i valori di una funzione. si parte quindi da 
$a_{0} = a ,b_{0} = b$ e si calcola $c_{0}=\cfrac{a_{0}+b_{0}}{2}$ e si procede con il normale algoritmo di _ricerca binaria_
![[Pasted image 20230512163407.png]]

```pseudo
    \begin{algorithm}
    \caption{binary Serch}
    \begin{algorithmic}
      \Procedure{BinarySerch}{$a,b,c$}
        \For{k}
			\State $c_k = \cfrac{a_k+b_k}{2}$
	        \If{$f(a)f(b)\leq 0$}
	        \State$a_{k+1} = a_k$
	        \State $b_{k+1} = c_k$
	        \Elif{}
	        \State $a_{k+1} = c_k$
	        \State $b_{k+1} = b_k$
	        \EndIf
        \EndFor
      \EndProcedure
      \end{algorithmic}
  \end{algorithm}
```
questo metodo trova _una sola soluzione_ dipendentemente da i parametri di inizio che si scelgono. non ci da informazioni sulle altre soluzioni.

si utilizza un $for$ siccome posso calcolare esattamente il numero di _passi_ $k$ che mi servono per riuscire ad _approssimare_ il risultato con una tolleranza $tol$ scelta a piacere. questo sfruttando il fatto che posso sempre sapere la grandezza del intervallo che sto analizzando facendo $b_{k}-a_{k} = \cfrac{b-a}{2^{k}}$ e posso limitare questo intervallo dalla mia _tolleranza_ e avere quindi $\cfrac{b-a}{2^{k}} \leq tol$. risolvendo questa disequazione ottengo il numero di passi necessari.
$$
\begin{array}
\cfrac{b-a}{2^{k}}  & \leq &  tol \iff  \\
2^{k}\cdot tol  & \geq &  b-a  \\
2^{k}\cdot tol  & \geq &  \cfrac{b-a}{tol}  \\
k  & \geq & \left\lceil \log_{2}\left( \cfrac{b-a}{tol} \right) \right\rceil 
\end{array}$$
anche se va con il logaritmo $k$ nella pratica può crescere molto

sapendo che lo _zero_ della funzione è necessariamente al interno di questo intervallo possiamo dire che l errore di _approssimazione_ è limitato da   $|\alpha -c_{k}|\leq \frac{tol}{2}$  
dove  $c_{k}$ è lo _zero calcolato_ dal algoritmo e $\alpha$ lo _zero vero_.
![[Pasted image 20230512171901.png]]
questo algoritmo funziona siccome $b \geq a_{k+1} \geq a_{k}$ e $b_{k+1}\leq b_{k} \leq a$
ovvero che i vari $a_{k}$ e $b_{k}$ si spostano internamente e non si superano mai.