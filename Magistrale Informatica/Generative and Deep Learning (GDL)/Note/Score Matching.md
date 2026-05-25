---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area: Modelli Generativi
topic: Score-based models
SubTopic:
---
# Score Matching
---
Lo **Score Matching** e un criterio di apprendimento per modelli probabilistici che punta a stimare la [[Score Function|score function]] di una distribuzione invece della sua densita normalizzata esplicita. La quantita centrale si definisce, per una distribuzione $p(x)$ sufficientemente regolare, come $$s(x)=\nabla_x \log p(x)$$dove $s(x)$ e la score e indica, in ogni punto dello spazio, la direzione di massima crescita della log-densita. Operativamente questo significa che la score descrive la geometria locale della distribuzione anche quando il termine di normalizzazione di $p(x)$ e ignoto o intrattabile.

Il punto chiave e che molti modelli energetici o impliciti possono definire una densita solo fino a una costante moltiplicativa. Se si scrive infatti$$p_{\theta}(x)=\frac{1}{Z_{\theta}} \exp(-E_{\theta}(x))$$con $E_{\theta}(x)$ energia e $Z_{\theta}$ costante di normalizzazione, allora calcolare direttamente la likelihood richiede conoscere $Z_{\theta}$, che in alta dimensionalita e spesso intrattabile. La score evita questo ostacolo, perche derivando il logaritmo la costante scompare: $$\nabla_x \log p_{\theta}(x)= -\nabla_x E_{\theta}(x)$$Quindi si puo apprendere un campo di direzioni locali senza dover normalizzare esplicitamente la distribuzione.

Per definizione, lo score matching confronta la score del modello con la score della distribuzione vera dei dati. La forma ideale dell'obiettivo sarebbe$$
\mathcal{J}(\theta)=\mathbb{E}_{p_{\text{data}}(x)}\left[\left\|s_{\theta}(x)-\nabla_x \log p_{\text{data}}(x)\right\|_2^2\right]
$$ma la score vera dei dati non e disponibile. Il risultato classico di Hyvarinen mostra che, sotto ipotesi regolari, questo obiettivo si puo riscrivere in una forma equivalente che dipende solo dalla score del modello e dai dati osservati:$$
\mathcal{J}(\theta)=\mathbb{E}_{p_{\text{data}}(x)}\left[\frac{1}{2}\|s_{\theta}(x)\|_2^2+\operatorname{div}s_{\theta}(x)\right]+\text{costante}
$$dove $\operatorname{div}s_{\theta}(x)$ e la divergenza del campo vettoriale score. Il significato operativo e che il modello viene addestrato a costruire un campo che, localmente, abbia la stessa struttura differenziale della distribuzione dei dati.

Questa idea e diventata particolarmente importante nei modelli generativi moderni nella variante di **denoising score matching**. In questo caso non si apprende la score della distribuzione pulita direttamente, ma la score di distribuzioni rumorose ottenute corrompendo i dati. Se si introduce una variabile rumorosa $x_t$ ottenuta da un dato pulito $x_0$ tramite rumore gaussiano, allora il modello apprende $$s_{\theta}(x_t,t)\approx \nabla_{x_t}\log p_t(x_t)$$dove $p_t(x_t)$ e la distribuzione dei dati al livello di rumore $t$. Questa formulazione e quella che compare naturalmente nei [[Diffusion Models|diffusion models]], nei quali la rete stima una direzione di denoising per ogni istante del processo.

![[IMG - da SDEs a ODEs Score and Flow-Matching.png]]

Il punto strutturale e che, in presenza di rumore gaussiano, un buon denoiser non si limita a ricostruire, ma definisce una direzione di ritorno verso regioni piu plausibili della distr ibuzione. Questo chiarisce perche nei modelli moderni denoising e score estimation siano due descrizioni della stessa informazione locale.

Il collegamento con il denoising e reso esplicito dalla [[Formula di Tweedie|formula di Tweedie]], che mostra come la stima del dato pulito medio e la score della distribuzione rumorosa siano due modi equivalenti di descrivere la stessa informazione locale. Se infatti il modello osserva un campione rumoroso $x_t$, allora conoscere la score $\nabla_{x_t}\log p_t(x_t)$ significa sapere come correggere $x_t$ verso un campione meno rumoroso e piu coerente con i dati.

Per questo, nelle formulazioni pratiche dei [[Diffusion Models|diffusion models]], si possono usare parametrizzazioni apparentemente diverse ma strettamente collegate:
- predire direttamente il rumore $\epsilon$
- predire il dato pulito $x_0$
- predire la score $\nabla_{x_t}\log p_t(x_t)$

Queste tre scelte non sono equivalenti in ogni dettaglio implementativo, ma rappresentano modi diversi di codificare la stessa struttura di denoising su una famiglia di distribuzioni rumorose. La differenza sta nella parametrizzazione del bersaglio di training, non nell'idea di fondo.

Rispetto ai [[Normalizing Flows|normalizing flows]], lo score matching non impone una trasformazione invertibile globale con jacobiano trattabile. Il suo oggetto centrale non e una mappa di trasporto esplicita, ma un campo locale di direzioni che descrive come la densita varia nello spazio.

Le proprieta operative piu importanti sono:
- stima la [[Score Function|score]] senza richiedere la densita normalizzata esplicita
- evita il problema della costante di normalizzazione nei modelli energetici
- nei [[Diffusion Models|diffusion models]] appare nella forma di denoising score matching su distribuzioni rumorose
    
