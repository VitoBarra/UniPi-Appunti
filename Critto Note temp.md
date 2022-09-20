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
RSA ( mischia lo stesso del Carmen pazzurdo)
 

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

 Calcolabilita e complessità studiano i problemi decisionali siccome tutti gli altri tipi possono riformulare come problemi decisionali mantenendo la difficoltà 