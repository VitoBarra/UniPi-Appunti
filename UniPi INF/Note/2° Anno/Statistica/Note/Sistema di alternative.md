## Sistema di alternative

si chiama sistema di alternative una partizione di $\Omega$ in $n$ eventi non trascurabili $B_1,\dots,B_n$

### Formula di Bayes
sia $B_1,\dots,B_n$ un sistema di alternative: assegnato una qualunque evento A non trascurabile, valgono le formule

$$
\mathbf{P}(A) = \sum^n_{i=1}\mathbf{P}(A|B_i)\mathbf{P}(B_i)
$$

$$
\mathbf{P}(B_i|A) =\frac{\mathbf{P}(A|B_i)\mathbf{P}(B_i)}{\mathbf{P}(A)} =\frac{\mathbf{P}(A|B_i)\mathbf{P}(B_i)}{\sum^n_{i=1}\mathbf{P}(A|B_i)\mathbf{P}(B_i)}
$$