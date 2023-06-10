In crittoanalista conosco è tutto tranne la chiava, la casualità è necessaria elimare le regole toglie gli appigli al critto analista per decrittografare il messaggio 


Esistono cifrari perfetti 
 - one time-pad : non da nessuna informazione perché la chiava deve esssere lunga quanto il messaggio e questo trasferisce la sua quasualita al messaggio rendendolo indecifrabile senza la chiave 
	- dIfficolta nello scambiare la chiave ( bisognerebbe mandare la chiave come se fosse il messaggio quindi c è un problema di circolarità )



**Cifrari sicuri 

Un cifrario viene considerato sicuro se il migliore algoritmo per decifrare senza la chiave è il peggiore ovvero la forza bruta. 

I cifrari sicuro per decifrare senza chiave necessitano la s9uzione di problemi matematici della classe NP che per ora si pensa che sia diverso da P e quindi gli algoritmi sono sempre esponenziali 




**AES

Usa chiavi simmetriche è a blocchi e una chiavi brevi 
I dispositivi si accordano sulla chiave che cambia ad ogni sessione di comunicazione 

Scambio delle chiavi in modo sicuro su canale insicuro 
		protocollo DH 


**altro

Esiste crittografia senza scambio di segreto ( non implementato ?)

Crittografia asimmetrica 
 Chiave publica: serve per careare crittogramma
 Chiave privata: più che segreta la sa una sola persona e serve a decifrare i crittogrammi fatti con la corrispettiva chiave privata 
  $$ c= C(m,k_{pub}) $$

  $$m = D (c,k_{prv})$$

Questo si ottiene con una fuzni9ne facile da colacolare e difficile da invertire 
RSA ( minchia lo stesso del Carmen pazzurdo)
	  
Modello molti ad uno 

Può essere usato per scambiarsi la chiave ma poi le comunicazione vengono effettuate con AES

*svantaggi*
Un po' troppo lento 
Prono a chosen plain-text










20-09-2022:
 rappresentazione matematica degli oggetti
 Alfabeto: Numero finito di caratteri

Alfabeto $$<teta$$
N oggetto da rappresentare 
- d(n,N): lunghezza della sequenza più lunga che rappresenta un oggetto dell insieme
-$$  D_{Min}$$

Caso peggiore rappresentazione unaria 
$$ s=1$$

Rapresentazione binaria 
$$s=2, $$
- per ogni oggetto $$k>1,2^2$$

$$d_{min}$$


Con un numero di caratteri posso costruire delle rappresentazioni esponenziale

***rapresentazipne s-arie







Una rapresentazio è una qualunque ha un numero massimo di caratteri di ordine logaritmi 

La praresentazione posizionale è sempre efficiente  con $$s>2$$

Note apparte 
l li algoritmi è infinito ma numerabile mentre i problemi sono infiniti in continuo 

Le sequenze di stringhe finite di un alfabeto finito sono un insieme numerabile  ma Non se ordinato con ordine alfabetico c è bisogno del ordinamento canonico ovvero le si ordina per lunghezza e nella stessa lunghezza in modo alfanumerico 



Possiamo vedere un problema come una funzione che prende i dati in input e da un risultato in author. L eleco delle funzioni sono infiniti r non numerabile mentre le sequenze di passi son un insieme infinito ma numerabile quindi L insieme degli algoritmi è più piccolo del insieme dei problemi 






***spostare in ProgAlgo

Problemi di decisione 

Problemi di ricerca 
Problemi di ottimizzazione 

 Calcolabilità e complessità studiano i problemi decisionali siccome tutti gli altri tipi possono riformulare come problemi decisionali mantenendo la difficoltà 


2022-10-03:


Dimostrare che una [[sequenza sia casuale secondo Kormogorov]] è un problema indecidibile. 
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


### Problema della Primalita
Se un numero è composto ha almeno un divisore minore della radice di n

L algoritmo di forza brutta fa $rad{n}$ che è esponenziale  (diventa $O(2^\frac{n}{2})$)

#### Algoritmo Randomizato 
Due famiglie di algoritmi Randomizati: 
- _Las Vegas_:  sono sicuramente corretti e eseguono in un tempo probalmente breve (quick sort)
- _Monte Carlo_: sono probabilmente corretti e eseguono in un tempo sicuramente breve (Test Di primalita )
	- un algoritmo del genre ha senso se la probabilità d errore è matematicamente misurabile e deve poter essere reso arbitrariamente piccolo  


test di primalita di Miller Rabin:
	Si base sui risultare di [[teoria dei numeri]] che dimostrano che i numeri primi soddisfano sempre delle proprietà. Queste proprietà pero sono necessarie ma non sufficenti il che significa che possono esistere dei numeri he suffissano queste proprietà che non sono primi.,fortunatamente sono pochi.  Questo rende questo algoritmo di primalita  probabilistico
- per ogni N numero dispari di n bit posso 
	- scomporre $N-1 = 2^w\cdot z$ 
- Se N è primo $\implies$ 
	- $2 \leq y \leq N-1$  con y Interro arbitrario (testimone )
	- $y^z mod N = 1 \or \exist i,0 \leq i \leq w  (y^z)^{2^i} mod N= -1$
	se N è composto tra 1 e N-1 che soddisfano i predicati P1 e P2 è minore di N/4
	Ripetendo il test con testimoni di versi posso abbassare la probabilità d errore. Se per k volte i due predicati sono vero allora N è primo con probabilità di errore $(\frac{1}{4})^k$
