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
Le **Generative Adversarial Networks** sono [[Modelli Generativi|modelli generativi]] impliciti: non imparano una [[Distribuzione di probabilita|densita]] esplicita $p_{\theta}(x)$, ma una procedura di campionamento.

Si parte da una variabile latente semplice $z \sim p_z(z)$, di solito una [[Variabili Aleatorie Notevoli - Gaussiana|gaussiana standard]], e la si trasforma con un generatore:

$$
\tilde{x} = G_{\theta_G}(z)
$$

Il generatore induce una distribuzione $p_G(x)$ sui campioni sintetici, mentre i dati reali seguono $p_{\text{data}}(x)$. Poiche $p_G(x)$ non viene valutata in forma chiusa, l'addestramento non usa direttamente il [[Stima Parametrica - Maximum Liklehood|Maximum Likelihood]] come nei [[Modelli Probabilistici|modelli probabilistici]] espliciti.

Una GAN contiene due reti:
- **Generator** $G_{\theta_G}$: riceve rumore latente e produce campioni sintetici.
- **Discriminator** $D_{\theta_D}$: riceve campioni reali o generati e stima se siano reali.

Il discriminatore risolve un task di [[Concetti generali del Machine Learning|classificazione]]: vuole $D_{\theta_D}(x) \rightarrow 1$ per i dati reali e $D_{\theta_D}(G_{\theta_G}(z)) \rightarrow 0$ per quelli sintetici. Il generatore ha l'obiettivo opposto: produrre campioni tali che $D_{\theta_D}(G_{\theta_G}(z)) \rightarrow 1$.

L'apprendimento e quindi un gioco avversariale: il discriminatore impara a distinguere reale da falso, mentre il generatore impara a produrre campioni sempre piu realistici.
![[IMG - architettura Generative Adversarial Networks (GAN).png]]

La **loss minimax** e:
$$
C_{\text{minimax}} =
\min_{\theta_G} \max_{\theta_D}
\left[
\mathbb{E}_{x \sim p_{\text{data}}}[\log D_{\theta_D}(x)]
+ \mathbb{E}_{z \sim p_z}[\log(1 - D_{\theta_D}(G_{\theta_G}(z)))]
\right]
$$

Il discriminatore massimizza entrambi i termini, assegnando probabilita alta ai campioni reali e bassa a quelli generati. Il generatore minimizza il secondo termine, cercando di rendere grande $D_{\theta_D}(G_{\theta_G}(z))$.

In pratica i due modelli non si ottimizzano simultaneamente, ma con passi alternati:

1. **Discriminator gradient ascent**, fissando $G$:$$
C_D =
\max_{\theta_D}
\left[
\mathbb{E}_{x \sim p_{\text{data}}}[\log D_{\theta_D}(x)]
+ \mathbb{E}_{z \sim p_z}[\log(1 - D_{\theta_D}(G_{\theta_G}(z)))]
\right]
$$

2. **Generator gradient descent**, fissando $D$:$$
C_G =
\min_{\theta_G}
\mathbb{E}_{z \sim p_z}
[\log(1 - D_{\theta_D}(G_{\theta_G}(z)))]
$$

tipicamente all'inizio del training si ha che $D(G(z)) \approx 0$ ovvero si ha che il discriminatore riconosce facilmente i campioni generati come falsi. In questo caso la loss **minimax del generatore** puo essere quasi piatta rispetto a $\theta_G$: il discriminatore e molto sicuro, ma il generatore riceve un gradiente debole. Questo causa il problema dei **vanishing gradients**.

Per evitarlo si usa spesso la **non-saturating loss**: $$C_G^{\text{NS}} = \max_{\theta_G}\mathbb{E}_{z \sim p_z}[\log D_{\theta_D}(G_{\theta_G}(z))]$$ovvero il generatore vuole massimizzare la likelihood del del errore del discriminatore. Questa variante mantiene lo stesso equilibrio desiderato della loss minimax, ma fornisce un segnale di gradiente piu forte quando i campioni generati sono ancora chiaramente falsi.
![[IMG - problematica della soluzione con massimizazione e minimizazione alternati.png]]
La curva **maximum likelihood cost** nella figura non e la loss GAN standard, ma un confronto teorico con la [[Stima Parametrica - Maximum Liklehood|Maximum Likelihood]]. Con Maximum Likelihood si vorrebbe aumentare direttamente la probabilita che il generatore assegna ai dati reali, cioe:
$$
\max_{\theta_G} \mathbb{E}_{x \sim p_{\text{data}}}[\log p_G(x)]
$$
Nelle GAN questa probabilita $p_G(x)$ non e disponibile in forma esplicita. Il collegamento compare tramite il **discriminatore ottimo**.

