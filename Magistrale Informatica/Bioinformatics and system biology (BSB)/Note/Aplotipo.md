---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic: Genomics
SubTopic: Haplotypes
---

# Aplotipo
---
Un **aplotipo** e' la combinazione di alleli e [[Varianti germinali e somatiche|varianti]] presente su una singola copia di un cromosoma. In una regione autosomica, un individuo diploide possiede normalmente due aplotipi: uno ereditato dalla madre e uno dal padre.

```text
aplotipo materno: A - C - G
aplotipo paterno: G - T - A
```

## Genotipo e aplotipo

Il **genotipo** indica quali alleli sono presenti in ciascuna posizione, ma non necessariamente su quale copia cromosomica si trovino:

| Posizione | Genotipo |
|---|---|
| 1 | A/G |
| 2 | C/T |
| 3 | G/A |

Questi genotipi sono compatibili con piu' organizzazioni. L'aplotipo specifica quali alleli si trovano insieme:

```text
cromosoma 1: A - C - G
cromosoma 2: G - T - A
```

La ricostruzione dell'appartenenza delle varianti alle due copie cromosomiche e' detta **phasing**.

## Ereditarieta' congiunta

Varianti vicine tendono a essere ereditate insieme perche' e' meno probabile che una ricombinazione avvenga precisamente tra di esse. L'associazione non casuale tra alleli di loci diversi e' chiamata **linkage disequilibrium**. Questo produce blocchi di combinazioni ricorrenti nella popolazione.

## Varianti in cis e in trans

Due varianti sono **in cis** quando si trovano sullo stesso aplotipo e **in trans** quando si trovano sulle due copie differenti:

```text
in cis                         in trans
copia 1: variante 1 + 2        copia 1: variante 1
copia 2: nessuna               copia 2: variante 2
```

La distinzione puo' avere conseguenze cliniche: nel caso *in cis* puo' rimanere una copia interamente funzionale del gene, mentre nel caso *in trans* entrambe le copie possono essere alterate.

## Relazione con il pangenoma

Scegliere l'allele piu' frequente indipendentemente in ogni posizione puo' creare una combinazione mai osservata. Il [[Pangenoma|pangenoma]] cerca invece di preservare percorsi corrispondenti ad aplotipi reali, rappresentando insieme le varianti che compaiono sulla stessa sequenza cromosomica.

Vedi anche: [[Genoma di riferimento]], [[Pangenoma]], [[Varianti germinali e somatiche]].
