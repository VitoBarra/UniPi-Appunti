---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area: Modelli Generativi
topic: GAN
SubTopic:
---

# Generative Adversarial Networks (GAN)
---
Le **Generative Adversarial Networks** sono [[Modelli Generativi|modelli generativi]] impliciti: non imparano una [[Distribuzione di probabilita|densita]] esplicita $p_{\theta}(x)$, ma una procedura di campionamento capace di generare nuovi esempi.

L'idea e partire da una variabile latente semplice $z \sim p(z)$, di solito una [[Variabili Aleatorie Notevoli - Gaussiana|gaussiana standard]], e trasformarla tramite un generatore $G_{\theta_G}$:$$\tilde{x} = G_{\theta_G}(z)$$Il modello induce quindi una distribuzione $p_G(\tilde{x})$ sui campioni generati, ma questa distribuzione non viene valutata in forma chiusa. Per questo l'addestramento non usa direttamente il [[Maximum likelihood learning]], a differenza di molti [[Modelli Probabilistici|modelli probabilistici]] espliciti.
Una GAN contiene due reti:
- **Generator** $G_{\theta_G}$: riceve rumore latente e produce campioni sintetici
- **Discriminator** $D_{\theta_D}$: riceve campioni reali o generati e stima se siano reali
Il **discriminatore** risolve un task di [[Concetti generali del Machine Learning|classificazione]]: vuole $D(x) \rightarrow 1$ per i dati reali e $D(G(z)) \rightarrow 0$ per i dati sintetici. Il **generatore**, invece, ha il task opposto: vuole $D(G(z)) \rightarrow 1$.

L'apprendimento e quindi un gioco avversariale: il discriminatore migliora nel distinguere reale da falso, mentre il generatore migliora nel produrre campioni sempre piu realistici.
![[IMG - architettura Generative Adversarial Networks (GAN).png]]

L'**funzione obiettivi** da ottimizzare delle **GAN** è:$$
C = \min_{\theta_G} \max_{\theta_D}
\left[
\mathbb{E}_{x \sim p_{\text{data}}}[\log D_{\theta_D}(x)]
+ \mathbb{E}_{z \sim p(z)}[\log(1 - D_{\theta_D}(G_{\theta_G}(z)))]
\right]
$$
Il **discriminatore massimizza** entrambi i termini: 
- assegna [[Definizione di Probabilita|probabilita]] alta ai campioni reali 
- assegna [[Definizione di Probabilita|probabilita]] bassa ai campioni prodotti dal generatore.
Il **generatore minimizza** il secondo termine cercando di rendere grande $D(G(z))$.

L'obiettivo minimax non viene risolto ottimizzando simultaneamente i due modelli, ma alternando due passi:
1. **Discriminator gradient ascent**: si fissa il generatore e si aggiorna solo $\theta_D$: $$
C_D =
\max_{\theta_D}
\left[
\mathbb{E}_{x \sim p_{\text{data}}}[\log D_{\theta_D}(x)]
+ \mathbb{E}_{z \sim p(z)}[\log(1 - D_{\theta_D}(G_{\theta_G}(z)))]
\right]
$$
2. **Generator gradient descent**: si fissa il discriminatore e si aggiorna solo $\theta_G$: $$
C_G =
\min_{\theta_G}
\mathbb{E}_{z \sim p(z)}
[\log(1 - D_{\theta_D}(G_{\theta_G}(z)))]
$$
Il costo ricevuto dal generatore per il campione $G_{\theta_G}(z)$ dipende solo dalla risposta del discriminatore $D_{\theta_D}(G_{\theta_G}(z))$. Se il **discriminatore classifica** il campione come falso con alta confidenza, il generatore riceve un segnale che lo spinge a modificare i propri parametri per produrre campioni più realistici. 
![[IMG - problematica della soluzione con massimizazione e minimizazione alternati.png]]
Per un generatore fissato, il discriminatore ottimo e:$$D^*(x) = \frac{p_{\text{data}}(x)}{p_{\text{data}}(x) + p_G(x)}$$Questa forma collega la teoria delle **GAN** alla minimizzazione di divergenze tra distribuzioni, in particolare alla Jensen-Shannon divergence, [[kullback-Leibler (KL) Divergence]] e [[Jensen inequality]].

La loss minimax del generatore e:

$$
J_G = \mathbb{E}_{z \sim p(z)}[\log(1 - D(G(z)))]
$$

All'inizio del training il discriminatore puo essere molto forte, quindi $D(G(z)) \approx 0$. In questo caso la loss satura e il generatore riceve gradienti deboli. Per questo si usa spesso la **non-saturating loss**:

$$
J_G^{\text{NS}} = -\mathbb{E}_{z \sim p(z)}[\log D(G(z))]
$$

L'equilibrio desiderato resta lo stesso, ma il segnale di gradiente e piu utile quando i campioni generati sono ancora facilmente riconoscibili come falsi.

Il training di una GAN non e una minimizzazione ordinaria, ma un problema a sella: i due modelli ottimizzano obiettivi opposti e vengono aggiornati alternatamente. Questo puo produrre oscillazioni, squilibri locali e mancata convergenza.

