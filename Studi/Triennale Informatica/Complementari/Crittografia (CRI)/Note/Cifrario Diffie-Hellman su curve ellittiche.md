---
Subject: Crittografia
topic: nota
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrario Diffie-Hellman su curve ellittiche
---
è un tipo di _[[Cifrari ibridi|cifrario ibrido]]_  che si basa sul funzionamento del [[Cifrario Diffie-Hellman (DH)|cifrario Diffi-Hellman]]  ma invece di utilizzare le proprietà del [[Algebra modulare|algebra modulare]] utilizza le proprietà delle [[Curve Ellittiche|curve ellittiche]]


Come succede nei cifrari ibridi i due utenti _Alice_ e _bob_ vogliono scambiarsi una _chiave di sessione_ $K[Session]$  utilizzando _[[Cifrari a chiave Asimmetrica|chiave assimetrica]]_ per  poterla utilizzare per lo scambio di messaggi con [[Cifrari a chiave Simmetrica|cifrario simmetrici]]

### Protocollo
1. _Alice_ e _bob_ si accordano _pubblicamente_ su un [[Curve Ellittiche|curva ellittica]] a [[Campi|campo finito]]  e una [[Curve Ellittiche|curve ellittiche]] e su un punto $B$ sulla curva con _[[Curve Ellittiche#ordine di un punto|ordine del punto]]_ $n$ del punto $B$ molto alto
2. _Alice_ genera un [[Generatori di numeri Pseudo Casuali|intero positivo casuale]] $n_{A} < n$,e genera la chiave _pubblica_ $P_{A}=n_{A}B$ che viene spedita in chiaro ad _Bob_
3. _Bob_ genera un [[Generatori di numeri Pseudo Casuali|intero positivo casuale]] $n_{B} < n$, e genera la chiave _pubblica_ $P_{B}=n_{B}B$ che viene spedita in chiaro ad _Alice_
4. _Alice_ riceve $P_{B}$ e calcola $n_{A}P_{B}=n_{A}n_{B}B=S$, dove $S$  è un punto della curva
5. _Bob_ riceve $P_{A}$ e calcola $n_{B}P_{A}=n_{B}n_{A}B=S$, dove $S$ è lo stesso punto calcolato da _Alice_
6. A questo punto _Alice_ e _Bob_ condividono lo stesso punto $S=(x_{S},y_{S})$ e per poterlo usare come _chiave di sessione_ il punto va trasformato in un numero intero. questo avviene tramite la formula$$k = x_{S}\mod  2^{256}$$ ovvero $k$ è costituito da gli ultimi 256 bit del ascisse di $S$
 
### Sicurezza di DH su curva ellittica
Un crittoanalista per violare il cifrario deve calcolare $S$ a partire da $P_{A},P_{B},B$ e per fare ciò ha bisogno di calcolare o $n_{A}$ o $n_{B}$ e per fare ciò deve risolvere il [[Problema del logaritmi discreto su curve ellittiche|problema del logaritmi discreto su curve ellittiche]] che è una [[Funzioni One-Way|Funzioni One-Way]] ma ciò non rende di perse il cifrario totalmente sicuro siccome come per il normale protocollo [[Cifrario Diffie-Hellman (DH)|Diffie-Hellman]] anche il protocollo _Diffi-Hellman su curve ellittiche_ è soggetto ad attacchi [[Tipologia di attacchi ai cifrari|man-in-the-midle]]
