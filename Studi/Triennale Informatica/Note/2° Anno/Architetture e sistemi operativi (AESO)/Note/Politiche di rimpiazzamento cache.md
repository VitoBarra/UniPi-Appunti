---
Subject: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Politiche di rimpiazzamento cache
---

Una della problematiche delle [[Memory Cache lookup|cache]] è gestire quale pagina sostituire questa scelta non deve essere troppo costosa perché impiegare troppo tempo nella scelta distrugge lo scopo delle cache stessa

## Random

si sceglie random la pagina da sostituire in contesti in cui la scelta può essere molto costosa è ottimo anche se banale.

il suo grande svantaggio e che essendo imprevedibile con questa politica non funzionano i programmi che fanno vantaggio della gestione della cache

 ## FiFo

è spesso una politica pessima siccome un caso comune dei programmi è accedere ripetutamente ad un array. con questa politica può capitare che faccia la peggiore scelta possibile ovvero scegliere come pagina da sostituire quello che servirà subito dopo

![[Studi/Triennale Informatica/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled.png]]

## Min: sostituzione ottima della cache

questa é una politica che si basa sullo scegliere la pagina che servirà più in la nel futuro. questa politica è sempre ottima ma è puramente teorica siccome per realizzarla bisognerebbe conoscere il futuro

## Last Recently used (LRU)

è una politica in cui si sceglie di sostituire la pagina che è stato usato più indietro nel tempo, utilizza questa strategia sulla base della località temporale. cerca di approssimare MIN. purtroppo in hardware non è facile da realizzare

![[Studi/Triennale Informatica/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 1.png]]

ci sono dei casi in cui LRU si comporta come una FIFO  ad esempio lo scan ripetuto di un aria di memoria. questo è il caso peggiore, invece la strategia ottimale sarebbe di scegliere quello piu recentemente usato

## Least Frequently Used (LFU)

una politica che sceglie come pagina da sostituire quella meno frequentemente usato. questo è particolarmente funzionale quando si è nel contesto di una zipf distribution

## Not Recently Userd (NRU) o k’th Chance

una politica che approssima LRU e sceglie la pagina in base a se il contatore di quella pagina supera K cosi facendo lo elimina solo dopo k iterazioni del algorismo del orologio

### Algoritmo del orologio

il sistema operativo ispeziona tutte le pagine della core map ad intervalli regolari se il bit di utilizzo è settato allora un contatore per quella pagina va a 0 altrimenti viene incrementato

![[Studi/Triennale Informatica/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 2.png]]

per core map molto grandi ha un considerevole overhead quindi si deve regolare bene la frequenza di lancio di questo algoritmo

---

## Belady’s anomaly

la anomalia di belady si riferisce al fatto che aggiungere blocchi memoria cache dovrebbe migliorare l hit rate di questa o quanto meno non farla peggiorare. questo è vero per l LRU e LFU ma ma non lo è per la FIFO. aggiungere uno slot potrebbe portare ad avere un hit rate più basso



![[Studi/Triennale Informatica/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 3.png]]
