## Probabilità condizionata e indipendenza

### Probabilità condizionata:

preso uno spazio delle probabilità $(\Omega,\mathcal{F},\mathbf{P})$ conoscendo l’esito di un evento $B$ non trascurabile si possono fare delle considerazioni su un altro evento $A$ non trascurabile modificandone cosi la Probabilità, la Probabilità Condizionata di $A$ rispetto a $B$ è definita come

$$
\mathbf{P}(A|B) = \frac{\mathbf{P}(A \cap B)}{\mathbf{P}(B)}
$$

### Esempio

nel caso del uscita di un numero sulla rullette

- $A = \{16\}$
- $B =\{2,4,\dots,36\}$ cioè i numeri pari

abbiamo che

$$
\mathbf{P}(A|B) = \frac{\mathbf{P}(A \cap B)}{\mathbf{P}(B)} = \frac{\frac{1}{37}}{\frac{18}{37}}=\frac{1}{18}
$$

vale anche per $n$ eventi infatti siano $A_1,\dots,A_n$ e supponiamo che $A_1 \cap\dots \cap A_{n-1}$ si  un evento non trascurabile allora

$$
\mathbf{P}(A_1 \cap\dots \cap A_n) = \mathbf{P}(A_1)\mathbf{P}(A_2|A_1) \dots\mathbf{P}(A_n|A_1 \cap\dots \cap A_{n-1})
$$