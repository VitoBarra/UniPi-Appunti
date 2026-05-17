---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area:
topic:
SubTopic:
---

# Modelli Probabilistici
---
Un **modello probabilistico** è un modello che descrive i dati tramite una o più [[Distribuzione di probabilita|distribuzioni di probabilità]].

Invece di limitarsi a produrre un output deterministico, assegna probabilità a eventi, osservazioni o variabili latenti. Per esempio può modellare:
- una distribuzione sui dati, come $p(x)$;
- una distribuzione condizionata, come $p(y \mid x)$;
- una distribuzione con variabili latenti, come $p(x,z)=p(z)p(x \mid z)$.

Nel contesto del [[Generative and Deep Learning (GDL)]], molti modelli generativi sono anche probabilistici, perché descrivono come i dati vengono generati da una distribuzione.

## Modelli generativi
I [[Modelli Generativi|modelli generativi]] non sono tutti probabilistici nello stesso modo:
- i **modelli generativi espliciti** definiscono direttamente una distribuzione, quindi sono modelli probabilistici in senso pieno;
- i **modelli generativi impliciti** definiscono soprattutto una procedura di sampling, che induce una distribuzione sui campioni ma spesso senza una densità esplicita o trattabile.

Per questo un modello come un [[Variational Autoencoder (VAE)|VAE]] è un modello probabilistico esplicito, mentre una [[Generative Adversarial Networks (GAN)|GAN]] è generativa ma non fornisce in generale una likelihood esplicita dei dati.

## Esempi
- Un [[Denoising Autoencoders (DAE)|DAE]] può avere una lettura probabilistica tramite la distribuzione condizionata $P(x \mid \hat{x})$.
- Un [[Variational Autoencoder (VAE)|VAE]] definisce esplicitamente un modello latente probabilistico $p_\theta(x,z)$.
- Un [[Mixture Models|mixture model]] descrive i dati come combinazione di più componenti probabilistiche.
