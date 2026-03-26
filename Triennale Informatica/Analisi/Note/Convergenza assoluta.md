---
Course: "[[Analisi]]"
topic: nota
tags:
  - Analisi
---
# Convergenza assoluta
---
La **convergenza assoluta** e una proprieta delle [[Serie|serie]] numeriche che richiede la convergenza della serie dei valori assoluti.

## Definizione
_Sia_ $\sum_{n=1}^{+\infty} a_n$ una serie reale o complessa.
_Se_ la serie
$$
\sum_{n=1}^{+\infty} |a_n|
$$
converge,
_allora_ si dice che la serie
$$
\sum_{n=1}^{+\infty} a_n
$$
**converge assolutamente**.

## Significato
La convergenza assoluta e una forma di convergenza piu forte della semplice convergenza.

L'idea e che la serie continua a convergere anche se si ignorano i segni dei termini: quindi non converge solo per compensazione tra termini positivi e negativi, ma perche i contributi complessivi diventano davvero piccoli.

## Teorema fondamentale
_Se_ una serie converge assolutamente,
_allora_ converge anche nel senso usuale.

In simboli:
$$
\sum |a_n| \text{ converge } \implies \sum a_n \text{ converge.}
$$

Il viceversa in generale e falso.

## Convergenza semplice e convergenza assoluta
Quando una serie $\sum a_n$ converge, ma la serie $\sum |a_n|$ diverge, si dice che la serie converge **solo condizionatamente** o **non assolutamente**.

Quindi si hanno due casi:
- **convergenza assoluta**: converge $\sum |a_n|$;
- **convergenza condizionata**: converge $\sum a_n$ ma diverge $\sum |a_n|$.

## Esempio
La serie
$$
\sum_{n=1}^{+\infty}\frac{(-1)^{n+1}}{n}
$$
converge, ma non converge assolutamente, perche
$$
\sum_{n=1}^{+\infty}\left|\frac{(-1)^{n+1}}{n}\right|
=
\sum_{n=1}^{+\infty}\frac{1}{n}
$$
diverge.

Questa e quindi un esempio di serie a convergenza condizionata.

## Osservazione utile
Per provare la convergenza assoluta di una serie si studia la serie dei valori assoluti usando i soliti criteri di convergenza, ad esempio:
- criterio del confronto;
- criterio del rapporto;
- criterio della radice;
- confronto con serie note, come la [[Serie geometrica|serie geometrica]].

>[!tip]
> La convergenza assoluta e spesso la condizione migliore da verificare, perche garantisce automaticamente la convergenza della serie originale.
