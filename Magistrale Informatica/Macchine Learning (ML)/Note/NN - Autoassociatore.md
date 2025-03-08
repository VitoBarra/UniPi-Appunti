---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Reti neurali - Autoassociatore
---
Gli __autoassociatori__ sono una classe di [[Reti Neurali (NN)|reti neurali]] che memorizzano e recuperano pattern associativi, rendendoli robusti a rumore e distorsioni. Apprende a riprodurre il proprio input, il modello si specializza nel recupero di pattern, anche se l input è corrotti o parziale e sono solitamente allenati tramite tecniche [[Algoritmi di learning NON supervisionato|NON supervisionate]]

Gli __autoassociatori__ possono essere definiti da una funzione di associazione $f$, dove un dato input  $x$ viene mappato in un output $r$, cercando di minimizzare la distanza tra i pattern memorizzati e quelli ricostruiti.  

Gli __autoassociatori__ sono solitamente di due tipi:  
- __[[Hopfield Networks|Reti di Hopfield]]__: una rete completamente connessa con pesi simmetrici, in grado di memorizzare un numero limitato di pattern stabili.  
- __Memorie associativa di Kanerva__: utilizza una rappresentazione distribuita per memorizzare e recuperare informazioni.  
- [[NN - Autoencoders|Autoencoders]]: reti neurali con una struttura __encoder-decoder__.
