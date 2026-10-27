---
Course: "[[Robotics MOC]]"
tags:
  - "#ROB"
Area:
topic:
SubTopic:
---

# Filtri passa alto e passa basso

Un **filtro** modifica un segnale in modo dipendente dalla sua frequenza. Nella [[Control Theory|teoria del controllo]] viene usato, per esempio, per attenuare il rumore di misura, rendere più regolare un riferimento oppure limitare l'effetto di disturbi ad alta frequenza sul comando.

La frequenza angolare è indicata con $\omega$ ed è legata alla frequenza ordinaria $f$ da $$\omega=2\pi f$$

## Filtro passa basso

Un **filtro passa basso** (*low-pass filter*, LPF) lascia passare le componenti a bassa frequenza e attenua quelle ad alta frequenza. È quindi adatto a eliminare oscillazioni rapide e rumore sovrapposti a un segnale che varia più lentamente.

Un passa basso del primo ordine ha funzione di trasferimento $$G_{LP}(s)=\frac{\omega_c}{s+\omega_c}=\frac{1}{\tau s+1}$$dove:

- $\omega_c$ è la **frequenza di taglio**;
- $\tau=1/\omega_c$ è la costante di tempo.

Per $\omega\ll\omega_c$, il guadagno è circa uno: il segnale passa quasi inalterato. Per $\omega\gg\omega_c$, il guadagno diminuisce proporzionalmente a $1/\omega$. Nel diagramma di Bode la pendenza oltre il taglio è $-20\ \mathrm{dB/decade}$.

Alla frequenza di taglio vale $$\left|G_{LP}(j\omega_c)\right|=\frac{1}{\sqrt{2}}$$corrispondente a circa $-3\ \mathrm{dB}$ rispetto al guadagno nella banda passante.

![[risposta-in-frequenza-filtri.svg|900]]

> [!example] Esempio d'uso
> La misura di posizione o velocità di un encoder può contenere rumore ad alta frequenza. Un passa basso rende la misura più stabile, ma introduce anche ritardo e attenua le variazioni rapide effettivamente presenti nel moto.

## Filtro passa alto

Un **filtro passa alto** (*high-pass filter*, HPF) attenua le componenti a bassa frequenza e lascia passare quelle ad alta frequenza. Può essere usato per rimuovere un offset costante o una deriva lenta dal segnale.

Un passa alto del primo ordine ha funzione di trasferimento $$G_{HP}(s)=\frac{s}{s+\omega_c}=\frac{\tau s}{\tau s+1}$$

Per $\omega\ll\omega_c$, il guadagno tende a zero; per $\omega\gg\omega_c$, tende a uno. Nel diagramma di Bode la pendenza sotto il taglio è $+20\ \mathrm{dB/decade}$.

Poiché $G_{HP}(0)=0$, una componente costante non passa attraverso il filtro. Per questo il passa alto viene spesso interpretato come un modo per evidenziare le variazioni del segnale, più che il suo valore assoluto.

## Confronto

| Proprietà | Passa basso | Passa alto |
| --- | --- | --- |
| Banda passante | Basse frequenze | Alte frequenze |
| Componente continua | Passa | Viene eliminata |
| Uso tipico | Riduzione del rumore rapido | Rimozione di offset e derive lente |
| Guadagno a $\omega=0$ | $1$ | $0$ |
| Guadagno per $\omega\to\infty$ | $0$ | $1$ |

![[effetto-temporale-filtri.svg|900]]

Nell'esempio temporale, il passa basso segue la componente lenta della misura e attenua le oscillazioni rapide. Il passa alto, invece, sopprime la deriva lenta e lascia emergere la componente che varia rapidamente.

## Scelta della frequenza di taglio

La scelta di $\omega_c$ è un compromesso. In un passa basso, una frequenza di taglio più piccola rimuove più rumore ma aumenta il ritardo e può rendere la retroazione meno reattiva. Una frequenza troppo grande, invece, lascia passare gran parte del rumore.

Conviene scegliere il taglio separando, per quanto possibile, la banda utile del segnale dalla banda in cui è concentrato il disturbo. Questa separazione non è sempre netta: in quel caso il filtro va valutato insieme alla dinamica del sistema e alle prestazioni richieste al controllore.

> [!warning] Effetto sulla retroazione
> Un filtro non modifica solo l'ampiezza del segnale: introduce anche fase. In un anello di controllo il ritardo di fase può ridurre i margini di stabilità; filtrare una misura richiede quindi di controllare l'effetto sull'intero anello chiuso.

## Implementazione discreta

Per un segnale campionato con periodo $T_s$, un semplice passa basso può essere implementato come $$y[k]=\alpha x[k]+(1-\alpha)y[k-1]$$dove $0<\alpha<1$. Un valore piccolo di $\alpha$ produce un filtraggio più forte e una risposta più lenta.

Una scelta comune, ottenuta dalla discretizzazione del filtro del primo ordine, è $$\alpha=\frac{T_s}{\tau+T_s}$$

## Collegamenti

- [[Funzioni di trasferimento]]
- [[Control Theory]]
- [[Proportional integral derivative (PID)]]
