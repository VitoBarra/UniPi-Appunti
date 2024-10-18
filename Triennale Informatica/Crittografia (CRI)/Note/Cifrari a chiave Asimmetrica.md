---
Course: Crittografia
topic: nota
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrari a chiave Asimmetrica
---
In generale sono un paradigma completamente diverso rispetto ai [[Cifrari a chiave Simmetrica|Cifrari a chiave Simmetrica]]  
i cifrari a chiave asimmetrica sono chiamati cosi proprio per l asimmetrica che hanno i due ruoli di _mit_ e _dest_.
abbiamo che la chiave di _cifratura_ è completamente diversa da quella di _decifratura_ infatti abbiamo 
- _chiave pubblica_ $k[pub]$ usata per la _cifratura_
- _chiave privata_ $k[prv]$usata per la _decifratura_
la _chiave pubblica_ è nota a tutti ed è associato ad un solo utente, tutti possono usare questa chiave per crittografare un messaggio ma solo chi ha la _chiave privata_ associata potrà decrittarlo. di fatto abbiamo che la chiave è $k=\langle k[pub],k[prv]\rangle$
le funzioni di [[Cifratura e Decifratura|Cifratura e Decifratura]] sono strutturate come
$$
\begin{array}
\mathcal{C}(m,k[pub])  & = &  c \\
\mathcal{D}(c,k[prv])  & = &  m
\end{array}
$$

questi classe di cifrari devono soddisfare le seguenti proprietà
1. Per ogni possibile messaggio $m$ si ha: $\mathcal{D}(\mathcal{C}(m, k[pub]), k[prv]) = m$. Ossia _Dest_ deve avere la possibilità di interpretare qualunque messaggio che gli altri utenti decidano di spedirgli. 
2.  La sicurezza e l’efficienza del sistema dipendono dalle funzioni $\mathcal{C}$ e $\mathcal{D}$, e dalla relazione che esiste tra le chiavi $k[prv]$ e $k[pub]$ di ogni coppia. Piu esattamente: 
	1. a) la coppia $k[prv]$, $k[pub]$ è _facile_ da generare, e deve risultare praticamente impossibile che due utenti scelgano la _stessa chiave_
	2. b) dati $m$ e $k[pub]$, è _facile per il mittente_ calcolare il crittogramma $\mathcal{C}(m, k[pub]) = c$;
	3. c) dati $c$ e $k[prv]$, è _facile per il destinatario_ calcolare il messaggio originale $\mathcal{D}(c, k[prv]) = m$;
	4. d) pur conoscendo il crittogramma $c$, la chiave pubblica $k[pub]$, e le funzioni  $\mathcal{C}$ e $\mathcal{D}$, _é difficile per un crittoanalista_ risalire al messaggio $m$.

le funzioni $\mathcal{C}$ per avere le prosperità sopra elencate devono essere di tipo [[Funzioni One-Way Trapdoor|One-Way Trapdoor]]. Ovvero facilmente calcolabili e difficilmente invertibili ameno che non si ha un informazione in piu. in questo caso la $k[prv]$




### Vulnerabilita
il sistema è sensibile ad attacchi [[Tipologia di attacchi ai cifrari|chosen plain-text]] siccome un critto analista puo scegliere una serie di messaggi $m_{1},\dots,m_{n}$ e crittarli per la chiave $k[pub]$ ottenendo i $c_{1},\dots,c_{n}$ per in destinatario $dest$ 
se passa sul canale un messaggio cifrato $c^{*}$ e si ha che $c^{*}=c_{i}  \implies \mathcal{D}(c_{i})=m_{i}$ ed il messaggio è _automaticamente decifrato_.
se invece si ha $c^{*}\not =c_{i}$ il crittoanalista ha comunque un informazione in piu ovvero che il messaggio non è uno di quelli scelti.
questo attacco è particolarmente pericoloso se il critto analista si aspetta un messaggio specifico o se la struttura del messaggi è conosciuta. es indirizzo IP.

