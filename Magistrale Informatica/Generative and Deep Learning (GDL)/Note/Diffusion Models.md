---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area: Modelli Generativi
topic: Score-based models
SubTopic:
---
# Diffusion Models
---
I **Diffusion Models** sono [[Modelli Generativi|modelli generativi]] che imparano a generare dati invertendo gradualmente un processo di corruzione con rumore.

L'idea di base e partire da un dato reale $x_0 \sim p_{\text{data}}(x)$ e costruire una sequenza di versioni sempre piu rumorose $$x_0, x_1, x_2, \dots, x_T$$ fino ad arrivare a una distribuzione finale semplice, in genere una [[Variabili Aleatorie Notevoli - Gaussiana multivariata|gaussiana multivariata]] quasi isotropa. Il modello non prova quindi a generare direttamente il dato finale in un solo passo, ma impara una procedura di **denoising progressivo**.

Questa idea e collegata direttamente ai [[Denoising Autoencoders (DAE)|Denoising Autoencoders]]. Anche nei DAE si aggiunge rumore a un dato e si impara a ricostruirlo. I **Diffusion Models** estendono questa intuizione a molti livelli di rumore e la trasformano in un vero modello generativo.
![[IMG - Diffusion Model forward(encoder) e reverse(decoder).png]]

## Processo forward
Il processo forward, o **diffusion process**, aggiunge rumore poco alla volta. In una formulazione discreta si scrive: $$q(x_t \mid x_{t-1}) = \mathcal{N}(x_t \mid \sqrt{1-\beta_t}\,x_{t-1}, \beta_t I)$$dove $\beta_t$ controlla quanta corruzione si aggiunge allo step $t$. Ogni passaggio conserva una parte del segnale precedente e aggiunge una piccola quantità di rumore gaussiano.

Dopo molti passi, l'informazione originaria viene progressivamente distrutta e la distribuzione di $x_T$ si avvicina a una gaussiana semplice. Questo rende il problema generativo piu accessibile:
- in avanti si sa esattamente come sporcare i dati;
- all'indietro si vuole imparare come rimuovere il rumore.
![[IMG - Diffusion Models aggiunta di rimore formward.png]]
Grazie alla struttura gaussiana, si puo anche scrivere direttamente $x_t$ in funzione di $x_0$:$$x_t = \sqrt{\bar{\alpha}_t}\,x_0 + \sqrt{1-\bar{\alpha}_t}\,\epsilon, \qquad \epsilon \sim \mathcal{N}(0,I)$$dove $\alpha_t = 1-\beta_t$ e $\bar{\alpha}_t = \prod_{s=1}^{t}\alpha_s$. Questa formula dice che ogni stato rumoroso e una combinazione del dato pulito e di rumore gaussiano.

Questa scrittura si interpreta come la **versione kernelizzata** del forward process, perche definisce direttamente il kernel gaussiano che porta dal dato pulito alla sua versione rumorosa al tempo $t$. Formalmente si definisce

$$q(x_t\mid x_0)=\mathcal{N}\left(x_t\mid \sqrt{\bar{\alpha}_t}\,x_0,(1-\bar{\alpha}_t)I\right)$$

cioe la distribuzione di $x_t$ ottenuta saltando tutti gli step intermedi della catena di Markov. Operativamente questa forma e cruciale, perche permette di campionare direttamente un livello di rumore arbitrario senza simulare esplicitamente tutti i passaggi $x_1,\dots,x_{t-1}$. Per questo il training puo scegliere un tempo $t$ a caso, costruire subito il corrispondente campione rumoroso e addestrare la rete in parallelo su livelli di rumore diversi.
![[IMG - Evoluzione distribuzione in diffusion model.png]]
## Processo reverse
Il problema generativo vero e imparare il processo opposto, cioe una catena che trasformi il rumore in dato: $$p_{\theta}(x_{t-1}\mid x_t)$$Se si conoscesse esattamente questa distribuzione condizionata per ogni livello di rumore, allora si potrebbe:
- campionare prima $x_T \sim \mathcal{N}(0,I)$
- applicare ripetutamente il processo reverse
- ottenere infine un campione $x_0$ plausibile
Il punto delicato e che il reverse non e noto a priori, quindi viene approssimato con una rete neurale, usando una [[U-Net|U-Net]] e il [[Time Embedding|time embedding]] per distinguere i vari stage di rumore.
![[IMG - u-net con res net e self attention.png]]



