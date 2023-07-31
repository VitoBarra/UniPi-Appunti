---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrario a Composizione di blocchi
---
Nei cifrari [[Cifrario a chiave Simmetrica AES|AES]] e [[Cifrario a chiave Simmetrica DES|DES]] dividendo il messaggi in blocchi  si possono producono blocchi _cifrati_ uguali inducendo una periodicità nel crittogramma che fornisce utili informazioni per la crittoanalisi. 

una soluzione è detta _Cipher Block Chaining_ (CBC). 
CBC utilizza il risultato della cifratura del blocco precedente per crittografare il prossimo blocco cosi facendosi si segue [[Criteri di Shannon per i cifrari|principio della diffusione di Shannon]] inducendo una dipendenza di posizione tra il blocco in elaborazione e quelli precedenti.
cosi facendo i _blocchi uguali_ nel messaggio vengono cifrati in _modo diverso_ eliminandone cosi la periodicità.

Supponiamo che il _cifrario d’origine_ operi su blocchi di $b$ bit con chiave $k$. Il messaggio viene diviso in blocchi, $m = m_1m_2 \dots m_{s}$: se $ms$ contiene se $r < b$ bit lo si completa aggiungendovi la sequenza binaria $10000\dots$  di lunghezza $b − r$, altrimenti si aggiunge al messaggio un intero nuovo blocco $ms+1 = 10000\dots$  di lunghezza $b$. In entrambi i casi la nuova sequenza funge da terminatore del messaggio. 

![[Pasted image 20230709191538.png]]

Sia ora $c_0$ una sequenza di $b$ bit scelta per esempio in modo casuale e diversa per ogni messaggio (nulla osta a che c0 sia pubblica).
funzione di  [[Cifratura e Decifratura|cifratura e decifratura]]: 
$$
\begin{array}{}
c_i = \mathcal{C}(m_i \oplus c_{i−1}, k) \\
m_i = c_{i−1} \oplus \mathcal{D}(c_i, k)
\end{array}
$$
la  _cifratura_ sia strettamente sequenziale siccome impiega il risultato $c_{i−1}$ del passo precedente
la _decifrazione_ puo essere eseguito in _parallelo_ se tutti i blocchi cifrati sono disponibili.

per garantire che blocchi uguali non creino valori uguali bisogna utilizzare per ogni messaggio una sequenza $c_0$ diversa essa puo essere costruita in modo _[[Generazione di numeri Pseudo Casuali|pseudocasuale]]_, per esempio una marca del orario del calcolatore. questa viene spedita in chiaro con il crittogramma e scartata all’atto della _decifrazione_.
Tutto ciò non pregiudica in alcun modo la robustezza del sistema crittografico. I vantaggi offerti dal metodo CBC dovrebbero essere evidenti. 

I processi di cifratura e decifrazione non sono apprezzabilmente piu lenti di quelli del _cifrario originale_ poiché le operazioni di composizione impiegano esclusivamente l’operazione di XOR. 
