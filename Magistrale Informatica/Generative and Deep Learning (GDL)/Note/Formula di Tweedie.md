---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area: Modelli Generativi
topic: Score-based models
SubTopic:
---

# Formula di Tweedie
---
La **Formula di Tweedie** esprime la media a posteriori di una variabile latente osservata attraverso rumore gaussiano in funzione della score della distribuzione osservata rumorosa. Il contesto naturale e quello in cui si definisce una variabile latente pulita $x_0$ e si osserva una variabile rumorosa $x_t$ ottenuta aggiungendo rumore gaussiano isotropo.

Formalmente, se si osserva

$$x_t = x_0 + \sigma_t \epsilon, \qquad \epsilon \sim \mathcal{N}(0,I)$$

con $\sigma_t^2$ varianza del rumore e $p_t(x_t)$ densita marginale della variabile osservata, la Formula di Tweedie afferma che la media condizionata del dato pulito dato il campione rumoroso si definisce come

$$\mathbb{E}[x_0 \mid x_t] = x_t + \sigma_t^2 \nabla_{x_t}\log p_t(x_t)$$

dove $\nabla_{x_t}\log p_t(x_t)$ e la [[Score Function|score]] della distribuzione rumorosa al livello di rumore $t$. Operativamente questa identita dice che, se si conosce la score della densita corrotta, allora si sa anche in quale direzione correggere il campione rumoroso $x_t$ per stimare il dato pulito medio compatibile con quell'osservazione.

La formula si puo leggere anche nella forma equivalente

$$\nabla_{x_t}\log p_t(x_t)=\frac{\mathbb{E}[x_0 \mid x_t]-x_t}{\sigma_t^2}$$

in cui la score appare come un vettore di correzione normalizzato dalla varianza del rumore. Questa scrittura rende esplicita l'interpretazione geometrica: la score non e solo un gradiente astratto di log-densita, ma misura quanto il campione rumoroso deve essere spostato verso regioni piu plausibili della distribuzione dei dati.

La derivazione nasce dal fatto che la densita osservata $p_t(x_t)$ e la convoluzione tra la distribuzione del dato pulito e un kernel gaussiano. Per definizione,

$$p_t(x_t)=\int p(x_0)\,\mathcal{N}(x_t\mid x_0,\sigma_t^2 I)\,dx_0$$

e derivando rispetto a $x_t$ si ottiene un termine proporzionale a $x_0-x_t$. Riordinando i termini dentro l'integrale emerge precisamente la media condizionata $\mathbb{E}[x_0\mid x_t]$, da cui segue l'identita di Tweedie. Il punto strutturale e che il gradiente della densita rumorosa incorpora gia informazione bayesiana sul dato pulito sottostante.

Nel caso dei [[Diffusion Models|diffusion models]] questa relazione e centrale perche collega tre oggetti che spesso vengono parametrizzati in modi diversi ma restano strettamente equivalenti: la score $\nabla_{x_t}\log p_t(x_t)$, la stima del dato pulito $\hat{x}_0(x_t,t)$ e la predizione del rumore $\hat{\epsilon}_{\theta}(x_t,t)$. Se infatti si usa la parametrizzazione standard

$$x_t=\sqrt{\bar{\alpha}_t}\,x_0+\sqrt{1-\bar{\alpha}_t}\,\epsilon$$

allora la versione di Tweedie adattata a questo livello di rumore permette di passare da una stima della score a una stima di $x_0$, e viceversa. In particolare, quando il modello predice il rumore, questa predizione puo essere riscritta come una stima della score della distribuzione rumorosa.

Per questo la Formula di Tweedie fornisce il ponte concettuale tra [[Denoising Autoencoders (DAE)|denoising]], [[Score Function|score matching]] e modelli di diffusione. Un denoiser ben addestrato non restituisce solo una ricostruzione utile, ma induce implicitamente una stima della score; allo stesso modo, una stima della score determina una correzione bayesiana del campione rumoroso verso il dato pulito medio.

Le proprieta operative piu importanti sono:
- trasforma la score della distribuzione rumorosa in una stima del dato pulito condizionato
- rende equivalenti, sotto rumore gaussiano, denoising, score estimation e posterior mean estimation
- spiega perche nei [[Diffusion Models|diffusion models]] predire il rumore e spesso equivalente a modellare la score