## Obiettivo di training
Una parametrizzazione molto comune sceglie una rete $\epsilon_{\theta}(x_t,t)$ che, dato un campione rumoroso e il livello di rumore, prova a ricostruire il rumore usato per corromperlo. La loss tipica e:$$\mathcal{L}(\theta)=\mathbb{E}_{x_0,t,\epsilon}\left[\|\epsilon-\epsilon_{\theta}(x_t,t)\|_2^2\right]$$dove $x_t$ e ottenuto dal processo forward. Questa loss ha una forma semplice, ma in realta addestra il modello a fare denoising a tutti i livelli di rumore.

Quindi il training dei **Diffusion Models** puo essere letto in due modi equivalenti:
- come apprendimento di un denoiser multiscala;
- come apprendimento della score delle distribuzioni rumorose, cioe come caso particolare di [[Score Matching|score matching]].

## Generazione
Una volta addestrato il modello, la generazione parte dal rumore puro e procede all'indietro: $$x_T \rightarrow x_{T-1} \rightarrow \dots \rightarrow x_1 \rightarrow x_0$$A ogni passo il modello usa il campione corrente $x_t$ e il tempo $t$ per stimare come rimuovere una parte del rumore. Il risultato finale non viene generato in un solo salto, ma emerge da una lunga sequenza di raffinamenti successivi.

Questa procedura ha due conseguenze importanti:
- il sampling e spesso molto stabile;
- ma puo essere piu lento rispetto ad altri modelli generativi, perche richiede molti passi sequenziali.
![[IMG - Generazione immagini ad alta risoluzione.png]]

## Interpretazione geometrica
Geometricamente, i **Diffusion Models** descrivono una traiettoria che parte da una distribuzione molto semplice e ritorna gradualmente verso la distribuzione dei dati. A ogni livello di rumore, il modello stima un [[Campo vettoriale|campo vettoriale]] che indica come spostare i campioni per aumentare la plausibilita.

Questo punto di vista si collega bene alla [[Manifold Hypothesis]]. Se i dati reali si trovano vicino a una manifold di dimensione piu bassa immersa nello spazio ad alta dimensionalita, allora il processo forward spinge progressivamente i campioni lontano da questa regione strutturata, mentre il processo reverse impara a riportarli verso regioni sempre piu plausibili del data manifold.

In questa lettura, il denoising non va visto solo come rimozione di rumore pixel per pixel, ma come una dinamica che riavvicina il campione a una struttura geometrica coerente con i dati osservati.
![[IMG - Diffusion Models come percorso da rumore al data manifold.png]]
In questo senso i modelli di diffusione non costruiscono la densita tramite una trasformazione invertibile singola come nei [[Normalizing Flows]], ma tramite una dinamica di denoising progressivo.


## Diffusion model nel framework dello score matching
I **Diffusion Models** entrano nel framework dello [[Score Matching|score matching]] quando si osserva che il denoising a tempo $t$ equivale a stimare la [[Score Function|score function]] della distribuzione rumorosa $p_t(x_t)$. La quantita rilevante e quindi il campo

$$\nabla_{x_t}\log p_t(x_t)$$

che, per definizione, indica come correggere localmente un campione rumoroso $x_t$ verso regioni di maggiore densita.

Il passaggio chiave si ottiene applicando la [[Formula di Tweedie|formula di Tweedie]] al processo forward gaussianizzato dei diffusion models. Se il campione rumoroso soddisfa

$$x_t=\sqrt{\bar{\alpha}_t}\,x_0+\sqrt{1-\bar{\alpha}_t}\,\epsilon, \qquad \epsilon\sim\mathcal{N}(0,I)$$

allora la variabile osservata $x_t$, condizionata a $x_0$, e gaussiana con media $\sqrt{\bar{\alpha}_t}\,x_0$ e varianza $(1-\bar{\alpha}_t)I$. Tweedie dice quindi che la media a posteriori del dato denoised scalato si definisce come

