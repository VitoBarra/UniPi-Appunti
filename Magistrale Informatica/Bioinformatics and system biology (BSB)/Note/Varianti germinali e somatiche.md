---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
  - AIGenerated
Area:
topic: Genomics
SubTopic: Genetic variants
---

# Varianti germinali e somatiche
---
Una **variante genetica** è una differenza di sequenza rispetto a una sequenza di riferimento. Una variante può essere germinale o somatica in base al momento e al tipo di cellula in cui è presente.

È importante distinguere il [[Gene|gene]] dalla variante: tutti gli individui ereditano normalmente geni come `BRCA1`, `RB1` o `MSH2`, mentre soltanto alcuni individui possiedono una specifica variante patogenetica in quei geni.

## Varianti germinali

Una **variante germinale** è presente nella cellula uovo o nello spermatozoo da cui si sviluppa l'individuo, oppure compare nelle primissime divisioni embrionali. Di conseguenza, è normalmente presente in quasi tutte le cellule dell'organismo.

Può essere:
- ereditata da uno dei genitori;
- **de novo**, se compare per la prima volta in un gamete o durante le prime fasi dello sviluppo.

Una variante germinale può essere trasmessa ai figli. Quando è patogenetica, può determinare una predisposizione ereditaria a una malattia, ma non implica necessariamente che la malattia si manifesterà.

```text
Variante nel gamete
        ↓
Presente dalla formazione dello zigote
        ↓
Presente in quasi tutte le cellule
        ↓
Potenzialmente trasmissibile ai figli
```

## Varianti somatiche

Una **variante somatica** viene acquisita dopo la formazione dello zigote. È presente soltanto nella cellula in cui si origina e nelle cellule che da essa discendono.

Le varianti somatiche:
- non sono normalmente presenti in tutte le cellule;
- possono formare un mosaico di popolazioni cellulari differenti;
- non sono normalmente trasmesse ai figli;
- possono contribuire allo sviluppo e all'evoluzione clonale di un tumore.

```text
Cellula inizialmente normale
        ↓
Comparsa di una variante durante la vita
        ↓
Espansione della cellula e dei suoi discendenti
        ↓
Variante presente soltanto in una parte dell'organismo
```

## Confronto

| Caratteristica | Variante germinale | Variante somatica |
|---|---|---|
| Momento di origine | Prima del concepimento o nelle primissime fasi embrionali | Dopo il concepimento |
| Distribuzione | Quasi tutte le cellule | Un sottoinsieme di cellule |
| Trasmissione ai figli | Possibile | Normalmente assente |
| Campione di rilevazione | DNA non tumorale, per esempio sangue o saliva | Confronto tra tumore e tessuto normale |
| Ruolo oncologico | Predisposizione ereditaria | Sviluppo ed evoluzione del tumore |

## Confronto con il genoma di riferimento

Il [[Genoma di riferimento|genoma di riferimento]] fornisce coordinate comuni e una sequenza di base rispetto alla quale individuare differenze:

```text
Sequenza di riferimento: ... A C G T C ...
Sequenza del campione:    ... A C A T C ...
                                  ↑
                             differenza
```

Una differenza rispetto al riferimento non è automaticamente una mutazione patogenetica. Ogni individuo possiede milioni di varianti, molte delle quali sono comuni o prive di conseguenze cliniche.

Il riferimento mostra un solo allele principale per posizione. L'allele diverso viene indicato come alternativo, ma puo' essere comune nella popolazione e non rappresenta necessariamente una mutazione comparsa nel campione. Le combinazioni di varianti ereditate sulla stessa copia cromosomica sono descritte dagli [[Aplotipo|aplotipi]].

## Identificazione di varianti somatiche

Per distinguere le varianti somatiche da quelle ereditate è preferibile confrontare il DNA tumorale con DNA normale dello stesso individuo:

```text
Genoma di riferimento
        ↓
DNA normale del paziente
→ identifica il patrimonio genetico individuale
        ↓
DNA tumorale confrontato con il DNA normale
→ identifica le differenze candidate come somatiche
```

Una variante presente sia nel campione normale sia nel tumore è compatibile con un'origine germinale. Una variante osservata nel tumore ma assente nel campione normale è candidata come somatica. La distinzione richiede anche controlli di qualità, profondità di sequenziamento e valutazione della composizione cellulare del campione.

## Interpretazione clinica

L'identificazione di una differenza di sequenza e la sua interpretazione sono due passaggi distinti. Le varianti possono essere classificate come:
- benigne;
- probabilmente benigne;
- di significato incerto;
- probabilmente patogenetiche;
- patogenetiche.

La classificazione può integrare frequenza nella popolazione, dati funzionali, segregazione familiare, evidenze cliniche e letteratura scientifica.

## Ipotesi dei due colpi

Per molti geni oncosoppressori, una variante germinale patogenetica può costituire un primo evento predisponente. Una successiva alterazione somatica della copia ancora funzionale può costituire il secondo evento necessario alla perdita della funzione:

```text
Primo allele alterato nella linea germinale
                    +
Secondo allele alterato somaticamente
                    ↓
Perdita della funzione oncosoppressiva
```

Questo modello è noto come **ipotesi dei due colpi** (*two-hit hypothesis*). Non descrive tutti i geni o tutti i tumori, ma è un modello centrale della genetica dei tumori.

## Relazione con le banche dati oncologiche

Risorse come [[COSMIC Cancer Gene Census]] raccolgono conoscenze generali su geni e varianti osservati in molti studi e pazienti. Un'annotazione che indica coinvolgimento germinale o somatico non significa automaticamente che la stessa alterazione sia presente in uno specifico paziente: indica che tale tipo di coinvolgimento è documentato nella letteratura e nelle fonti integrate.

Vedi anche: [[Genomics]], [[Genoma]], [[Genoma di riferimento]], [[Aplotipo]], [[Gene]], [[COSMIC Cancer Gene Census]].