Fissato il generatore $G$, il discriminatore risolve un problema di classificazione binaria: dato un campione $x$, deve stimare se proviene dai dati reali oppure dal generatore. L'uscita ottimale del discriminatore e quindi la probabilita a posteriori:
$$
D^*(x) = P(\text{reale}\mid x)
$$
Per [[Formula di Bayes|Bayes]]:
$$
P(\text{reale}\mid x)
=
\frac{p(x\mid \text{reale})P(\text{reale})}
{p(x\mid \text{reale})P(\text{reale}) + p(x\mid \text{generato})P(\text{generato})}
$$
Nel training GAN si campionano di solito reali e generati in uguale quantita, quindi $P(\text{reale}) = P(\text{generato}) = \frac{1}{2}$. Inoltre $p(x\mid \text{reale}) = p_{\text{data}}(x)$ e $p(x\mid \text{generato}) = p_G(x)$. Sostituendo:
$$
P(\text{reale}\mid x)
=
\frac{p_{\text{data}}(x)\frac{1}{2}}
{p_{\text{data}}(x)\frac{1}{2} + p_G(x)\frac{1}{2}}
=
\frac{p_{\text{data}}(x)}
{p_{\text{data}}(x) + p_G(x)}
$$
Quindi, per un generatore fissato, il miglior discriminatore possibile e:
$$
D^*(x) = \frac{p_{\text{data}}(x)}{p_{\text{data}}(x) + p_G(x)}
$$
Questa formula dice che $D^*(x)$ e alto quando $x$ e molto piu probabile nei dati reali che nei campioni generati. Riscrivendola si ottiene:
$$
\frac{D^*(x)}{1 - D^*(x)}
=
\frac{p_{\text{data}}(x)}{p_G(x)}
$$
quindi il discriminatore ottimo stima indirettamente il rapporto:
- se $\cfrac{p_{\text{data}}(x)}{p_G(x)}$ e alto, $x$ e molto piu tipico dei dati reali che del generatore;
- se il rapporto e vicino a $1$, il generatore assegna a $x$ una probabilita simile a quella dei dati reali.
In questo senso il discriminatore sostituisce la likelihood esplicita: non calcola direttamente $p_G(x)$, ma fornisce un segnale che dice quanto $p_G$ e vicina a $p_{\text{data}}$.

## Training
Il ciclo interno con $k$ passi e uno stability trick: il discriminatore può essere aggiornato piu volte prima di ogni aggiornamento del generatore. Le medie empiriche $\cfrac{1}{m}\sum_{i=1}^{m}$ stimano le aspettai [[Variabili aleatoria - Valore atteso|valori attesi]] sugli esempi reali e sui rumori latenti.
```pseudo
\begin{algorithm}
\caption{Training di una Generative Adversarial Network}
\begin{algorithmic}
    \For{numero di iterazioni di training}
        \For{$k$ passi}
            \State Campiona un minibatch di $m$ rumori $\{z^{(1)}, \dots, z^{(m)}\}$ dal prior $p_z(z)$
            \State Campiona un minibatch di $m$ esempi reali $\{x^{(1)}, \dots, x^{(m)}\}$ da $p_{\text{data}}(x)$
            \State Aggiorna il discriminatore salendo lungo il gradiente stocastico:
            \State $\displaystyle
            \nabla_{\theta_D}
            \frac{1}{m}
            \sum_{i=1}^{m}
            \left[
            \log D_{\theta_D}(x^{(i)})
            + \log\left(1 - D_{\theta_D}(G_{\theta_G}(z^{(i)}))\right)
            \right]
            $
        \EndFor
        \State Campiona un minibatch di $m$ rumori $\{z^{(1)}, \dots, z^{(m)}\}$ dal prior $p_z(z)$
        \State Aggiorna il generatore salendo lungo il gradiente stocastico dell'obiettivo non saturante:
        \State $\displaystyle
        \nabla_{\theta_G}
        \frac{1}{m}
        \sum_{i=1}^{m}
        \log D_{\theta_D}(G_{\theta_G}(z^{(i)}))
        $
    \EndFor
\end{algorithmic}
\end{algorithm}
```
questo problema di ottimizazione  solitamente un **saddle point** quindi ha bassa stabilita.