$$\mathbb{E}\!\left[\sqrt{\bar{\alpha}_t}\,x_0 \mid x_t\right]=x_t+(1-\bar{\alpha}_t)\nabla_{x_t}\log p_t(x_t)$$

dove il primo termine $x_t$ e il campione rumoroso osservato, il secondo termine $(1-\bar{\alpha}_t)$ misura la varianza introdotta dal forward process e il gradiente $\nabla_{x_t}\log p_t(x_t)$ e precisamente la score della distribuzione rumorosa al tempo $t$. Operativamente questa formula dice che il denoised sample si ottiene correggendo $x_t$ lungo la direzione indicata dalla score.

Risolvendo rispetto a $x_0$ si ottiene una forma equivalente piu esplicita:

$$x_0=\frac{x_t+(1-\bar{\alpha}_t)\nabla_{x_t}\log p_t(x_t)}{\sqrt{\bar{\alpha}_t}}$$

Questa scrittura mostra che conoscere la score e sufficiente per costruire una stima del dato pulito. In questo senso i [[Diffusion Models|diffusion models]] non imparano solo a sottrarre rumore, ma apprendono un campo vettoriale dipendente dal tempo sullo spazio dei dati.

La formulazione pratica usata nel modello introduce poi la versione kernelizzata del denoising. Dalla rappresentazione diretta del forward process si ricava infatti$$x_0=\frac{x_t-\sqrt{1-\bar{\alpha}_t}\,\epsilon_t}{\sqrt{\bar{\alpha}_t}}$$dove $\epsilon_t$ e il rumore che ha generato il campione rumoroso $x_t$. Confrontando questa espressione con la forma ottenuta da Tweedie si ricava immediatamente la relazione$$\nabla_{x_t}\log p_t(x_t)=-\frac{\epsilon_t}{\sqrt{1-\bar{\alpha}_t}}$$e, sostituendo la predizione neurale $\epsilon_{\theta}(x_t,t)$ al rumore ignoto, si ottiene la stima operativa della score:$$\nabla_{x_t}\log p_t(x_t)\approx-\frac{\epsilon_{\theta}(x_t,t)}{\sqrt{1-\bar{\alpha}_t}}$$Questa e la forma che rende esplicito il legame tra predizione del rumore e [[Score Matching|score matching]]: addestrare la rete a predire $\epsilon_t$ equivale ad addestrarla a rappresentare la score delle distribuzioni intermedie rumorose. Muoversi in direzione opposta al rumore aggiunto equivale quindi a muoversi nella direzione che massimizza la log-densita locale.

![[IMG - Diffusion Models come score metching.png]]


## Varianti e applicazioni
Molte estensioni moderne dei **Diffusion Models** sfruttano la stessa idea di denoising progressivo, ma la applicano in contesti piu strutturati:
- **conditional generation**, in cui il processo viene guidato da una condizione esterna come una classe o un testo;
- **cascaded generation**, in cui si genera prima una versione grossolana e poi la si raffina a risoluzioni piu alte;
- **latent diffusion**, in cui il processo di diffusione non avviene direttamente nello spazio dei pixel ma in uno spazio latente piu compatto

Queste varianti mantengono l'intuizione centrale del modello, ma riducono il costo computazionale o aumentano il controllo sul contenuto generato.
![[IMG - Conditinal GenerationDiffusion Models.png]]
![[IMG - cascade coditional generation.png]]
![[IMG - latent space diffusion model.png]]
![[IMG - DALL E2 architecture.png]]

## Limiti
I **Diffusion Models** hanno alcuni limiti pratici:
- il sampling puo richiedere molti step;
- il training dipende dalla scelta della noise schedule $\beta_t$;
- il modello non fornisce la stessa likelihood esatta dei [[Normalizing Flows]];
- la teoria e l'implementazione sono piu complesse di un semplice autoencoder.
Nonostante questo, i **Diffusion Models** sono diventati molto importanti perché combinano buona qualità dei campioni, training stabile e un forte legame teorico con denoising e [[Score Function|score-based modeling]].
