---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area: Modelli Generativi
topic: Continuous-time generative models
SubTopic:
---
# Flow Matching
---
Il **Flow Matching** e un metodo per addestrare modelli generativi continui imparando direttamente il [[Campo vettoriale|campo vettoriale]] che trasporta i campioni da una distribuzione iniziale semplice alla distribuzione dei dati. Il suo oggetto centrale non e quindi la densita in forma chiusa e nemmeno la [[Score Function|score]], ma la dinamica continua che descrive come ogni punto deve muoversi nel tempo.

Per definizione, il problema si costruisce introducendo una famiglia continua di distribuzioni intermedie $p_t(x)$, con $t\in[0,1]$, dove $p_0$ e tipicamente una distribuzione semplice, per esempio gaussiana, e $p_1$ e la distribuzione dei dati. Invece di rappresentare il trasporto come composizione di trasformazioni discrete, si definisce una dinamica continua tramite una [[Ordinary Differential Equation (ODE)|ordinary differential equation]] in cui $x$ e lo stato del campione al tempo $t$ e $v_t(x)$ e il campo di velocita:$$\frac{dx}{dt}=v_t(x)$$Operativamente, questa equazione dice che il campione evolve lungo una traiettoria la cui direzione istantanea e specificata dal campo $v_t(x)$. Conoscere il campo significa quindi conoscere la legge locale di movimento che realizza il trasporto probabilistico.

Il problema di learning si definisce allora introducendo un modello parametrico $v_{\theta}(x,t)$, dove $\theta$ sono i parametri della rete, $x$ e la posizione del campione e $t$ e il tempo, e imponendo che esso approssimi un campo target $v_t^*(x)$ compatibile con la probability path scelta:$$v_{\theta}(x,t)\approx v_t^*(x)$$Il significato operativo e che il training non stima direttamente una likelihood esatta e non ricostruisce una mappa inversa globale, ma esegue una regressione locale sul vettore di trasporto corretto in ogni coppia punto-tempo.

La quantita strutturale piu importante si definisce quindi come **probability path**. Si sceglie una famiglia di distribuzioni $p_t(x)$ che collega rumore e dati, e insieme a questa si costruisce un campo target coerente con il percorso. Una formulazione molto usata consiste nel considerare una coppia $(x_0,x_1)$, dove $x_0$ e un campione iniziale di rumore e $x_1$ un campione dato, e nel definire un'interpolazione continua tra i due. In questa lettura il modello non apprende direttamente la distribuzione finale, ma la dinamica locale che rende possibile raggiungerla.

![[IMG - Flow-Matching.png]]

Se la probability path viene costruita tramite un'interpolazione particolarmente semplice tra $x_0$ e $x_1$, per esempio quasi lineare, anche il campo target tende a diventare piu regolare. Questo rende piu trasparente il significato del training, perche la rete non deve inferire indirettamente una struttura complessa della densita, ma approssimare vettori di spostamento che descrivono direttamente come i campioni devono muoversi lungo il percorso scelto.

![[IMG - Flow-Matching percorso in linea retta.png]]

La relazione tra densita e campo di velocita si esprime formalmente tramite l'equazione di continuita. Se $p_t(x)$ e la densita al tempo $t$ e $v_t(x)$ e il campo che trasporta la massa di probabilita, allora si definisce$$\partial_t p_t(x)+\nabla_x\cdot\bigl(p_t(x)\,v_t(x)\bigr)=0$$Questa equazione rappresenta la conservazione della massa lungo il flusso. Operativamente, impone che il campo $v_t(x)$ non muova i punti in modo arbitrario, ma deformi la distribuzione nel tempo in modo coerente con la path probabilistica prescelta.

Una formulazione equivalente del quadro concettuale consiste nel dire che il flow matching apprende direttamente una dinamica deterministica continua, mentre altri approcci, come quelli basati su [[Stochastic Differential Equations (SDE)|stochastic differential equations]], descrivono prima un'evoluzione stocastica e solo successivamente ne ricavano una dinamica deterministica equivalente. L'immagine seguente va letta proprio in questo senso: mostra che una dinamica score-based puo essere formulata inizialmente come [[Stochastic Differential Equations (SDE)|SDE]] e poi riscritta come [[Ordinary Differential Equation (ODE)|ODE]] di probability flow, cioe come un trasporto continuo della distribuzione senza rumore esplicito nelle traiettorie. Per questo il flow matching e vicino ai [[Normalizing Flows|normalizing flows]] continui, ma non richiede di partire da blocchi invertibili discreti.

![[IMG - da SDEs a ODEs Score and Flow-Matching.png]]

Il legame con i [[Diffusion Models|diffusion models]] esiste, ma va interpretato con precisione. Nei diffusion models tradizionali si apprende spesso informazione di denoising o di score su una famiglia di distribuzioni rumorose, spesso interpretabile in tempo continuo tramite [[Stochastic Differential Equations (SDE)|SDE]]; nel flow matching si apprende invece direttamente una velocita deterministica. Le due prospettive possono produrre la stessa evoluzione delle distribuzioni, ma il bersaglio di training resta diverso: da una parte un denoiser o una score, dall'altra un velocity field.

Una variante importante si definisce come **conditional flow matching**. In questo caso il campo non viene appreso solo in media tra due distribuzioni globali, ma condizionatamente a informazione aggiuntiva o a una specifica coppia iniziale-finale. Operativamente questo rende il target di training piu strutturato, perche il modello apprende un trasporto locale coerente con una relazione condizionata esplicita.

![[IMG - condizionamento Flow-Matching.png]]

Rispetto a [[Score Matching|score matching]], il flow matching non stima il gradiente della log-densita ma direttamente la velocita del trasporto.  Rispetto ai diffusion models discreti, fornisce una formulazione piu diretta del trasporto continuo in termini di campi vettoriali e [[Ordinary Differential Equation (ODE)|ODE]].

Le proprieta operative piu importanti sono:
- apprende direttamente un campo di velocita $v_t(x)$ invece della [[Score Function|score]]
- separa chiaramente probability path e parametrizzazione della dinamica
- usa naturalmente una formulazione continua basata su [[Ordinary Differential Equation (ODE)|ODE]]
