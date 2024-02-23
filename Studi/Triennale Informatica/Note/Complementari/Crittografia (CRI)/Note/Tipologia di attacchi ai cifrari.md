---
Subject: Crittografia
topic: nota
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Tipologia di attacchi ai cifrari
---
gli attacchi di un crittoanalista ad un certo cifrario possono essere di più tipi e dipende dal intenzione del attacco. 

alcune tipologie tipologie sono:
- _Cipher Text Attack_: Semplice rilevazione di una serie $c_1,\dots,c_n$ crittogrammi
- _Known Plain-Text Attack_: sono state rilevate una serie di coppie $(m_1,c_1)\dots, (m_n,c_n)$ ovvero il testo in chiaro e il relativo crittogramma
- _Chosen Plain-Text Attack_: sono state rilevate una serie di coppie $(m_1,c_1)\dots, (m_n,c_n)$ ovvero il testo in chiaro e il relativo crittogramma ma il critto analista ha scelto i messaggi in chiaro


### attacco Man in the midle
l attacco _Man in-the-middle_ avviene come 
	viene interrotta la comunicazione diretta tra i due interlocutori e un terzo agente appunto in mezzo riceve e manda i messaggi che dovrebbero viaggiare direttamente , questo permetterebbe alla persona in mezzo di modificare quel messaggio o anche solo di leggerli a seconda delle intenzioni del attacco

in generale un attacco di questo tipo  viene fatto su [[Cifrari a chiave Asimmetrica|Cifrari a chiave Asimmetrica]] e avviene secondo il seguente schema generale:
1. $U$ richiede a $V$ la sua _chiave pubblica_
2. un utente $X$ intercetta la risposta contenente $k_{V}[pub]$ e la sostituisce con la sua _chiave pubblica_ $k_{X}[pub]$
3. Da questo momento in poi $X$ si pone costantemente in ascolto inattesa dei crittogrammi spediti da $U$ a $V$ e _cifrati mediante_ $k[pub]$. Ciascuno di questi crittogrammi viene rimosso dal canale e poi $X$ le  _decifrara_ e lo _cifrera_ di nuovo mediante $k_{V}[pub]$ e spedira il nuovo crittogramma a $V$
questo procedimento è completamente trasparente a $U$ e $V$ finche il ritardo introdotto da $X$ è abbastanza basso da essere attribuito alla rete.


	


>[!note] maquillage editoriale
>serve a nascondere le struttore del linguaggio naturale per dare meno informazioni al critto analista es. rimuovere spazi, accetti e punteggiatura e aggiunta di inregolarita nella struttura


