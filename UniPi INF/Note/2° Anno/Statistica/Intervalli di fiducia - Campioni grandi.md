---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Intervalli di fiducia - Campioni grandi
---
in generale si puo usare il [[Teorema centrale del limite|teorema centrale del limite]] per poter determinare gli [[Intervalli di fiducia|interevalli di fiducia]] infatti valgono i seguenti risultati 


#### Intervalli di fiducia per la media, campioni grandi, varianza nota
_sia_
- $X_{1},\dots X_{n}$ un [[Campione Statistico|campione statistico]] la cui legge di [[Probabilita sui numeri Reali|probabilita]] ha [[Variabili aleatoria - Momenti|momento secondo]] finito.
- $\alpha \in (0,1)$
_se_ $n$ è grande
_allora_ l [[Intervalli di fiducia#Intervallo aleatorio o casuale (Definizione)|intervallo aleatorio]] $$\left[ \overline{X}_{n}\pm\frac{\sigma}{\sqrt{ n }}q_{1-\alpha/2} \right]$$è un _intervallo di fiducia_ con _livello di fiducia_ approssimativamente $1-\alpha$ $$\lim_{ n \to \infty } \left\{ m \in  \left[ \overline{X}_{n}\pm\frac{\sigma}{\sqrt{ n }}q_{1-\alpha/2} \right] \right\} =1-\alpha$$
#### Intervalli di fiducia per la media, Campioni grandi, Varianza non nota
_sia_
- $X_{1},\dots X_{n}$ un [[Campione Statistico|campione statistico]] la cui legge di [[Probabilita sui numeri Reali|probabilita]] ha [[Variabili aleatoria - Momenti|momento secondo]] finito.
- $\alpha \in (0,1)$
_se_ $n$ è grande
_allora_ l [[Intervalli di fiducia#Intervallo aleatorio o casuale (Definizione)|intervallo aleatorio]] $$\left[ \overline{X}_{n} \pm\frac{S_{n}}{\sqrt{ n }}q_{1-\alpha/2} \right]$$è un _intervallo di fiducia_ con _livello di fiducia_ approssimativamente $1-\alpha$ $$\lim_{ n \to \infty } \left\{ m \in  \left[ \overline{X}_{n}\pm\frac{S_{n}}{\sqrt{ n }}q_{1-\alpha/2} \right] \right\} =1-\alpha$$dove $S^{2}_{n}$ è la [[Idd - varianza campionaria|varianza campionaria]] di $X_{1},\dots X_{n}$ del _[[Campione Statistico|campione statistico]]_ ed è un [[Statistica Parametrica#Stimatore corretto (Definizione)|buon stimatore]] della varianza


