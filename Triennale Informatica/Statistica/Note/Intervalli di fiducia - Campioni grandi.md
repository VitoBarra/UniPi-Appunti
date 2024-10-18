---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Intervalli di fiducia - Campioni grandi
---
In caso di _campioni grandi_ per poter determinare gli [[Intervalli di fiducia|interevalli di fiducia]] si può fare uso del [[Teorema centrale del limite|teorema centrale del limite]]  infatti valgono i seguenti risultati 


#### Intervalli di fiducia per la media, campioni grandi, varianza nota
_sia_
- $X_{1},\dots X_{n}$ un [[Campione Statistico|campione statistico]] la cui legge di [[Probabilita sui numeri Reali|probabilita]] ha [[Variabili aleatoria - Momenti|momento secondo]] finito.
- $\alpha \in (0,1)$
- $\sigma^{2}$ la [[Variabili aleatorie - Varianza|varianza]] _nota_
_se_ $n$ è grande
_allora_ l [[Intervalli di fiducia#Intervallo aleatorio o casuale (Definizione)|intervallo aleatorio]] $$I=\left[ \overline{X}_{n}\pm\frac{\sigma}{\sqrt{ n }}q_{1-\alpha/2} \right]$$è un _[[Intervalli di fiducia#Intervallo di fiducia|intervallo di fiducia]]_ con _livello di fiducia_ approssimativamente $1-\alpha$ ovvero vale che $$\lim_{ n \to \infty } \mathcal{P}\left\{ m \in  \left[ \overline{X}_{n}\pm\frac{\sigma}{\sqrt{ n }}q_{1-\alpha/2} \right] \right\} =1-\alpha$$
#### Intervalli di fiducia per la media, Campioni grandi, Varianza non nota
_sia_
- $X_{1},\dots X_{n}$ un _[[Campione Statistico|campione statistico]]_ la cui legge di [[Probabilita sui numeri Reali|probabilita]] ha [[Variabili aleatoria - Momenti|momento secondo]] finito.
- $\alpha \in (0,1)$
- $S_{n}^{2}$ la [[Idd - varianza campionaria|varianza campionaria]] di $X_{1},\dots X_{n}$
_se_ $n$ è grande
_allora_ l [[Intervalli di fiducia#Intervallo aleatorio o casuale (Definizione)|intervallo aleatorio]] $$\left[ \overline{X}_{n} \pm\frac{S_{n}}{\sqrt{ n }}q_{1-\alpha/2} \right]$$è un _intervallo di fiducia_ con _livello di fiducia_ approssimativamente $1-\alpha$ $$\lim_{ n \to \infty } \left\{ m \in  \left[ \overline{X}_{n}\pm\frac{S_{n}}{\sqrt{ n }}q_{1-\alpha/2} \right] \right\} =1-\alpha$$dove si usa $S^{2}_{n}$  la _[[Idd - varianza campionaria|varianza campionaria]]_ perché  è un [[Statistica Parametrica#Stimatore corretto (Definizione)|buon stimatore]] della _[[Variabili aleatorie - Varianza|varianza]]_


