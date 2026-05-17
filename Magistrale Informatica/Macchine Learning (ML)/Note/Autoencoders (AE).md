---
Course: "[[Machine Learning (ML)]]"
Corse 1: "[[Generative and Deep Learning (GDL)]]"
tags:
  - IIA
  - ML
  - GDL
Area: Modelli Generativi
topic: Autoencoders
SubTopic:
---
# Reti neurali - Autoencoders
---
Gli **autoencoders** sono un particolare tipo di [[NN - Autoassociatore|autoassociatore]], cioè una [[Reti Neurali (NN)|rete neurale]] allenata per riprodurre l'input sul proprio output. Il task è [[Algoritmi di learning NON supervisionato|non supervisionato]] o, più precisamente, **self-supervised**: il target usato per il training è lo stesso dato in ingresso.

L'obiettivo generale una **rappresentazione latente** $z$ che conservi le informazioni importanti e scarti **rumore, ridondanza e variazioni irrilevanti**.

Gli autoencoders sono definiti da una architettura **encoder-decoder**:
- **Encoder** $f_{\theta}$: trasforma l'input in una rappresentazione latente $z$;
- **Decoder** $g_{\phi}$: riconverte la rappresentazione latente in una ricostruzione del dato originale $\tilde{x}$.
Formalmente:$$
z = f_{\theta}(x) \quad \quad
\tilde{x} = g_{\phi}(z)$$L'intero autoencoder può essere visto come una [[Funzioni|funzione composta]]:$$\tilde{x} = g_{\phi}(f_{\theta}(x))$$
l architettura generale è quindi: ![[IMG - architettura autoencoders.png]]
Allenare la rete significa minimizzare un errore di ricostruzione:$$\min_{\theta,\phi}\mathcal{L}(x, g_{\phi}(f_{\theta}(x)))$$dove $\mathcal{L}$ misura quanto la ricostruzione $\tilde{x}$ è distante dall'input $x$

La reconstruction loss da sola non basta. Se la rete ha troppa capacità, può imparare quasi una funzione identità e copiare l'input senza estrarre una rappresentazione utile.

Serve quindi un **bottleneck**, cioè un vincolo che renda la ricostruzione non banale. Il bottleneck può essere ottenuto in vari modi:
- usare uno spazio latente di dimensione $K$ più piccola rispetto all'input $D$, cioè $K \ll D$;
- imporre sparsità sulle attivazioni latenti, come nello [[Sparse Autoencoders (SAE)|SAE]]
- corrompere l'input e chiedere di ricostruire il dato pulito come nel [[Denoising Autoencoders (DAE)|DAE]] 
- penalizzare la sensibilità dell'encoder;
- usare dropout o altre forme di regolarizzazione.
Il bottleneck costringe l'encoder a conservare solo i fattori di **variazione utili** a spiegare molti esempi del dataset.