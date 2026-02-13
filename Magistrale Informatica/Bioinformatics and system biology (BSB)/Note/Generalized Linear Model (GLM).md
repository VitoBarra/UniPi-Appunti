---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
Area:
topic:
SubTopic:
---

# Generalized Linear Model (GLM)
---
Il **Generalized Linear Model (GLM)** è una generalizzazione del [[Modelli lineari con LMS|modello lineare]] classico che permette di modellare variabili risposta che non seguono una distribuzione normale. È adatto a dati discreti, conteggi, proporzioni o variabili binarie, mantenendo una struttura lineare nei parametri.

Un GLM è definito da tre componenti fondamentali.

1) **Componente casuale (random component)**  
La variabile risposta $Y_i$ segue una distribuzione appartenente alla famiglia esponenziale (Normale, Binomiale, Poisson, Negative Binomial, ecc.). La distribuzione determina la relazione tra media e varianza.
2) **Componente sistematica (systematic component)**  
Si definisce un predittore lineare:
$$\eta_i = X_i \beta$$
dove $X_i$ è il vettore delle covariate osservate per l’osservazione $i$ e $\beta$ è il vettore dei parametri da stimare.

3) **Funzione di link**  
Una funzione $g(\cdot)$ collega la media della risposta al predittore lineare:
$$g(\mu_i) = \eta_i$$
dove $\mu_i = \mathbb{E}[Y_i]$.

La funzione di link permette di modellare relazioni non lineari tra la media della risposta e le covariate, mantenendo linearità nei parametri.

---

Esempi comuni:

- **Modello lineare classico**  
  Distribuzione: Normale  
  Link: identità$$\mu_i = X_i \beta$$
- **Regressione logistica**  
  Distribuzione: Binomiale  
  Link: logit  $$\log\frac{\mu_i}{1-\mu_i} = X_i \beta$$
- **Regressione di Poisson**  
  Distribuzione: Poisson  
  Link: log  $$\log(\mu_i) = X_i \beta$$

I parametri $\beta$ sono stimati tramite **massima verosimiglianza**. L’inferenza si basa su test di ipotesi sui coefficienti, ad esempio:
$$H_0 : \beta_j = 0$$
per valutare l’effetto di una covariata.

Il GLM estende quindi il modello lineare consentendo:
- distribuzioni non gaussiane,
- varianza dipendente dalla media,
- modellizzazione flessibile di diversi tipi di dati.
