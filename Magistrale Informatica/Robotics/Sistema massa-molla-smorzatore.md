---
Course: "[[Robotics MOC]]"
tags:
  - "#ROB"
Area:
topic:
SubTopic:
---

# Sistema massa-molla-smorzatore

Il sistema **massa--molla--smorzatore** è un modello fondamentale per descrivere sistemi meccanici traslazionali e, per analogia, molti sistemi rotazionali, elettrici e robotici. Mostra in modo concreto come passare dalle leggi fisiche a una [[Funzioni di trasferimento|funzione di trasferimento]].

## Modello fisico

Una massa $M$ è collegata a una molla con costante elastica $K$ e a uno smorzatore viscoso con coefficiente $C$. Si applica una forza esterna $u(t)$ e si misura lo spostamento $y(t)$.

- La massa oppone una forza inerziale $M\ddot y(t)$.
- La molla oppone una forza $Ky(t)$ proporzionale allo spostamento.
- Lo smorzatore oppone una forza $C\dot y(t)$ proporzionale alla velocità.

Applicando il secondo principio della dinamica si ottiene $$M\ddot y(t)+C\dot y(t)+Ky(t)=u(t)$$

## Passaggio nel dominio di Laplace

Applicando la [[Trasformata di Laplace]] senza trascurare le condizioni iniziali: $$M\left(s^2Y(s)-sy(0)-\dot y(0)\right)+C\left(sY(s)-y(0)\right)+KY(s)=U(s)$$

Questa forma evidenzia che posizione e velocità iniziali contribuiscono alla risposta. Per ricavare la funzione di trasferimento si pongono $y(0)=0$ e $\dot y(0)=0$: $$\left(Ms^2+Cs+K\right)Y(s)=U(s)$$

La funzione di trasferimento forza--posizione è quindi $$G(s)=\frac{Y(s)}{U(s)}=\frac{1}{Ms^2+Cs+K}$$

## Forma normalizzata

Dividendo numeratore e denominatore per $M$, si può scrivere $$G(s)=\frac{1/M}{s^2+\frac{C}{M}s+\frac{K}{M}}=\frac{1/M}{s^2+2\zeta\omega_n s+\omega_n^2}$$dove $$\omega_n=\sqrt{\frac{K}{M}}$$è la pulsazione naturale e $$\zeta=\frac{C}{2\sqrt{MK}}$$è il rapporto di smorzamento.

- $\zeta=0$: assenza di smorzamento e oscillazioni persistenti.
- $0<\zeta<1$: risposta sottosmorzata, con oscillazioni smorzate.
- $\zeta=1$: smorzamento critico.
- $\zeta>1$: risposta sovrasmorzata, senza oscillazioni ma generalmente più lenta.

## Risposta a un gradino di forza

Per un gradino unitario di forza, $U(s)=1/s$, l'uscita è $$Y(s)=\frac{1}{s\left(Ms^2+Cs+K\right)}$$Se $K>0$ e $C>0$, il sistema è asintoticamente stabile e il valore finale dello spostamento è $$\lim_{t\to\infty}y(t)=\frac{1}{K}$$Questo coincide con l'equilibrio statico: a regime la forza elastica $Ky$ bilancia una forza unitaria.

## Uso nel controllo

Il modello è di secondo ordine e rende visibile il compromesso fra velocità di risposta, oscillazioni e smorzamento. È una base ideale per studiare poli, risposta al gradino e progettazione di controllori, ad esempio un PID.

## Collegamenti

- [[Trasformata di Laplace]]
- [[Funzioni di trasferimento]]
- [[Control Theory]]

## Fonte della lezione

- [[Transfer Functions Introduction and Implementation - christopher lum]]
