---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area: Modelli Generativi
topic: Continuous-time generative models
SubTopic:
---
# Stochastic Differential Equations (SDE)
---
Le **Stochastic Differential Equations (SDE)** descrivono dinamiche continue nel tempo in cui l'evoluzione dello stato dipende sia da una componente deterministica sia da una componente casuale. Invece di specificare solo una velocita istantanea, come nelle [[Ordinary Differential Equation (ODE)|ordinary differential equations]], si introduce anche un termine di rumore che perturba continuamente la traiettoria.

Formalmente, una SDE si scrive nella forma

$$dx_t = f(x_t,t)\,dt + g(t)\,dW_t$$

dove $x_t$ e lo stato al tempo $t$, $f(x_t,t)$ e il termine di drift che governa la parte deterministica, $g(t)$ e il coefficiente di diffusione che regola l'intensita del rumore e $W_t$ e un [[Moto Browniano|moto browniano]] o processo di Wiener. Operativamente, il termine $f(x_t,t)\,dt$ sposta il campione secondo una direzione media, mentre $g(t)\,dW_t$ introduce una fluttuazione casuale infinitesima.

Questa struttura e importante nei modelli generativi continui perche permette di descrivere processi di corruzione e di denoising non come semplici traiettorie deterministiche, ma come evoluzioni stocastiche di intere distribuzioni. Nei [[Diffusion Models|diffusion models]], per esempio, il forward process discreto che aggiunge rumore gaussiano a ogni step ammette un limite continuo rappresentabile tramite una SDE. In questa lettura, il modello non segue una singola curva nello spazio dei dati, ma una dinamica rumorosa che deforma progressivamente la distribuzione.

Se si considera una SDE forward, la distribuzione dei campioni evolve nel tempo secondo un'equazione differenziale per densita, spesso espressa tramite l'equazione di Fokker-Planck. Il punto strutturale e che la dinamica dello stato induce una dinamica sulle distribuzioni, e quindi su oggetti probabilistici invece che solo su traiettorie individuali.

Nei modelli score-based, la SDE e particolarmente utile perche il reverse process di una dinamica diffusiva puo essere espresso anch'esso come una SDE, ma con un drift corretto dalla [[Score Function|score function]] della distribuzione intermedia. In questo modo la score entra come termine che orienta il processo stocastico all'indietro verso regioni di maggiore densita dei dati.

Una formulazione importante collega poi SDE e [[Ordinary Differential Equation (ODE)|ODE]]. A partire da una SDE score-based si puo definire una **probability flow ODE**, cioe una ODE deterministica che preserva la stessa evoluzione marginale delle densita pur eliminando il rumore esplicito dalle traiettorie. Questo chiarisce perche i modelli score-based e i metodi di [[Flow Matching|flow matching]] siano concettualmente vicini: i primi nascono da una dinamica stocastica, i secondi lavorano direttamente con un campo di velocita deterministico, ma entrambi descrivono trasporto continuo di probabilita.

Rispetto a una [[Ordinary Differential Equation (ODE)|ODE]], una SDE non assegna una traiettoria unica a una condizione iniziale, ma una famiglia di traiettorie casuali. Rispetto ai modelli discreti di diffusione, fornisce invece una descrizione continua piu adatta per collegare denoising, score-based modeling e flow continuo.

Le proprieta operative piu importanti sono:
- combina un termine di drift deterministico e un termine di diffusione stocastico
- descrive naturalmente il limite continuo dei [[Diffusion Models|diffusion models]]
- collega [[Score Matching|score matching]] e [[Flow Matching|flow matching]] tramite la probability flow [[Ordinary Differential Equation (ODE)|ODE]]