Problemi tipici:
- **vanishing gradients**: il discriminatore diventa troppo forte e il generatore non riceve un segnale utile
- **mode collapse**: molti valori diversi di $z$ vengono mappati in campioni molto simili
- **scarsa copertura della distribuzione**: il generatore e premiato per ingannare il discriminatore, non per coprire esplicitamente tutti i modi di $p_{\text{data}}$

Le **Deep Convolutional GAN** applicano le GAN alla generazione di immagini usando architetture convoluzionali, collegandosi direttamente alle [[Convolutional Neural Network  (CNN)]]. Il generatore parte da un vettore latente, lo proietta in un tensore di feature e poi aumenta progressivamente la risoluzione tramite convoluzioni trasposte. Il discriminatore fa l'operazione opposta: riduce progressivamente l'immagine fino a produrre uno score reale/falso.

Se lo spazio latente e organizzato bene, interpolare tra due vettori:

$$
z(\alpha) = (1 - \alpha)z_1 + \alpha z_2
$$

puo produrre transizioni visive coerenti dopo la decodifica con $G$. In alcuni casi si osservano anche operazioni vettoriali empiriche:

$$
z_G = z_1 - z_2 + z_3
$$

Questo non e garantito dall'obiettivo, ma suggerisce che il generatore possa imparare una rappresentazione strutturata della manifold dei dati, in linea con l'idea di [[Latent Model]].

Le **Wasserstein GAN** sostituiscono la loss avversariale classica con un obiettivo basato sulla distanza Wasserstein-1, detta anche Earth Mover's Distance:

$$
W(p_{\text{data}}, p_G)
= \sup_{\lVert D \rVert_L \leq 1}
\left(
\mathbb{E}_{x \sim p_{\text{data}}}[D(x)]
- \mathbb{E}_{z \sim p(z)}[D(G(z))]
\right)
$$

In WGAN il discriminatore diventa un **critic**: non produce una probabilita, ma uno score reale. Il vantaggio e che la distanza Wasserstein puo dare gradienti informativi anche quando $p_{\text{data}}$ e $p_G$ hanno poco overlap. Il vincolo centrale e che il critic deve essere 1-Lipschitz:

$$
|D(x) - D(x')| \leq \lVert x - x' \rVert
$$

Le prime WGAN imponevano questo vincolo con weight clipping; versioni successive usano spesso gradient penalty.

Le **Progressive GAN** stabilizzano la generazione ad alta risoluzione partendo da immagini piccole e aumentando progressivamente la dimensione:

$$
4 \times 4 \rightarrow 8 \times 8 \rightarrow 16 \times 16 \rightarrow \cdots
$$

I nuovi layer vengono inseriti gradualmente: il modello impara prima la struttura globale e poi i dettagli fini.

Le **Conditional GAN** introducono una condizione $y$ nel processo generativo:

$$
G(y, z) \rightarrow \tilde{x}
$$

Il discriminatore riceve anche la condizione, quindi deve valutare se il campione sia sia realistico sia coerente con $y$. Nel caso image-to-image translation si puo scrivere:

$$
G(x, z) \rightarrow y
$$

Esempi: generazione condizionata dalla classe, text-to-image, colorazione di immagini grayscale, trasformazione giorno-notte, traduzione da mappe semantiche a immagini realistiche.

Le **CycleGAN** affrontano la traduzione image-to-image senza coppie allineate. Dati due domini $A$ e $B$, il modello impara due trasformazioni:

$$
G_{A \rightarrow B}: A \rightarrow B
$$

$$
G_{B \rightarrow A}: B \rightarrow A
$$

Le loss avversariali rendono realistici i campioni nel dominio di arrivo. La cycle consistency evita trasformazioni degeneri:

$$
G_{B \rightarrow A}(G_{A \rightarrow B}(x_A)) \approx x_A
$$

$$
G_{A \rightarrow B}(G_{B \rightarrow A}(x_B)) \approx x_B
$$

In questo modo la traduzione tende a preservare il contenuto dell'input invece di mappare molti input diversi nello stesso output plausibile.

Gli **Adversarial Autoencoder** combinano ricostruzione da autoencoder e regolarizzazione avversariale dello spazio latente. Il training alterna una fase di **reconstruction**, in cui encoder e decoder minimizzano l'errore di ricostruzione, e una fase di **regularization**, in cui un discriminatore nello spazio latente distingue campioni dal prior da codifiche prodotte dall'encoder. L'effetto e far coincidere la distribuzione aggregata delle codifiche con un prior scelto, senza richiedere una KL in forma chiusa come nei modelli variazionali.

In sintesi, le GAN imparano a campionare dati realistici senza modellare una densita esplicita. Sono efficaci nella generazione di immagini, ma difficili da addestrare per via della dinamica avversariale. Le varianti principali migliorano aspetti diversi: WGAN rende il segnale di training piu stabile, DCGAN adatta il modello alle immagini, Progressive GAN scala a risoluzioni maggiori, Conditional GAN controlla la generazione e CycleGAN permette traduzione tra domini senza coppie allineate.
