---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area: Modelli Generativi
topic: Autoencoders
SubTopic:
---

# Contractive Autoencoders (CAE)
---
I **Contractive Autoencoders** sono una variante degli [[Autoencoders (AE)|autoencoders]] ispirata all'idea dei [[Denoising Autoencoders (DAE)|denoising autoencoders]], ma invece di regolarizzare il modello corrompendo l'input penalizza direttamente la sensibilità dell'**encoder** rispetto a piccole variazioni del dato.

L'idea è che la rappresentazione latente non debba cambiare molto quando l'input viene perturbato localmente. In questo modo il modello impara feature più stabili e meno sensibili a variazioni accidentali o rumore infinitesimo.

Dato un input $x$, l'**encoder** $f_\theta$ costruisce una rappresentazione latente $z$:$$z = f_{\theta}(x)$$Il **decoder** $g_\phi$ produce una **ricostruzione**:$$\tilde{x} = g_{\phi}(z)$$Come in un autoencoder standard, il target resta il dato originale $x$, ma alla reconstruction loss si aggiunge un termine che rende l'encoder localmente contractive.


Il **contractive autoencoder** aggiunge alla normale loss di ricostruzione $\mathcal{L}(x,\tilde{x})$ un termine di regolarizzazione:
$$
J_{\text{CAE}}(\theta,\phi)
=
\sum_{x \in \mathcal{D}}
\left[
\mathcal{L}(x,\tilde{x})
+
\lambda \, \Omega(z)
\right]
$$
dove:
$$
\Omega(z) = \Omega(f(x)) = \left\|\frac{\partial f_{\theta}(x)}{\partial x}\right\|_F
$$
Quindi la penalità coincide con la [[Norme Matriciali e Norme Vettoriali|norma]] del [[Jacobiana di una funzione|jacobiano]] dell'encoder rispetto all'input. Qui $\frac{\partial f_{\theta}(x)}{\partial x}$ è il jacobiano dell'encoder, $\left\|\cdot\right\|_F$ è la [[Norma di Frobenius|norma di Frobenius]] e $\lambda$ controlla il peso della regolarizzazione contractive.

In modo analogo, si possono anche penalizzare derivate di ordine superiore. In questo caso non si controlla solo la sensibilità locale di primo ordine dell'encoder, ma anche come questa sensibilità cambia nelle vicinanze del punto, imponendo una rappresentazione ancora più regolare.

In pratica, il modello deve soddisfare due vincoli contemporaneamente:
- ricostruire bene il dato;
- evitare che piccole perturbazioni dell'input producano grandi variazioni nella rappresentazione latente.

## Interpretazione geometrica
La penalità forza l'encoder a essere localmente **insensibile** nelle direzioni in cui piccoli spostamenti dell'input non corrispondono a variazioni significative dei dati.

Secondo la [[Manifold Hypothesis|manifold hypothesis]], i dati ad alta dimensionalità si concentrano vicino a una manifold di dimensione più bassa. In questo contesto, il CAE cerca di costruire una rappresentazione che:
- resti stabile nelle direzioni ortogonali alla manifold;
- rimanga invece sensibile nelle direzioni che descrivono vere variazioni del dato.

Quindi, invece di imparare esplicitamente a correggere un input rumoroso come fa un [[Denoising Autoencoders (DAE)|denoising autoencoder]], il **contractive autoencoder** ottiene un effetto simile imponendo localmente che l'encoder vari il meno possibile attorno ai punti osservati.


## Limite
La contrazione è una proprietà locale: il modello controlla la sensibilità dell'encoder attorno ai dati osservati, ma non costruisce direttamente un [[Modelli Probabilistici|modello probabilistico]] esplicito della distribuzione.

Se la penalità è troppo forte, il rischio è comprimere eccessivamente la rappresentazione, perdendo informazione utile anche lungo direzioni significative della manifold.
