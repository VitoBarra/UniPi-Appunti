---
Course: "[[Robotics MOC]]"
tags:
  - "#ROB"
Area:
topic:
SubTopic:
---

# Trasformata di Laplace

La **trasformata di Laplace** porta una funzione del tempo $f(t)$ nel dominio complesso $s$. Nella [[Control Theory|teoria del controllo]] è utile perché trasforma le equazioni differenziali in equazioni algebriche, rendendo più semplice ricavare e analizzare le [[Funzioni di trasferimento]].

## Definizione

La trasformata unilatera di $f(t)$, per $t\geq0$, è $$F(s)=\mathcal{L}\{f(t)\}=\int_0^{\infty}f(t)e^{-st}\,dt$$dove $s=\sigma+j\omega$ è una variabile complessa. L'operazione inversa, quando esiste, permette di ritornare a $f(t)$.

## Proprietà utili nel controllo

La trasformata è lineare: $$\mathcal{L}\{af(t)+bg(t)\}=aF(s)+bG(s)$$

La proprietà più importante riguarda le derivate. Per la derivata prima vale $$\mathcal{L}\{\dot f(t)\}=sF(s)-f(0)$$e, più in generale, $$\mathcal{L}\left\{\frac{d^nf(t)}{dt^n}\right\}=s^nF(s)-s^{n-1}f(0)-s^{n-2}\dot f(0)-\dots-f^{(n-1)}(0)$$

Se tutte le condizioni iniziali sono nulle, la formula si semplifica in $$\mathcal{L}\left\{\frac{d^nf(t)}{dt^n}\right\}=s^nF(s)$$Questa è precisamente l'ipotesi usata nella definizione di funzione di trasferimento.

> [!important] Condizioni iniziali
> I termini $f(0)$, $\dot f(0)$, \dots rappresentano lo stato iniziale del sistema. Non vanno eliminati quando si sta calcolando la risposta di un sistema che parte da uno stato non nullo; si annullano solo nel calcolo della funzione di trasferimento.

## Coppie di trasformate ricorrenti

| Segnale nel tempo | Trasformata di Laplace |
| --- | --- |
| $1$ | $1/s$ |
| $t$ | $1/s^2$ |
| $e^{-at}$ | $1/(s+a)$ |
| $\sin(\omega t)$ | $\omega/(s^2+\omega^2)$ |
| $\cos(\omega t)$ | $s/(s^2+\omega^2)$ |
| $e^{-at}\sin(\omega t)$ | $\omega/((s+a)^2+\omega^2)$ |

Per un sistema causale, il gradino unitario $u(t)$ ha trasformata $1/s$. Un ingresso sinusoidale $A\sin(\omega t)$ ha invece trasformata $$\frac{A\omega}{s^2+\omega^2}$$

## Dalle ODE alle funzioni di trasferimento

Data un'equazione differenziale lineare, si applica la trasformata di Laplace a entrambi i membri, si sostituiscono le derivate con le corrispondenti potenze di $s$ e si isolano $Y(s)$ e $U(s)$. Con condizioni iniziali nulle, il rapporto $$G(s)=\frac{Y(s)}{U(s)}$$è la funzione di trasferimento.

Un esempio completo è [[Sistema massa-molla-smorzatore]], in cui un'equazione differenziale del secondo ordine diventa una TF razionale in $s$.

## Collegamenti

- [[Funzioni di trasferimento]]
- [[Sistema massa-molla-smorzatore]]
- [[Control Theory]]

## Fonte della lezione

- [[Transfer Functions Introduction and Implementation - christopher lum]]
