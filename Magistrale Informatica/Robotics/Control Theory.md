---
Course: "[[Robotics MOC]]"
tags:
  - "#ROB"
Area:
topic:
SubTopic:
---

# Teoria del controllo

La **teoria del controllo** studia come descrivere, analizzare e progettare sistemi dinamici affinché il loro comportamento segua quello desiderato. In robotica serve, per esempio, a fare raggiungere a un giunto una posizione, mantenere la velocità di una ruota o stabilizzare l'assetto di un drone.

L'idea centrale è trasformare un obiettivo in un'azione sul sistema:

$$r(t) \longrightarrow \text{controllore} \longrightarrow u(t) \longrightarrow \text{sistema} \longrightarrow y(t)$$

- $r(t)$ è il riferimento, cioè il valore desiderato;
- $u(t)$ è il comando o ingresso applicato al sistema;
- $y(t)$ è l'uscita osservata;
- il **sistema** (o *plant*) è la parte fisica da controllare.

Nella maggior parte delle applicazioni si misura $y(t)$ e la si confronta con il riferimento. L'errore $e(t)=r(t)-y(t)$ viene usato dal controllore per correggere il comando: è il principio della **retroazione** (*feedback*).

## Modello del sistema

Un sistema reale può avere molti ingressi, molte uscite e dinamiche non lineari. Ad esempio, per un velivolo gli ingressi possono essere la deflessione delle superfici di controllo, la spinta o perfino perturbazioni come la densità dell'aria; tra le uscite possono comparire velocità, angoli e velocità angolari.

Per studiarne una proprietà specifica spesso si isola una relazione ingresso--uscita: come influenza un dato $u(t)$ una data $y(t)$? Questa astrazione permette di passare dal sistema fisico a un modello matematico utile per l'analisi e il progetto del controllo.

> [!note] Accoppiamenti
> Isolare una coppia ingresso--uscita non significa che gli altri segnali siano irrilevanti fisicamente. Un singolo attuatore può influenzare più uscite e la relazione scelta può dipendere dal punto operativo del sistema.

## Sistemi lineari tempo-invarianti

Le [[Funzioni di trasferimento]] si applicano direttamente ai sistemi **lineari tempo-invarianti** (*Linear Time-Invariant*, LTI): sistemi descrivibili da equazioni differenziali lineari con coefficienti costanti. Questa classe è importante perché rende disponibili strumenti algebrici nel dominio di Laplace.

Molti sistemi robotici non sono LTI in tutto il loro spazio di lavoro; tuttavia, possono essere approssimati come tali attorno a un punto di equilibrio o a una traiettoria operativa. Il modello risultante è locale, ma spesso sufficiente per progettare e comprendere un controllore.

## Collegamenti

- [[Funzioni di trasferimento]]: modello ingresso--uscita nel dominio di Laplace per sistemi LTI.
- [[Robotics MOC]]

## Fonte della lezione

- [[Transfer Functions Introduction and Implementation - christopher lum]]
