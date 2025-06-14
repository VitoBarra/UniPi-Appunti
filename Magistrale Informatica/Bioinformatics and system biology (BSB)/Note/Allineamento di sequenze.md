---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Allineamento di sequenze
---
L’**allineamento di sequenze** è una procedura computazionale utilizzata per [[Confronto tra sequenze|confrontare]] due o più [[stringhe|stringhe]] simboliche mediante una **disposizione relativa** che preserva l’ordine dei simboli.  l’allineamento introduce una **corrispondenza esplicita** tra le **posizioni delle sequenze considerate**, ammettendo mismatch o  l’inserimento di spazi vuoti (*gap*) al fine di compensare differenze di lunghezza. Ogni possibile disposizione relativa delle sequenze definisce un allineamento valido, che può essere valutato e confrontato con altri.

In base alle ipotesi sul tipo di relazione tra le sequenze, si distinguono due principali modelli concettuali di allineamento:
- l’**allineamento globale**, in cui l’intera lunghezza delle sequenze viene considerata nel confronto;
- l’**allineamento locale**, in cui si ricerca la migliore corrispondenza tra sottosequenze contigue.

Il problema di trovare l'allineamento migliore puo essere formulato **[[Problemi di ottimizzazione|problema di ottimizzazione]]**. Dato l’insieme di tutti i possibili allineamenti ottenuti introducendo gap in posizioni diverse, a ciascun allineamento viene associato un valore numerico, definito da una **funzione obiettivo**. L’allineamento ottimale è quello che massimizza tale valore o, in modo equivalente, minimizza una misura di [[Definizione di distanza|distanza]]. La funzione obiettivo è tipicamente **additiva** e valuta un allineamento come la somma dei contributi associati alle singole colonne. Tali contributi dipendono dalla corrispondenza tra simboli allineati e dalla presenza di gap. In questo modo, il valore complessivo dell’allineamento emerge dalla combinazione di decisioni locali coerenti.

Un elemento centrale dell’allineamento è la definizione di una **misura di similarità** tra simboli. Nei contesti in cui i simboli possiedono proprietà eterogenee, la sostituzione tra simboli diversi non è uniforme e richiede un modello di valutazione differenziato. In tali casi, la similarità viene espressa mediante schemi di punteggio che assegnano valori diversi alle diverse corrispondenze.

Un ulteriore aspetto fondamentale è il trattamento dei **gap**. L’introduzione di gap consente di modellare inserzioni e cancellazioni, ma richiede l’applicazione di penalità che ne limitino l’uso arbitrario. Il modello di penalizzazione dei gap influisce in modo significativo sulla struttura dell’allineamento risultante e sull’interpretazione del confronto.