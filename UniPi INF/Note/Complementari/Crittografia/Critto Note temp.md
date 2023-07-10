

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





