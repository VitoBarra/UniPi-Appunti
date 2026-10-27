---
Course: "[[Robotics MOC]]"
tags:
  - "#ROB"
Area:
topic:
SubTopic:
---

# Funzioni di trasferimento

Una **funzione di trasferimento** (*transfer function*, TF) è un modello ingresso--uscita: descrive come un particolare ingresso $u(t)$ influenza una particolare uscita $y(t)$ di un sistema. È uno degli strumenti principali della [[Control Theory|teoria del controllo]] per analizzare sistemi dinamici e progettare controllori.

## Interpretazione ingresso-uscita
Un sistema fisico può avere più ingressi $u_1,\dots,u_n$ e più uscite $y_1,\dots,y_p$. Una singola funzione di trasferimento seleziona una coppia di interesse; ad esempio, per un aeromobile si potrebbe studiare l'effetto della deflessione dell'elevatore sull'angolo d'attacco: $$G_{\alpha,\delta_e}(s)=\frac{\alpha(s)}{\delta_e(s)}$$Questa scelta è un'approssimazione utile: l'elevatore influenza anche altre grandezze, come l'assetto e temporaneamente la velocità, mentre l'angolo d'attacco dipende anche da altri ingressi e dallo stato operativo. Nei sistemi multivariabili, le singole relazioni possono essere raccolte in una **matrice di trasferimento** $G(s)$.

## Definizione per un sistema LTI
Per un sistema **lineare tempo-invariante** (*LTI*), con condizioni iniziali nulle, la funzione di trasferimento è $$G(s)=\frac{Y(s)}{U(s)}$$dove $U(s)=\mathcal{L}\{u(t)\}$ e $Y(s)=\mathcal{L}\{y(t)\}$ sono le trasformate di Laplace di ingresso e uscita.

Di conseguenza, noto un ingresso $U(s)$, l'uscita si ottiene come $$Y(s)=G(s)U(s)$$L'antitrasformata di Laplace di $Y(s)$ riporta la risposta nel dominio del tempo.

> [!important] Condizioni iniziali nulle
> La definizione di $G(s)$ presuppone che lo stato iniziale e le sue derivate rilevanti siano nulli. Se, per esempio, una massa parte già spostata o con velocità iniziale non nulla, questi termini compaiono nella trasformata di Laplace e la sola funzione di trasferimento non ne rappresenta l'effetto.

## Dall'equazione differenziale alla TF

Un sistema LTI a singolo ingresso e singola uscita può essere descritto nella forma generale $$\sum_{k=0}^{n} a_k\frac{d^k y(t)}{dt^k}=\sum_{k=0}^{m} b_k\frac{d^k u(t)}{dt^k}$$Con condizioni iniziali nulle, la trasformata di Laplace trasforma ogni derivata in una moltiplicazione per $s^k$. Si ottiene quindi $$\left(\sum_{k=0}^{n}a_ks^k\right)Y(s)=\left(\sum_{k=0}^{m}b_ks^k\right)U(s)$$ e pertanto $$G(s)=\frac{Y(s)}{U(s)}=\frac{b_ms^m+b_{m-1}s^{m-1}+\dots+b_1s+b_0}{a_ns^n+a_{n-1}s^{n-1}+\dots+a_1s+a_0}$$ Il denominatore contiene la dinamica naturale del sistema; le sue radici sono i **poli**. Le radici del numeratore sono gli **zeri**. Poli e zeri determinano aspetti essenziali della risposta, come stabilità, transitorio e risposta alle diverse frequenze.



## Uso pratico in MATLAB e Simulink

Per $G(s)=1/(Ms^2+Cs+K)$, MATLAB rappresenta numeratore e denominatore tramite i coefficienti dei polinomi in potenze decrescenti di $s$:

```matlab
M = 1;
C = 3;
K = 5;

G = tf(1, [M C K]);
step(G)
```

In Simulink lo stesso modello può essere inserito con il blocco **Transfer Fcn**, usando `1` come numeratore e `[M C K]` come denominatore. Questo consente di collegare facilmente gradini, sinusoidi e altri segnali di ingresso e osservarne l'uscita.

## Limiti del modello

- Vale direttamente solo per sistemi LTI e per condizioni iniziali nulle.
- Descrive una relazione ingresso--uscita, non l'intero stato interno del sistema.
- In presenza di non linearità, grandi variazioni del punto operativo o forti accoppiamenti tra canali, una singola TF può essere insufficiente: possono servire linearizzazioni locali, matrici di trasferimento o modelli nello spazio di stato.

## Fonte della lezione

- [[Transfer Functions Introduction and Implementation - christopher lum]]
- [[Control Theory]]
