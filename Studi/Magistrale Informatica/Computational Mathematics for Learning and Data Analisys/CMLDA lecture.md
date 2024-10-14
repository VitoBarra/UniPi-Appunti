# 2024 - 09 - 19

ci basiamo su [[Norme Matriciali e Norme Vettoriali|norme]] euclidee per i probleml perche sono generalmente piu facili

[[Algebra Lineare (AL)]] e [[Calcolo Numerico(CN)]] 


Trefethen-Bau : libro da seguire, Da cercare 

da  sotto ogni linguaggio usa la  libreria Blas/Lapack.  

Guardare linguaggio Julia: linguaggio che dovrebbe unire in vantaggi di C++, matlab e py 

[[Soluzioni di un sistema lineare]]


in algebra lineare ok fare $y=A^{-1}x$ ma in mat lab la stessa cosa si fa come $x=A/y$
mantre in py è **scipy.sorlve(A,x)**

Da riguardare le [[Uso delle basi|basi]] di algebra lineare.
Ripassare anche le [[Trasformazioni Lineari Geometriche|trasformazionei linere]]


costo computazioneale prodotto tra matricie $m\times n \cdot n \times p$ è pari a $pm(2n-1)$ quindi $O(pmn)$

Flops = floating point operation

In matlab per fare la trasposta in di una colona  $c'$ mentre per fare il trasposto di una riga $r^T$ 
importate fare i calcoli con le metrici "a pezzi" siccome per motivi di localita delle [[Cache]] la performance è migliore in questo modo 
![[Chopperd Matrix.jpg]]


nel caso di matrici [[Matrici quadrate|triangolari inferiori o superiori]] si puo risolvere il sistema tramite sostituzione diretta 

$O(n^2)$ invece di trovare l inversa che costa $O(n^3)$ 
anche questo caso si puo risolvere con i blocchi quindi vale anche per una matrici triangolari a blocchi ma non si puo risolvere direttamente è bisogno di calcolare l inversa del blocco.





 
# 2024 - 09 - 19