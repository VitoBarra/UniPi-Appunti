---
Subject: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
Status: ToReview
---

Prev: [[Reti]]

# Tecniche di Commutazione
---
le tecniche di commutazione sono modalità con cui viene determinato il percorso sorgente-destinazione e vengono dedicate ad esso le risorse della [[Reti Concetti Generali|rete]]

## Commutazione di circuito
con questa metodologia si instaura un cammino dedicato (detto canale logico o circuito) tra due dispositivi che vogliono comunicare. su questo percorso vengono allocate delle risorse quali: 
- banda di frequenza o slot di trasmissione sui collegamenti
- capacita commutative nei nodi
queste risorse restano allocate fino alla fine della comunicazione

![[Pasted image 20221117192045.png]]



#### Divisione del mezzo comunicativo
- _Frequency Division Multiplexing (FDM)_
- frequenze ottiche, elettromagnetiche suddivise in bande di frequenza (strette). 
- Ad ogni comunicazione è assegnata una certa banda
![[Pasted image 20221117192548.png]]

_Time Division Multiplexing (TDM)_ 
- tempo suddiviso in slot i tempo 
- ogni comunicazione ha uno o più slot periodici assegnati 
- può trasmettere alla velocità massima di una banda di frequenza (più ampia), ma solo durante i suoi intervalli di tempo
![[Pasted image 20221117192615.png]]


- #### Contro
	- Necessaria una fase di instaurazione (setup) della comunicazione 
	- Le risorse rimangono inattive se non utilizzate siccome non c è condivisione
- #### PROs
	- Performance garantita
	- Tariffazione facile


## Commutazione di pacchetto 
con questa metodologia non si instaura nessuna connessione tra il mittene e destinatario della comunicazione e quindi si possono condividere le risorse.
 - il flusso di dati viene suddiviso in pacchetti 
 - ogni pacchetto è instradato singolarmente e in maniera indipendente dagli altri pacchetti
	 - il che significa che potrebbero fare lo stesso percorso o  percorsi diversi
 - le risorse vengono usate a seconda della necessita (minore spreco)
![[Pasted image 20221117195209.png]]
siccome le risorse sono condivisi ci potrebbe essere una contesa per l utilizzo di risorse. ad esempio in una rete del tipo:
![[Pasted image 20221117200136.png]]
ogni volta che si manda un pacchetto ma il mezzo trasmissivo non ha ulteriore capacita per mandare i pacchetti ciò che arriva si accoda nei buffer del router.  il che porta a congestione se i pachetti iniziano ad essere tanti e i buffer si possono riempire 

#### Problematiche
- _Ritardi di store and forward_ : Il commutatore (es. router) deve ricevere l’intero pacchetto prima di poter cominciare a trasmettere il primo bit del pacchetto sul collegamento in uscita
- _Ritardo di accodamento_: Attesa dei pacchetti in code di output (buffer)
- _Perdita di pacchetti_: succede se i buffer dei router o del destinatario sono pieni.
in generale si riescono a Sfruttare efficientemente le risorse ma le performance non sono garantite, ci potrebbero essere quindi dei ritardi

> [!note]
> ![[Pasted image 20221117200605.png]]
>La sequenza dei pacchetti A e B sul collegamento a 1,5 Mbps non segue uno schema prefissato si fa una  condivisione di risorse su richiesta (detta anche multiplexing statistico delle risorse)


>[!note]
>![[Pasted image 20221117201120.png]]

