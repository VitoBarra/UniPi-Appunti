---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Critto analisi Statistica
---
la critto analisi statistica si basa su delle proprietà del linguaggio naturale come la frequenza delle _lettere_ dei _digrammi_, _trigrammi_ e sono dei gruppi di lettere che solitamente stanno assieme.
questo sono detti q-grammi perché crescono come $26^{q}$
![[Pasted image 20230705174154.png]]

i [[Cifrari storici|Cifrari storici]] sono stati tutti attaccati con la critto _analisi statistica_ tramite attacchi [[Tipologia di attacchi ai cifrari|cipher test]] 

e sotto l assunzione che il messaggio sia abbastanza lungo per fare _crittoanalisi statistica_ si puo ragionare per [[Classificazione di cifrari|famiglie di classificazione]]


#### su cifrari monoalfabetici
nei cifrari mono alfabetici abbiamo che dato un messaggio $m$ e una sostituzione di una lettera $x$ con una $y$ abbiamo che non cambiano le frequenze delle lettere ma cambia di quale lettere nello specifico

per [[Cifrario di Cesare]] infrangerlo è facilissimo basta trovare una solo coppia $\langle x,y\rangle$ ed il messaggio è violato
per [[Cifrario affine e cifrari completo|cifrario affine]] e leggermente piu complesso bisogna trovare due coppie e mettere a sistema la distanza
per il [[Cifrario affine e cifrari completo#Cifrario completo|cifrario completo]] restano uguali le distribuzioni e si usano quelle per fare le associazioni, bisogna pero fare un po' di tentativi per le lettere con distribuzione simile.


#### su cifrari polialfabetici
i cifrari _polialfabetici_ cambiano la distribuzione delle lettere rendendo piu difficile la critto analisi. 

per il [[Cifrario di Vigenere|Cifrario di Vigenere]] osservando il fatto che la chiave viene ripetuta e che se conosco la lunghezza $h$ della chiave in quella porzione la crittografia e monoalfabetica
sapendo che ci sono dei q-grammi e parole ripetute posso riuscire a trovare coppie di porzioni identiche. 
_Siano_ $p_{1}, p_{2}$ la posizione in cui iniziano le sotto sequenza identiche abbiamo che la distanza $d=p_{2}-p_{1}$ è la lunghezza $h$ della chiave. sapendo questo si puo procedere con l analisi _monoalfabetica_ dei blocchi di dimensione $h$.

se ci sono piu distanze $d',d'',\dots$ la lunghezza $h$ deve essere un loro divisore comune.

per [[Cifrario di Alberti|alberti]] questo discorso non vale se si cambia chiave spesso e senza fare pattern ripetitivi

#### Cifrari a trasposizione
Questi mantenendo le stesse lettere del messaggi in lingua naturale non alterano ne la distribuzione ne la lettere associate quindi potrebbe sembrare inutile un _approccio statistico_.

per il [[Cifrario a permutazione semplice|permutazione semplice]] dallo studio dei q-grammi abbiamo che certe lettere devo stare necessariamente nello stesso _blocco del crittogramma_ o al massimo in quelli adiacenti.
Se si riescono ad individuare questi q-grammi si puo risalire facilmente alla porzione della chiave che li ha permutati e se se ne trovano abbastanza al intera chiave, si prova con valori plausibili.
procedimenti simili valgono per [[Cifrario a permutazione di colonna|cifrario a permutazione di colonna]] e per[[Cifrario a griglia|cifrari a griglia]].

#### Capire il tipo di cifrario
con la _critto analisi statistica_ abbiamo anche dei potenti strumenti per capire di che [[Classificazione di cifrari|tipo]] è il cifrario solo dalla distribuzione delle lettere nel crittogramma

infatti abbiamo che rispetto al [[Statistica descrittiva#Grafici|istogramma]] delle distribuzione delle lettere in linguaggio naturale l _istogramma_  delle lettere in cifrari a
- _trasposizione_  coincide
- _sostituzione monoalfabetico_ l istogramma coincide a meno di permutazioni delle lettere
- _sostituzione polialfabetica_ l istogramma è assai piu appiattito.