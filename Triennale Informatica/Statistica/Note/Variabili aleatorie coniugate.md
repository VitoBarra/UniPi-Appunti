---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
Area:
topic:
SubTopic:
---

# Variabili aleatorie coniugate
---
le **Variabili aleatorie coniugate** descrivono una relazione tra distribuzioni in [[Formula di Bayes|inferenza bayesiana]] in cui la posterior appartiene alla stessa famiglia della prior dopo l’osservazione dei dati.

Dato un parametro $\theta$ con prior $p(\theta)$ e dati $D$ con likelihood $p(D|\theta)$, si dice che la prior è coniugata rispetto alla likelihood se $$p(\theta|D) \propto p(D|\theta)p(\theta)$$ appartiene alla stessa famiglia parametrica di $p(\theta)$ :contentReference[oaicite:0]{index=0}

Struttura generale:
- prior: $$p(\theta|\alpha)$$
- likelihood: $$p(D|\theta)$$
- posterior: $$p(\theta|D,\alpha) = p(\theta|\alpha')$$

dove $\alpha'$ sono parametri aggiornati che incorporano l’informazione dei dati.

Interpretazione:
- la coniugatezza garantisce chiusura rispetto all’aggiornamento bayesiano
- l’aggiornamento avviene in forma analitica senza integrazione complessa
- i parametri della prior si comportano come pseudo-conteggi

Esempio generale (schema conteggi):
- likelihood basata su conteggi $n$
- prior con parametri $\alpha$
- aggiornamento: $$\alpha' = \alpha + n$$

Questo riflette un accumulo additivo dell’informazione osservata.

Proprietà:
- semplifica drasticamente l’inferenza bayesiana
- evita il calcolo esplicito dell’integrale di normalizzazione
- consente aggiornamenti incrementali dei parametri

Relazione con distribuzioni notevoli:
- [[Variabili aleatorie Notevoli - Dirichlet]] è coniugata della multinomiale
- Beta è coniugata della Bernoulli
- Gaussiane con media nota hanno prior gaussiane coniugate

Ruolo nei modelli:
- utilizzata in [[Latent Dirichlet Allocation (LDA)|LDA]] per gestire distribuzioni multinomiali
- base teorica per algoritmi come EM e metodi variazionali

Formalmente, la coniugatezza permette di mantenere la stessa forma funzionale della distribuzione, rendendo l’inferenza un aggiornamento parametrico piuttosto che strutturale