Problemi tipici:
- **mode collapse**: molti valori diversi di $z$ vengono mappati in campioni molto simili.
	- ![[IMG - GAN model collapse.png]]
- **scarsa copertura della distribuzione**: il generatore e premiato per ingannare il discriminatore, non per coprire esplicitamente tutti i modi di $p_{\text{data}}$.

# Varianti GAN

## Deep Convolutional GAN

Le **Deep Convolutional GAN** (**DCGAN**) applicano le GAN alla generazione di immagini usando architetture convoluzionali, usano i concetti delle [[Convolutional Neural Network (CNN)|CNN]]. Il generatore proietta il vettore latente in un tensore di feature e aumenta progressivamente la risoluzione tramite convoluzioni trasposte; il discriminatore riduce l'immagine fino a uno score reale/falso.

Se lo spazio latente e organizzato bene, interpolare tra due vettori:

$$
z(\alpha) = (1 - \alpha)z_1 + \alpha z_2
$$

puo produrre transizioni visive coerenti. In alcuni casi si osservano anche operazioni vettoriali empiriche:

$$
z_G = z_1 - z_2 + z_3
$$

Non e garantito dall'obiettivo, ma suggerisce che il generatore possa imparare una rappresentazione strutturata della manifold dei dati, in linea con l'idea di [[Latent Model]].
![[IMG - Deep convolutional Generative Adversarial Networks (GAN).png]]



## Wasserstein GAN

Le **Wasserstein GAN** sostituiscono la loss avversariale classica con un obiettivo basato sulla distanza Wasserstein-1, detta anche Earth Mover's Distance:

$$
W(p_{\text{data}}, p_G)
= \sup_{\lVert D \rVert_L \leq 1}
\left(
\mathbb{E}_{x \sim p_{\text{data}}}[D(x)]
- \mathbb{E}_{z \sim p_z}[D(G(z))]
\right)
$$

In WGAN il discriminatore diventa un **critic**: non produce una probabilita, ma uno score reale. Il vantaggio e che la distanza Wasserstein puo dare gradienti informativi anche quando $p_{\text{data}}$ e $p_G$ hanno poco overlap. Il vincolo centrale e che il critic sia 1-Lipschitz:

$$
|D(x) - D(x')| \leq \lVert x - x' \rVert
$$

Le prime WGAN usavano weight clipping; versioni successive usano spesso gradient penalty.

## Progressive GAN

Le **Progressive GAN** stabilizzano la generazione ad alta risoluzione partendo da immagini piccole e aumentando progressivamente la dimensione:

$$
4 \times 4 \rightarrow 8 \times 8 \rightarrow 16 \times 16 \rightarrow \cdots
$$

I nuovi layer vengono inseriti gradualmente: il modello impara prima la struttura globale e poi i dettagli fini.

## Conditional GAN

Le **Conditional GAN** introducono una condizione $y$ nel processo generativo:

$$
G(y, z) \rightarrow \tilde{x}
$$

Il discriminatore riceve anche la condizione, quindi valuta sia il realismo sia la coerenza con $y$. Nel caso image-to-image translation si puo scrivere:

$$
G(x, z) \rightarrow y
$$

Esempi: generazione condizionata dalla classe, text-to-image, colorazione di immagini grayscale, trasformazione giorno-notte, traduzione da mappe semantiche a immagini realistiche.

## CycleGAN

Le **CycleGAN** affrontano la traduzione image-to-image senza coppie allineate. Dati due domini $A$ e $B$, il modello impara due trasformazioni:

$$
G_{A \rightarrow B}: A \rightarrow B
$$

$$
G_{B \rightarrow A}: B \rightarrow A
$$

Le loss avversariali rendono realistici i campioni nel dominio di arrivo. La **cycle consistency** evita trasformazioni degeneri:

$$
G_{B \rightarrow A}(G_{A \rightarrow B}(x_A)) \approx x_A
$$

$$
G_{A \rightarrow B}(G_{B \rightarrow A}(x_B)) \approx x_B
$$

In questo modo la traduzione tende a preservare il contenuto dell'input invece di mappare molti input diversi nello stesso output plausibile.

