---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# Consensus docking
---
Il **consensus [[Docking|docking]]** è un approccio utilizzato durante il [[Virtual screeaning|virtual screening]] receptor-based per aumentare l’affidabilità delle **pose predette**. Poiché i diversi [[Docking|software di docking]] adottano algoritmi di ricerca e funzioni di scoring differenti, lo stesso ligando può generare risultati discordanti a seconda del programma impiegato. Il **consensus docking** affronta questa variabilità combinando più docking indipendenti sullo stesso sistema.  
![[IMG - Consensus docking.png]]
In questo approccio, ciascun ligando viene dockato utilizzando diversi software e le pose ottenute vengono confrontate tramite misure geometriche, in particolare la RMSD. Due pose sono considerate equivalenti quando la RMSD reciproca è inferiore a una soglia tipicamente pari a $2\text{Å}$. Il **livello di consenso** è definito come il numero di programmi che convergono sulla stessa modalità di legame: un consenso basso indica alta incertezza, mentre un consenso elevato suggerisce una posa più robusta e una maggiore probabilità che il ligando sia effettivamente attivo sul bersaglio.  
![[IMG - consensus docking lvl 1.png]]  
![[IMG - Consensus docking lvl 5.png]]  
![[IMG - consensus docking lvl 10.png]]
