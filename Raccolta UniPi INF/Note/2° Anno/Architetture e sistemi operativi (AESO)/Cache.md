---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Cache
---


Le cache sono un punto chiave per rendere i sistemi informatici  veloci e con loro riporgono tre problematiche da tenere in conto

- **Trovare la copia sulla cache** :  siccome lo scopo della cache e velocizzare l accesso il tempo
- **Pollicy di rimpiazzamento**: quando un nuovo dato deve entrare nella cache va scelto in [[Politiche di rimpiazzamento cache|modo efficiente cosa rimpiazzare]] dalla cache
- **Coerenza**: Controllare quando i dati salvati sono nella cache sono out-date

### Concetti cache

![[8CB06F0A-8BA3-4928-B22C-6F3ADA30C1FE.jpeg]]

Una cache è una memoria che mantiene una coppia di valori con il primo si raggiunge il secondo valore della coppia fa in pratica da dizionario.

 Se al momento della ricerca il dato si trova allora è un __cache hit__  altrimenti si chiama __cache miss__

Stimare quali dati è probabile che vengano riusati è un concetto fondamentale per poter decidere cosa sostituire nella cache. Due concetti per questo sono

- **Località temporale**: la località temporale si riferisce ad i processi che tendono ad riutilizzare spesso la memoria che hanno da poco richiamato come in un ciclo o in una struttura dati utilizzata spesso
- **Località Spaziale**:  la località spaziale si riferisce alla tendenza dei processi ad accedere a memoria vicina a quella a cui se appena fatto l accesso infatti uno le cache sono disegnate per prendere blocchi interi di dati e non la singola istruzione
    - Un altra delle tecniche per utilizzare questo fatto è fare prefeth ovvero il processore carica dati contigui a quelli appena richiesti anche se non gli è stato ancora chiesto

Con tutto questo la latenza d accesso  in lettura diventa

$$
Latency(read \ request ) = Prob(cache \ hit ) \times Latency(cache \ hit) + Prob(cache \ miss ) \times Latency(cache \ miss)
$$

In scrittura  in una cache  è più semplice perché essendo bafferizata appare al programma immediata

![[4CEF1162-8B0A-45E3-A0BB-40BA2E10201D.jpeg]]

 il suo funzionamento è:

- ad una richiesta di scrittura carica il dato nel buffer e fai perseguire l esecuzione
- I background quando se vuole eseguire la scrittura il processore controlla se l indirizzo da scrivere è nella memoria se lo è lo aggiorna direttamente altrimenti prima lo fetcha
- Una volta scritto vanno aggiornati gli altri livelli di cache questo si può fare in due modi
    - Write-Throught: ovvero appena viene aggiornato viene fatto anche negli altri livelli
    - Write-back: quando il dato viene eliminato prima viene scritto aggiornato negli altri livelli della cache

[[Memory Cache lookup]]


