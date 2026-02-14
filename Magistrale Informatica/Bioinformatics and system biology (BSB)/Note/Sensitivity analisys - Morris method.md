---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Sensitivity analisys - Morris method
Il **Morris method** è un metodo di screening per la **[[Sensitivity analisys|Sensitivity analisys]] globale**, progettato per identificare in modo efficiente i parametri influenti in modelli ad alta dimensionalità.

L’idea è stimare come l’output del modello varia quando ciascun parametro viene perturbato individualmente lungo traiettorie casuali nello spazio parametrico.

Sia un modello scalare:
$$
y = f(p_1, \dots, p_k)
$$

Si definisce l’**Elementary Effect (EE)** del parametro $p_i$ come:

$$
EE_i = \frac{f(p_1, \dots, p_i + \Delta, \dots, p_k) - f(p_1, \dots, p_i, \dots, p_k)}{\Delta}
$$

dove:
- $\Delta$ è un passo finito scelto su una griglia discreta dello spazio dei parametri,
- gli altri parametri restano fissati durante la perturbazione di $p_i$.

Il procedimento viene ripetuto per:
- più punti iniziali scelti casualmente nello spazio parametrico,
- più traiettorie casuali.

Si ottiene quindi, per ciascun parametro, una distribuzione di effetti elementari.

Dalle repliche si calcolano due indicatori principali:

- Media dei valori assoluti:
$$
\mu_i^\ast = \frac{1}{r} \sum_{j=1}^{r} |EE_i^{(j)}|
$$
misura l’influenza complessiva del parametro $p_i$ sull’output.

- Deviazione standard:
$$
\sigma_i = \sqrt{\frac{1}{r-1}\sum_{j=1}^{r}(EE_i^{(j)} - \bar{EE_i})^2}
$$
misura la variabilità degli effetti elementari, indicando:
  - non linearità,
  - interazioni con altri parametri.

Interpretazione:
- $\mu_i^\ast$ alto ⇒ parametro influente.
- $\sigma_i$ alto ⇒ presenza di interazioni o comportamento non lineare.
- $\mu_i^\ast$ basso e $\sigma_i$ basso ⇒ parametro trascurabile.

Caratteristiche del metodo:
- Richiede un numero relativamente ridotto di simulazioni rispetto ai metodi variance-based.
- È adatto come fase preliminare di screening.
- È particolarmente utile per modelli con molti parametri.
- Non fornisce una decomposizione completa della varianza come gli indici di Sobol.

Il Morris method rappresenta quindi un compromesso tra costo computazionale e capacità di rilevare effetti globali, risultando efficace per l’identificazione preliminare dei parametri dominanti.