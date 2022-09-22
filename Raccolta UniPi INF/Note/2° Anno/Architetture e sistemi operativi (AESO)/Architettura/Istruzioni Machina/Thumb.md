# Thumb

Le istruzioni Thumb sono lunghe 16 bit per aumentare la densità del codice
macchina; sono identiche alle normali istruzioni ARM ma con alcune limitazioni in quanto:

- possono accedere solo ai primi otto registri;
- utilizzano un registro sia come sorgente sia come destinazione;
- gestiscono solo immediati più corti;
- non dispongono dell’esecuzione condizionata;
- modificano sempre le flag di stato.
