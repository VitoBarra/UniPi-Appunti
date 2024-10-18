---
Course: Crittografia
topic: nota
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# La macchina enigma
---
e la prima _macchina crittografica automatizzata_  usata nella seconda guerra mondiale ed è una estensione digitale delle idee del [[Cifrario di Alberti|cifrario di alberti]] 

![[IMG_0632.jpeg]]
![[IMG_0635.jpeg]]


- I _rotori non mantenevano_ la stessa posizione reciproca durante la cifratura  
    Per ogni _lettera battuta_ sulla tastieraIl primo rotore avanzava di un passo, Dopo $26$ passi il rotore era tornato sulla posizione iniziale, e avanzava di un passo il secondo rotore , Dopo la rotazione completa del secondo rotore, avanzava di un passo il terzo rotore  
    La corrispondenza tra caratteri cambiava ad ogni passo (la chiave cambia a ogni passo)

- 26 con le rotazioni del primo rotore rispetto al secondo  
- 26 con le rotazioni del secondo rotore rispetto al terzo 
- 26 con le rotazioni del terzo rotore rispetto al riflettore  
- $26 \times 26 \times 26 = 17576$ chiavi diverse

#### Debolezza
- I _Rotori immutabili_  
    $26^{3}$ _permutazioni_ sono sempre le stesse, applicate nello stesso ordine e sono Note a tutti i proprietari di una macchina _Enigma_
        _Alberti_ aveva previsto, per ogni coppia di utenti, una coppia di dischi diversa da tutte le altre  

##### Possibili soluzioni 
Possibilità di _permutare_ tra loro i tre rotori:
 in questo modo le permutazioni diventano: $$(3!) \times 263 > 105$$si aggiunge il plugboard tra tastiera e primo rotore  
Consente di scambiare tra loro i caratteri di _6 coppie scelte arbitrariamente_ in ogni trasmissione
![[IMG_0637.jpeg]]
Ogni cablaggio è descritto da una sequenza di 12 caratteri (le 6 coppie da scambiare)  
_Combinazioni possibili_:$$\begin{pmatrix}26  \\ 12\end{pmatrix} \approx 10^{7}$$
	Ogni gruppo di 12 caratteri si può presentare in $12!$ permutazioni diverse, ma non tutte producono effetti diversi:
    _AB CD EF GH IJ KL_ 
	_CD AB EF GH IJ KL_ 
	producono lo stesso effetto, e con queste anche tutte le 6! permutazione delle 6 coppie
	Infine si devono considerare i possibili scambi tra gli elementi delle coppie, che producono lo stesso effetto 
	_AB CD EF GH IJ KL_ 
	_BA CD EF HG IJ KL_ 
	Dobbiamo dividere per un ulteriore fattore $2^{6} = 64$
	e quindi il conto diventa$$\begin{pmatrix}
26 \\12 
\end{pmatrix}\cfrac{12!}{6!\cdot 64}>10^{11}$$
_conto algernativo_:
	si scelgono 6 coppie di variabili, in 
	$$\begin{pmatrix}26 \\ 2\end{pmatrix}\begin{pmatrix}24 \\ 2\end{pmatrix}\begin{pmatrix}22 \\ 2\end{pmatrix}\begin{pmatrix}20 \\ 2\end{pmatrix}\begin{pmatrix}18 \\ 2\end{pmatrix}\begin{pmatrix}16 \\ 2\end{pmatrix}=\cfrac{26!}{2^{6}14!}=\begin{pmatrix}26 \\ 12\end{pmatrix}\cfrac{12!}{2^{6}}$$
	modi ,e poi si divide per le $6!$ permutazione tra le coppie:
	$$\begin{pmatrix}26 \\ 12\end{pmatrix} \cfrac{12!}{6!\cdot 64}$$




#### Applicazione
nella seconda guerra mondiale 
- 8 rotori in dotazione da cui sceglierne 3
- aumentarono da 6 a 10  le coppie scambiabili nel _plugboard_
- _elenco di chiavi giornalieri_  in dotazione ai reparti militari.
- assetto iniziale della macchina per quel giorno
- Con l’assetto iniziale si trasmetteva una nuova chiave di messaggio 
- indicava l’assetto da usare in quella particolare trasmissione

 