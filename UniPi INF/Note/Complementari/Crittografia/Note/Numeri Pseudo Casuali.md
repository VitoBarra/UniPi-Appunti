---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Numeri Pseudo Casuali
---
Dimostrare che una [[Teorema di Kormogorov|sequenza sia casuale secondo Kormogorov]] è un problema indecidibile. 
_DImStrazione:_
$$Random()=\begin{cases}0 \text{    se NON casuale} \\ 1 \text{Se Casuale}\end{cases}$$


```C
Random()
{
	while(true)
	{
	
	}
}
```




Sequenza binaria casuale:
1. La [[Probabilità e variabili aleatorie|Probabilita]] di ottenere 1 = alla probabilita di avere 0 = 1/2
	1. Sostituibili in P(0)>0 e P(1)>0
2. La generazione di un bit è indipendente dai precedenti 


generatori di sequenze casuali.
Fonti:
- FIsiche: Si possono usare fenomeni fisici come generatore (il rumore, la posizione di una testina, lettura di un fotone).  Funziona abstanza bene per chiavi corte. Non si sa in casi pratici.
- numeri Pseudo Causuali: 
	- Generatore lineare
	input: Seme
	$x_1 = (ax_{i-1} + b)mod m$
	questo parte da un valore detto il seme e genera i numeri a partire da quello quindi se gli si da lo stesso seme si otterrà sempre la stessa sequenza di numeri. Se nella sequenza si dovesse tornare al seme la sequenza reinizierebbe da zero infatti è una sequenza periodica. Potrebbe succedere che si genere un numero che si è generato e che si entra in un ciclo di una sequenza 
	GENERARE UNA PERMUTAZIONE di tutti gli interi 
			MCD(B,m) = 1 ovvero devono essere coprimi
			(a-1) deve essere per ogni fattore primo di m
			(a-1) deve essere multiplo di 4se anche m lo è
	per convertire la sequenza in sequenza di bit con 
	Si chiamano Pseudo casuale perche il programma è breve e la ge3nerazione del numero casuale successivo dipedne da valore di prima non c è quindi l indipendenza.
	M,n
	- GENERATORE POLINOMIARE:
		- Superano i test statistici
			1. Test di frequenza: per sequenza lunghe tutti i caratteri sono euquiprobabili
			2. Pokert test:se le sotto sequenze sono eqprobabili
			3. Test di autocorrelazione: verificano che non ci siano valori che si ripetono a distanze regolari 
			4. Ran test: l frequenza delle sequenze di simbolo uguali devono essere esponenziale minore con la lunghezza 
I generatori di numeri pseudocasuali non si possono usare per chiavi crittografiche.

I generati che sono critto graficamente sicuri devono passare il test di 
1. Prossimo bit: se non esiste un algoritmo  di tempo polinomiale in grado di prevedere l $i +1$ bit della sequenza a partire dalla conoscenza degli i bit già generati con probabilità maggiore dio $\frac{1}{2}$


Generatori che superano il test di Prossimo bit

Funzioni one-Way. Facili da calcolare difficili da invertire. Di solito di algebra modulare
La utilizzo in senso crittografico al contrario

GENERATORE BBS
	Genera interi 
	usa il quadrato in modulo 
	Per invertilo serve fare la radice in modulo difficile se il numero non èprim
	LA parità è difficile da verificare (Predicato hard core ovvero in un singolo predicato c è tutta la difficolta computazione )  


2022-10-04:
Generatore basato su cifrari simmetrici:
	r = # bit delle parole prodotte dal cifrario
	s = seme casuale di r bit
	k = chiave segreta del cifrario 

```C
Generatore(s,n)
{
	D= rapresentazione in r bit di data e ora
	y = C(d,k)
	z= s
	for(int i =0 ; i < n; i++)
	{
		x[i]= C(y xor Z,k)
		Z= C(y xor x[i],k)
		Comunicazione al esterno
	}
}
```

