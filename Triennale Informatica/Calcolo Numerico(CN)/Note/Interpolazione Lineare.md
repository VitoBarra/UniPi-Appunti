---
Course: "[[Calcolo Numerico(CN)]]"
tags:
  - CN
topic:
---
# Interpolazione Lineare
---
L'_interpolazione lineare_ è un metodo che stima il valore di una funzione tra due punti noti utilizzando una [[Retta|retta]] che li _congiunge_. 
Questo approccio fornisce una stima lineare del valore della funzione in punti intermedi non noti.

_siano_ due coordinate $(x_i, y_i)$ e $(x_{i+1}, y_{i+1})$
_allora_ la formula per l'_interpolazione lineare_ è data da:$$f(x) =\frac{x_{i+1}-x}{x_{i+1}-x_{i}}\cdot y_1 + \frac{{x - x_i}}{{x_{i+1} - x_i}}\cdot y_{i+1}$$ 
dove:
- $f(x)$ è il _valore interpolato_,
- $x$ è il punto in cui si desidera stimare il valore,
- $x_i$ e $x_{i+1}$ sono le coordinate $x$ dei punti noti
- $y_i$ e $y_{i+1}$ sono i corrispondenti valori della funzione.

un esempio di _interpolazione lineare_ che si puo fare tra _valori reali_ è il seguente 
![[Pasted image 20230515170753.png]]
dove le linee spezzate sono ciò che riusciamo ad ottenere con l _interpolazione lineare_

### Applicazioni

1. **Grafici e Dati Sperimentali:**
   - Utilizzata per stimare valori intermedi tra punti noti in un grafico.
   - Applicata in analisi dati sperimentali per ottenere valori approssimativi.

2. **Animazioni e Grafica Computerizzata:**
   - Nelle animazioni, l'interpolazione lineare può essere utilizzata per ottenere movimenti fluidi tra due posizioni.

3. **Finanza e Mercati:**
   - Nei mercati finanziari, l'interpolazione lineare può essere usata per stimare il valore di un asset in un punto di tempo non specificato.

### Limitazioni

1. **Assunzioni Lineari:**
   - L'interpolazione lineare assume che la relazione tra i punti noti sia approssimativamente lineare, il che potrebbe non essere vero in tutte le situazioni.

2. **Errori di Approssimazione:**
   - Poiché l'interpolazione lineare approssima con una retta, potrebbe introdurre errori significativi in presenza di variazioni non lineari.

