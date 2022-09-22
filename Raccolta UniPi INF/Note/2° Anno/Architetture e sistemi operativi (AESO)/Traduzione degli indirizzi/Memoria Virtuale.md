# Memoria Virtuale

La virtualizzazione degli indirizzi permette ad un programma di lavorare come se tutta la memoria fosse a disposizione del processo infatti gli indirizzi utilizzati dal programma ora possono partire da un numero arbitrario e.s. 0 .

Invece il sistema operativo avrà bisogno di algoritmi per convertire gli [[indirizzi virtuali in indirizzi fisici]].

[[Astrazione_Kernel_2.png]]

Virtualizzare gli indirizzi risolve i problemi del metodo Base e bound siccome con questo sistema è possibile

- Riallocare in porzioni di memoria fisica più grandi i blocchi di memoria assegnati al programma mantenendo lo stesso indirizzo virtuale ma cambiando quello fisico cosi che possano crescere a seconda delle necessita del processo
- Gli indirizzi utilizzato dal processo sono sempre gli stessi
- Tutte le instanze di un programma daranno sempre lo stresso risultato se se va a stampare l indirizzo di una variabile. Questo a meno di Adress Randomization

<aside>
💡 **Adress Randomization**
L Adress Randomization è una piccola variazione degli indirizzi virtuali delle variabili tra istanza e istanza  dello v stesso programma. Questo è stato aggiunto perché avere la locazione virtuale di una variabile fissa rendere facile injectare codice malevolo in quelle variabili, ad esempio in una stringa può essere scritto del codice

</aside>

[[Base e Bound]]

[[Memoria Segmentata]]

[[Memoria Paginata]]

[[Memoria Segmentata paginata]]

[[Memoria Paginata su più livelli]]

[[Memoria Paginata su più livelli segmentata]]
