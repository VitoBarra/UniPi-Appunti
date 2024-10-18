---
Course: "[[Analisi|Analisi]]"
topic: nota
tags:
  - Analisi
---
# Derivate
---
#### Derivata di una Funzione (Definizione)
La **derivata** di una funzione $f(x)$ in un punto $x$ è definita come il **limite**:$$
f'(x) = \lim_{{\varepsilon \to 0}} \frac{f(x + \varepsilon) - f(x)}{\varepsilon}
$$Questa espressione rappresenta il tasso di variazione istantaneo di $f$ rispetto a $x$ quando la variazione $h$ tende a zero. In altre parole, la derivata di $f$ in $x$ è la pendenza della retta tangente alla curva di $f$ in quel punto.

#### Regole di Derivazione

_Regola Somma e Differenza_$$\frac{d}{dx}(f(x) \pm g(x)) = f'(x) \pm g'(x)$$
_Regola della Catena_$$\frac{d}{dx}(f(g(x))) = f'(g(x)) \cdot g'(x)$$

_Derivata della  moltiplicazione_$$\frac{d}{dx}(f(x) \cdot g(x))=f’(x)g(x) + g’(x)f(x)$$
_Derivata della divisone_ $$\frac{d}{dx}\left(\frac{f(x)}{g(x)}\right) =\frac{f’(x)g(x) - g’(x)f(x)}{(g(x))^2}$$