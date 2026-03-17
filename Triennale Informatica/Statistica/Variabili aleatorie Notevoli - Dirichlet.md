---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
Area:
topic:
SubTopic:
---

# Variabili aleatorie Notevoli - Dirichlet
---
Variabili aleatorie Notevoli - Dirichlet è una distribuzione continua multivariata definita sul [[Simplex (Simplesso)|simplesso]], utilizzata per modellare vettori di probabilità e come prior coniugato della distribuzione multinomiale.

Definizione:
- sia $\theta = (\theta_1, \dots, \theta_K)$ tale che $$\theta_k \ge 0,\ \sum_{k=1}^K \theta_k = 1$$
- $\theta$ appartiene al simplesso $\Delta^{K-1}$

La distribuzione di Dirichlet con parametro $\alpha = (\alpha_1, \dots, \alpha_K)$, con $\alpha_k > 0$, ha densità:
$$P(\theta|\alpha) = \frac{\Gamma\left(\sum_{k=1}^K \alpha_k\right)}{\prod_{k=1}^K \Gamma(\alpha_k)} \prod_{k=1}^K \theta_k^{\alpha_k - 1}$$ 

Interpretazione dei parametri:
- $\alpha_k$ rappresenta pseudo-conteggi associati alla categoria $k$
- $\alpha_0 = \sum_{k=1}^K \alpha_k$ controlla la concentrazione
- media: $$\mathbb{E}[\theta_k] = \frac{\alpha_k}{\alpha_0}$$
- varianza: $$\text{Var}(\theta_k) = \frac{\alpha_k(\alpha_0 - \alpha_k)}{\alpha_0^2(\alpha_0 + 1)}$$

Proprietà:
- distribuzione sul simplesso (vettori che sommano a 1)
- supporto continuo
- generalizzazione multivariata della Beta (caso $K=2$)
- coniugata rispetto alla multinomiale

Coniugatezza:
- se $$\theta \sim \text{Dirichlet}(\alpha)$$
- e dati conteggi $n = (n_1, \dots, n_K)$ da multinomiale
- allora la posterior è ancora Dirichlet:
$$P(\theta|n) = \text{Dirichlet}(\alpha_1 + n_1, \dots, \alpha_K + n_K)$$ 

Interpretazione probabilistica:
- modello per distribuzioni discrete ignote
- incorpora conoscenza a priori tramite $\alpha$
- aggiorna in modo additivo con i dati osservati

Ruolo nei modelli:
- fondamentale in [[Latent Dirichlet Allocation (LDA)|LDA]] come prior sui topic
- utilizzata in [[Modelli Probabilistici]] per gestire incertezza su parametri multinomiali
- permette inferenza analitica in contesti bayesiani

Effetto dei parametri:
- $\alpha_k < 1$ ⇒ distribuzioni sparse (massa vicino ai vertici)
- $\alpha_k = 1$ ⇒ distribuzione uniforme
- $\alpha_k > 1$ ⇒ distribuzioni più concentrate verso il centro del simplesso