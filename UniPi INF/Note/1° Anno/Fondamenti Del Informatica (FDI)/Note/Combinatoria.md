---
type: nota
course: Fondamenti Di Informatica
topic: 
tags:
  - FDI
Parent MOC: "[[Fondamenti Del Informatica (FDI)]]"
---
# Combinatoria
---

### Definizione

![[UniPi INF/Note/1° Anno/Fondamenti Del Informatica (FDI)/Media/Untitled.png]]
#### Permutazioni
il numero di modi in cui si possono rovinare gli elementi di $\{ 1,\dots,n \}$ è la formula $$n!$$
##### Permutazione cona ripetizioni
le permutazioni con ripetizioni 

$$P^{n_{1},\dots,n_{n}}_{n}=\frac{n!}{n_{1}!,\dots,n_{n}!}$$

1. Principio dei fattoriali: Iniziamo con il fatto che il fattoriale di un numero rappresenta il numero di modi unici in cui è possibile disporre quei numeri in un ordine specifico. Ad esempio, il fattoriale di 5 (scritto come 5!) rappresenta il numero di modi in cui è possibile disporre 5 oggetti distinti in ordine. Quindi, 5! = 5 x 4 x 3 x 2 x 1 = 120 rappresenta tutti i modi unici in cui puoi riordinare 5 oggetti diversi.

  

2. Trattamento delle lettere ripetute: Quando hai una parola con lettere ripetute, non tutte le lettere sono diverse tra loro. Alcune sono identiche, e quindi devi considerare il modo in cui queste lettere identiche possono essere riordinate tra loro. Questo è dove entrano in gioco i fattoriali delle lettere ripetute. Ad esempio, nella parola "MISSISSIPPI", hai 4 "I", 4 "S" e 2 "P". Pertanto, stai considerando il modo in cui queste lettere identiche possono essere riordinate tra loro senza cambiare l'aspetto generale della parola.

  

3. Divisione per i fattoriali delle lettere ripetute: La divisione per i fattoriali delle lettere ripetute serve a evitare il conteggio duplicato degli anagrammi. Quando hai lettere identiche, senza la divisione per i fattoriali, otterresti un conteggio in eccesso poiché molteplici anagrammi sarebbero identici a causa della presenza di lettere ripetute. La divisione per i fattoriali delle lettere ripetute serve a correggere questo problema, assicurando che ogni anagramma venga conteggiato solo una volta.

  

In breve, la formula tiene conto del numero totale di lettere nella parola e considera come le lettere identiche possono essere riordinate tra loro senza duplicare gli anagrammi. Questo è il motivo per cui funziona per calcolare il numero di anagrammi di una parola.
>[!tip]
>ci si puo contare il numero di _anagrammi_




![[UniPi INF/Note/1° Anno/Fondamenti Del Informatica (FDI)/Media/Untitled 1.png]]

![[UniPi INF/Note/1° Anno/Fondamenti Del Informatica (FDI)/Media/Untitled 2.png]]

### Disposizioni
Dato un [[Insiemi Matematici|insieme]] finito $A$ con $|A| = n$ e un intero $k ≤ n$, una _disposizione_ degli elementi di $A$ in $k$ posti è una sequenza ordinata $a_1, \dots , a_k$ dove esattamente $k$ elementi di $A$ appaiono esattamente una volta.


si puo ridurre una disposizione ad una combinazione con la formula
$$\begin{pmatrix}
n \\ k
\end{pmatrix} \cdot k! = \frac{n!}{(n-k)!}$$
##### Disposizione con ripetizione
se vogliamo permettere la ripetizione di elementi 
la formula diventa 
$$n^{k}$$



