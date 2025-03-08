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
Gli __autoencoders__ sono un particolare tipo di [[NN - Autoassociatore|autoassociatore]] ovvero è una  [[Reti Neurali (NN)|rete neurale]] allenata per riprodurre l'input su proprio output ed è allenata in modo [[Algoritmi di learning NON supervisionato|NON supervisionato]]. 

Gli __autoencoders__ sono definiti da una architettura fissa descrivibile in 2 parti:
- __Encoder__: trasforma l'input in una rappresentazione più compatta.
- __Decoder__: riconverte la rappresentazione compatta nel dato originale.
e può essere vista come una [[Funzioni|funzione composta]] infatti prendendo $g$ come la funzione di __encoding__ e $f$ come funzione di __deconding__ abbiamo che un __autoencoder__ è rappresentabile come: $$r=f(g(x))$$ allenare questa rete significa minimizzare l'errore tra $r$ e $x$  e avere quindi $r \approx x$
 

gli __autoencoders__ solo solitamente di due tipi:
- __Undercomplete__: il layer nascosto ha meno unità dell’input, costringendo la rete a catturare solo le caratteristiche più rilevanti.
- __Overcomplete__: il layer nascosto è più grande dell'input, si usa la regolarizazione per  applicare dei vincoli di sparsità il che permette di avere proprietà aggiuntive oltre al "copia e incolla" dei dati, come ad empio il denoising 
![[Pasted image 20250206182601.png]]

Un’applicazione tipica è il __denoising autoencoder__, che impara a ricostruire un’immagine originale da una versione rumorosa.
![[Pasted image 20250206182635.png]]