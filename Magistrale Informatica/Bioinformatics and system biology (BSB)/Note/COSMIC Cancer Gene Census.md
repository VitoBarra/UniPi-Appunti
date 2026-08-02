---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic: Biological databases
SubTopic: Cancer genomics
---

# COSMIC Cancer Gene Census
---
Il **COSMIC Cancer Gene Census** (CGC) è una risorsa curata che raccoglie geni per i quali esistono evidenze del coinvolgimento causale nello sviluppo del cancro. Fa parte di **COSMIC** (*Catalogue Of Somatic Mutations In Cancer*), una [[Banche dati biologiche|banca dati biologica]] dedicata alle alterazioni genomiche osservate nei tumori.

Il Cancer Gene Census non rappresenta l'analisi di un singolo paziente o di un singolo esperimento. Integra conoscenze provenienti da letteratura scientifica, studi oncologici e annotazioni curate.

## Informazioni associate ai geni

Per un gene oncologico possono essere riportate informazioni quali:
- simbolo e identificatori del gene;
- coinvolgimento somatico o germinale;
- tipi di tumore associati;
- ruolo come oncogene o gene oncosoppressore;
- tipi di alterazione;
- sindromi tumorali ereditarie;
- partner di traslocazione;
- sinonimi e identificatori alternativi.

## Somatico e germinale

Le annotazioni **somatic** e **germline** indicano che il coinvolgimento del gene attraverso quel tipo di variante è stato documentato in ambito oncologico:
- **somatic**: alterazioni acquisite in cellule tumorali;
- **germline**: varianti ereditarie o de novo presenti nella linea germinale che possono conferire predisposizione.

Queste annotazioni costituiscono conoscenza generale. Non dimostrano che una specifica variante sia presente in un determinato paziente o campione. Per questa distinzione si veda [[Varianti germinali e somatiche]].

## Ruolo in cancer

Un gene può essere annotato come:
- **oncogene**: alterazioni attivanti o aumento dell'attività possono favorire la trasformazione tumorale;
- **TSG** (*tumour suppressor gene*): la perdita o riduzione della funzione può favorire il tumore;
- **oncogene/TSG**: il ruolo può dipendere dal tipo di alterazione o dal contesto biologico.

## Tipi di alterazione

Le categorie possono includere:
- mutazioni missenso;
- mutazioni nonsenso;
- frameshift;
- alterazioni dei siti di splicing;
- delezioni;
- amplificazioni;
- traslocazioni e fusioni;
- altre alterazioni strutturali.

L'elenco associato a un gene sintetizza categorie osservate in precedenza; non identifica da solo una specifica variante né la sua presenza in un nuovo campione.

## Uso come conoscenza preesistente

Il Cancer Gene Census può essere usato per:
1. annotare una lista di geni ottenuta sperimentalmente;
2. verificare quali geni candidati sono già riconosciuti come cancer genes;
3. interpretare il possibile ruolo oncologico di geni e varianti;
4. selezionare o prioritizzare candidati insieme ad altre evidenze;
5. confrontare risultati sperimentali con conoscenza curata.

Un workflow generale può essere:

```text
Analisi sperimentale
→ produce una lista di geni candidati

Cancer Gene Census
→ fornisce conoscenza oncologica preesistente

Intersezione o annotazione
→ evidenzia candidati già supportati dalla letteratura oncologica
```

L'appartenenza al CGC aumenta la plausibilità oncologica di un candidato, ma non costituisce una nuova validazione sperimentale e non dimostra che il gene sia alterato nei campioni analizzati.

## Limiti interpretativi

- I geni più studiati possono avere annotazioni più ricche.
- Le conoscenze e le versioni della risorsa cambiano nel tempo.
- Un gene può avere ruoli diversi in tumori differenti.
- Un'associazione generale non sostituisce l'analisi del singolo paziente.
- L'assenza dal CGC non dimostra che un gene non abbia alcun ruolo nel cancro.
- Le annotazioni devono essere distinte dai dati prodotti dall'esperimento che si sta interpretando.

Quando il CGC viene usato in un'analisi, è necessario documentare la versione o la data di accesso e distinguere chiaramente i risultati sperimentali dalle annotazioni importate.

Vedi anche: [[Banche dati biologiche]], [[Genomics]], [[Varianti germinali e somatiche]], [[Gene]].
