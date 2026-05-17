---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area:
topic:
SubTopic:
---

# Modelli Generativi
---
i **Modelli Generativi** sono una classe di [[modelli parametrici|modelli parametrici]] [[Deep Learning|deep]] utilizzati per generare nuovi dati invece che semplicemente [[Concetti generali del Machine Learning|predirli o classificarli]].

Molti modelli generativi sono anche [[Modelli Probabilistici|modelli probabilistici]], perché descrivono o approssimano la distribuzione dei dati. Tuttavia non tutti lo fanno nello stesso modo: alcuni definiscono una densità esplicita, altri imparano soprattutto una procedura di campionamento.

una tassonomia riassuntiva:
- modelli espliciti: imparano una [[Distribuzione di probabilita|distribuzione di probabilità]] da cui fare sampling
- modelli impliciti: imparano una procedura di sampling che induce una distribuzione, ma senza esplicitare necessariamente una densità trattabile
![[IMG - Generative Deep Learning (GDL).png]]
