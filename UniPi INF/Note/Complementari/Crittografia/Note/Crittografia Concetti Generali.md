---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Crittografia Concetti Generali
---

## Perchè Esiste
”Crittografia” etimologicamente significa messaggio nascosto e nasce dalla necessita del umano di poter scambiare dei messaggi privatamente. Questa necessita nasce con l invenzione della scrittura che già inizialmente era una cosa per pochi. Questa necessita nasce dalla presenza di persone con l obbiettivo opposto ovvero quello di impicciarsi delle comunicazioni altrui. Questa contrapposizione di necessita fa nascere la __crittografia__ che si occupa di  occultare il messaggio e la _crittoanalisi_ che si occupa di risalire al messaggio dal [[crittogramma]]. 

>[!nota] 
> Tra i due ruoli non c è una connotazione di buono o cattivo dipende da cosa se ne sta facendo di questa tecnologia.

## Su cosa si base per funzionare
La crittografia a senso se i messaggi scritti sotto forma di crittogrammi generati dal algoritmo di crittografia sono difficilmente ricavabili dagli agenti non destinatari del messaggio, va pero tenuto in considerazione la praticità del algoritmo. In particolare criptare un messaggio deve essere molto veloce per chi deve inviarlo e la decrittazione deve essere molto veloce per chi deve riceverlo e  __molto__ lenta per chi cerca di intercettare quel messaggio. 
Esistono algoritmi di crittazione che generano crittogrammi da cui è matematicamente impossibile ricavare il messaggio originale ma questi algoritmi sono impratichì siccome ci vorrebbe troppo tempo a fare la crittazione del messaggio questi vengono usati in casi molto estremi  di solito militari e quindi non di massa.

La _Crittografia moderna_ si basa sulla crittazione e la decrittazione di un messaggio basato su chiave. Chi possiede la chiave riesce a fare queste due cose in [[Complessita| tempo Polinomiale]]  mentre a chi non ha accesso alla chiave per decrittografare il crittogramma è richiesto di risolvere un problema di [[Complessita|complessità esponenziale]] facendo cosi la decrittazione richiederebbe anche milioni di anni rendendo cosi inutile ricavare l informazione di quel messaggio.

A oggi le tecnologie che abbiamo si basano su questo principio pero tutto ciò è basato sulla [[Congettura P diverso da NP|congettura]] che $P \not = NP$ se questo non dovesse essere il caso allora i problemi richiesti per la de-crittografazione senza chiede passerebbero da essere esponenziali a polinomiali distruggendo tutto ciò su cui si basa la crittografia  

### Metodo publico
nella crittografia moderna non si nasconde il metodo del cifrario ma si tiene segreta solo la chiave