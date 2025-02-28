---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Reti neurali - Autoencoders
---
Gli __autoencoders__ sono sono delle [[Reti Neurali (NN)|reti neurali]] allenate in [[Algoritmi di learning supervisionato|modo supervisionato]]  per riprodurre il proprio input su proprio output. È composto da:
- __Encoder__: trasforma l'input in una rappresentazione più compatta.
- __Decoder__: riconverte la rappresentazione compatta nel dato originale.
e può essere vista come una semplice [[Funzioni|funzione composta]] infatti prendendo $h$ come la funzione di __encoding__ e $f$ come funzione di __deconding__ abbiamo che un auto encoder fa l operazione $$r=f(g(x))$$ e si cerca di minimizzare l errore tra $r$ e $x$
 

gli __autoencoders__ solo solitamente di due tipi:
- __Undercomplete__: il layer nascosto ha meno unità dell’input, costringendo la rete a catturare solo le caratteristiche più rilevanti.
- __Overcomplete__: il layer nascosto è più grande dell'input, ma si usa la regolarizazione per  applicare dei vincoli di sparsità il che permette di avere proprieta aggiuntive oltre al "copia e incolla" dei dati, come ad empio il denoising 
![[Pasted image 20250206182601.png]]

Un’applicazione tipica è il __denoising autoencoder__, che impara a ricostruire un’immagine originale da una versione rumorosa.
![[Pasted image 20250206182635.png]]