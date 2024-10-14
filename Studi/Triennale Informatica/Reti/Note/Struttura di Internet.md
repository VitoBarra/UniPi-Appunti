---
Subject: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
Status: ToReview
---

Prev: [[Reti]]

# Struttura di Internet
---
Internet è un interconnessione di [[Reti Concetti Generali|reti]] è siccome si parla di grandi numeri di reti bisogna trovare un modo intelligente per connetterle facendo si che ogni dispositivo terminale possa mandare informazioni a qualsiasi altro dispositivo.

ogni host si connette ad un _Internet Service Provider_ (ISP) ovvero un gestore della connessione 
- questo può essere: aziendale,residenzialo ecc

per vanno perciò connessi più ISP per ottenere la connessione di tutte le reti: 
un modo sbagliato di gestire queste connessione é costruire connessioni dirette 
![[Pasted image 20221117183315.png]]
siccome abbiamo risorse limitate  la cosa non funziona per grandi numeri di ISP.
il modo corretto è di avere un ISP globale che connette le varie reti.
![[Pasted image 20221117183157.png]]
queste sono gestite con un accordo economico tra l ISP globale e l' ISP clienti e siccome è un attività economica esistono molteplici ISP Globali che vanno messi in comunicazione. 
per fare ce si utilizzano i
- _Peering link_: accordo tra due ISP di accettare e inoltrare il traffico che ricevono dall’altro
- _IXP_: internet eXchange Point: punto d’incontro (può essere gestito da un’azienda terza) per il peering tra due o più ISP
![[Pasted image 20221117183631.png]]
questa infrastruttura può essere complicata a piacere con ISP regionali e di content. questa complicazione aggiunge strati ma non i concetti di base restano gli stessi
![[Pasted image 20221117184857.png]]
![[Pasted image 20221117185234.png]]
quindi la struttura genere ritrova al _centro_ delle reti molto connesse: 
- Tier-1 ISP commerciali, che hanno copertura nazionale e internazionale
- e content provider network: che sono reti private che collegano i lori data center a internet anche by-passando ISP Tier-1 e regionali
E ai _margini_:
- ISP regionali: che aree più piccole 
- ISP access: ovvero tutte le connessioni di piccole dimensioni come una casa un ufficio 
