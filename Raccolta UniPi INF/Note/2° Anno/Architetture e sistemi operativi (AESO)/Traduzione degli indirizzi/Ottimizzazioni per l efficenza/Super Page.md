# Super Page

le superpage sono un modo ottimizzare nel caso di blocchi contigui di memoria per ognuno delle pagine in questi blocchi bisognerebbe riempire una entry della TLB mentre con le superpage se ne può riempire una sola salvando tutto il blocco. quando non si è in questo caso si possono continuare ad usare le normali pagine.

le pagine nelle super pagine devono essere allineate  e adiacenti quindi una super pagina deve iniziare al inizio della prima pagine e finire alla fine del ultima pagina. ad esempio con blocchi da 2Kb una superpagina da due pagine sarà di 4Kb

 le superpagine complica la gestione della memoria siccome ora i blocchi sono di dimensione variabili ma utilizzarle riduce molto l unimero delle entry del TLB. per gestione delle superpage ognuna di questa ha un flag che indica se è una superpage o meno

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Traduzione degli indirizzi/Ottimizzazioni per l efficenza/Super Page/Untitled.png]]

nelle super page la dimensione del offset è variabile a seconda di quanta memoria si sta indirizzando ad esempio per superpage di 2Mb si usano 21 bit per 1Gb 30 bit