```C
void verifica(){
	
}
```
analisi della complessità:
- primo predicato prende $log(n)$
- Secondo predicato
	1. per l  [[Algoritmo delle Quadrature successive o esponeziazione veloce]]  La complessità è  



Cercare i primi molto grandi 
N: # numero di bit del numero da generare 


Primo (n,k) genera un primo di almeno n bit con probabilità d errore $(\frac{1}{4})^k$
- Genera una sequenza S di n-2 bit
- Genera N = 1S1 il primo uno e per assicurare si che non ci siano x 0 a sinistra e qundi per avere una codifica significativa e il secondo per rendere il mnumerpo sempre dispari 


While(TEst_MR(n,k) == 0) {N=N+2}
Return N


I numeri primi sono densi cade miadiamente un  primo in un intorno $log_e$ di un numero grande 



## Classe di complessità RP random Polinomia


Classei dei problemi decisionali verificabili in tempo polinomialele Randomizati 



## Cifrarei storici 
Cifrario di cesare 
Viva il prima i 


$$Pos(y)=(pos(y)+k) \mod 26$$


[[Formula di Eulero]] da vedere dal corso di algebra per i cifrarei ci cedere affini 




2022-10-17: Cifrari perfetti

Nei cifrari perfetti La sicurezza non è legata a nessuna difficolta computazionale sono sicuri a presncindere siccome il esssaggio e il crittogramma sono completamente scorrelati. È un cifrario simmetrico

L informazione è protetta da una chiave e l attacco assurgente è inutile perche non darebbe nessun risultato significativo 


Decifrare il messaggio con una chiave “sbagliata” da un messaggio sensato quindi un critto analista non saprebbe mai quale è il messaggio vero. 

È costoso generare la chiave che deve essere molto lungo 


>[!note]
>Non si usa in contesti di massa ma in comunicazioni classificate dove deve esserci una sicurezza assoluta


MSG: spazio dei messaggi.
CRITTO: spazio dei crittogrammi 
KEY: spazio delle chiavi.

M= [[Variabili Aleatorie (Casuali)| variabile aleatoria ]] che descrive il comportamento del mittente, assume valori in MSH
C= VAriabile aleatoria che descrive il processi di comunicazione assume valori in CRITTO


P(M=m) = Probabilita che il mittente voglia inviare il messaggio M
P(C=c) = probabilirita che sul canale stia transitando un crittogrammma c

P(M=m|C=c) = probabilita che sul canale ci sia il messaggio m condizionata dal fatto che sul canale sta passando c 


## definizine 

un cifrario è perfetto se per ogni messaggio appartenente allo spazio dei messaggi e per ogni crittogrammi appartenenti dallo spazio dei crittogrammi al pababilita condizionata P(M=m|C=c) = P(M=m)

La conoscenza del crittoanalista non cambia dopo aver ossservato il crittogramma c 


## teorema i Shannon
Su un crittogramma è perfetto deve avere almeno tante chi avevi quando i possibili messaggi 


### DImostrazione
$m_k$ = # numero di chiavi
$nm$ = # numero di massaggi

Sopponiamo $n_k<n_m$ 

S= # messaggi che possono corrispondere $c C \leq N_k$
S<n_m ovvero esistono dei messaggi che non possono corrispondente a c e quindi si ha 
P(M=m’ ) >o
P(M=m’|C=c) = 0
Quindi non è perfetto



## One-TIme-Pad
Msg,Critto,key = ${\{0,1\}}^n$
CIfratura  = m= sequenza di bit del messaggio in XOR con n bit del stringa di bit  delle chiave. Poi questo questi n bit della chiave si scartano  
Decifrazione:
La cifratura 
c = crittogramma. 
c XOR k

 Se su usassero la stessa chiave più volte si potrebbe

C= m XOR k
C’ = m’ XOR k

C XOR C =m XOR k Xor m’ XOrm = m Xor m’ 
Ovvero nuove informazioni  pe il crittonalsita se si trovano strisce di zero allora so che una parte del messaggio è uguale

## Dimostrazione di perfettezza 
1. tutti i messaggi hanno lunghezza n
2. tutte le sequenza di n bit sono messaggi possibili 
	- tutti I messaggi hanno una probabilita non nulla molta bassa di essere inviato (non necessariamente queste probabilità sono uguali)
3. Chaive scelta a caso per scegli perfettamente a caso per ogni key = ${\{0,1\}}^n$ $(\frac{1}{2})^n$


 Sotto queste ipotesi one time pad è un cifrario perfetto e minimale dove minimal esignifica che impiega il numero minimo di chiavi.



$\forall m \in MSG, \forall c\in CRITTO$
$P(M=m|C=c)= P(M=m)$

$P(M=m|C=c)= \frac{P(M=m \cup C=c)}{P(C=c)}$

Per proprietà dello XOR fissato m diverse producono crittogrammi diversi 

$\exists !$ Chiave che tra che trasforma m in c $c =m \oplus k \implies k = c \oplus M$ 


$\frac{P(M=m)P(C=c)}{P(C=c)} =\frac{P(M=m)\not{P(C=c)}}{\not{P(C=c)}}$





