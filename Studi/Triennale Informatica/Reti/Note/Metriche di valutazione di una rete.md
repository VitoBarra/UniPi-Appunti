---
Course: "[[Reti]]"
tags:
  - RETI_LAB_III
topic: 
Status: ToReview
---

# Metriche di valutazione di una rete
---
 - _Larghezza di banda (Bandwidth)_:  larghezza dell’intervallo di frequenze utilizzato dal sistema trasmissivo. Si misura in Hertz (Hz – cycles per second) 
- _Velocità di trasmissione_ (bit rate o transmission rate):  quantità di dati (bits) che possono essere trasmessi (“inseriti nella linea”) nell'unità di tempo (bits/secondo or bps) su un certo collegamento 
	- _Bit rate_: dipende dalla larghezza di banda ma è influenzato anche da altri fattori (tecnica trasmissiva usata, rumore, ecc.)
- 
### Throughput
il Throughput è la quantità di dati che possono essere trasmessi con successo da un nodo sorgente a un nodo destinazione in un certo intervallo di tempo 
- Throughput indica la velocità con cui trasferiamo i dati, al netto di perdite sulla rete, duplicazioni, protocolli, ecc. 
- _Throughput_ < _transmission rate_
![[Pasted image 20221117201733.png]]
![[Pasted image 20221117201757.png]]
- _end-end Throughput_ per connessione: $min(R_c ,R_s ,R/n)$ 
- in pratica spesso $R_c$ o $R_s$ sono il collo di bottiglia (rete di accesso) 
>[!nota]
>- Il throughput dipende non solo dalla velocità di trasmissione del collegamento ma anche dalla quantità di dati (flussi di traffico aggiuntivi rispetto a quello di interesse), effetti dei protocolli, ecc…
![[Pasted image 20221117201859.png]]

## Latenza (Ritardo)
la _Latenza_ è il tempo richiesto affinché un messaggio arrivi a destinazione dal momento in cui il primo bit parte dalla sorgente. 

quando si verifica il ritardo nel caso della [[Tecniche di Commutazione#Commutazione di pacchetto| commutazione di pacchetto]]
- il tasso di arrivo dei pacchetti sul collegamento eccede la capacità del collegamento in uscita di evaderli
- i pacchetti si accodano, in attesa del proprio turno
![[Pasted image 20221117232909.png]]
#### Tipi di ritardo
1. $R_{acc} =$ _Ritardo di accodamento_
	 è il tempo in cui il pacchetto attende nella coda del router (dipende dalla congestione)
	- attesa di trasmissione
	- Dipende da intensità e tipo di traffico (che influiscono sul numero di pacchetti in coda nel buffer)
2. $R_{el} =$ _Ritardo di elaborazione del nodo_
	tempo per l’elaborazione al nodo intermedio (in genere pochi microsecondi, o anche meno)
	- controllo errori sui bit
	- determinazione del canale di uscita
3. $R_{tra} =$ _Ritardo di trasmissione = (L/R)_
	 Tempo impiegato per trasmettere un pacchetto sul link
	- R= rate (velocità) di trasmissione del collegamento (in bps)
	- L= lunghezza del pacchetto (in bit)
4. $R_{pr} =$ _Ritardo di propagazione = (d/s)_
	Tempo che serve a un bit per viaggiare da un punto A a un punto B sul mezzo trasmissivo. Dipende dalla distanza (valori tipici da pochi microsecondi a centinaia di millisecondi)
	 - Tempo impiegato da 1 bit per essere propagato da un nodo all’altro
	 - d = lunghezza del collegamento fisico
	 - s = velocità di propagazione del mezzo
![[Pasted image 20221117233413.png]]
il ritardo totale si calcola
$$R_{node} = R_{pr}+R_{tr}+R_{acc}+R_{el}$$
