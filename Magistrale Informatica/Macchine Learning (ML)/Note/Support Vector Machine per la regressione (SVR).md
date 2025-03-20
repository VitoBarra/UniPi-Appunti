---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Support Vector Machine per la regressione (SVR)
---
le support **vector machine per  regressione** è un estenzione delle [[Support Vector Machine (SVM)|support vector macchine]] per poter fare [[Algoritmi di learning supervisionato|regressione]].




![[IMG - SVR  Double moon Training.png]]
![[IMG - SVR Double moon test.png]]![[IMG - SVR - bho.png]]


# Stima della Dipendenza di uno Scalare da un Vettore  

Abbiamo una funzione che descrive la dipendenza di uno scalare da un vettore:  

$$
d = f(\mathbf{x}) + \nu
$$  

Dove:
- La funzione $f$ è **sconosciuta**  
- Il termine di rumore $\nu$ è **statisticamente indipendente** dal vettore di input $\mathbf{x}$  

Abbiamo solo un **training set** dato da:  

$$
T = \{ (\mathbf{x}_i, d_i) \}_{i=1}^{N}
$$  

Stimiamo $d$ usando una **espansione lineare di funzioni non lineari** $\{\phi_j(\mathbf{x})\}_{j=0}^{m_1}$:  

$$
y = h(\mathbf{x}) = \mathbf{w}^T \Phi(\mathbf{x})
$$  

Dove:
- Il vettore dei pesi è:  

  $$
  \mathbf{w} = (w(0) = b, w(1), \dots, w(m_1))^T
  $$

- La trasformazione non lineare $\Phi(\mathbf{x})$ è definita come:

  $$
  \Phi(\mathbf{x}) = (\phi_0(\mathbf{x}) = 1, \phi_1(\mathbf{x}), \dots, \phi_{m_1}(\mathbf{x}))^T
  $$

---

# Introduzione delle Variabili di Slack  

Per permettere una certa tolleranza negli errori di previsione, introduciamo le **variabili di slack** $\xi_i$ e $\xi_i'$ per $i = 1, \dots, N$.  

Definiamo il vincolo di approssimazione:  

$$
- \xi_i' - \epsilon \leq d_i - \mathbf{w}^T \Phi(\mathbf{x}_i) \leq \epsilon + \xi_i, \quad \forall i = 1, \dots, N
$$  

Questo porta ai seguenti **vincoli**:  

$$
\begin{cases}
    d_i - \mathbf{w}^T \Phi(\mathbf{x}_i) \leq \epsilon + \xi_i \\
    \mathbf{w}^T \Phi(\mathbf{x}_i) - d_i \leq \epsilon + \xi_i' \\
    \xi_i \geq 0 \\
    \xi_i' \geq 0
\end{cases}
\quad \forall i = 1, \dots, N
$$  

---

# Problema Primal  

Dato il training set  

$$
T = \{(\mathbf{x}_i, d_i)\}_{i=1}^{N}
$$  

vogliamo trovare i valori ottimali di $\mathbf{w}$ che minimizzano la seguente funzione obiettivo:  

$$
\Psi(\mathbf{w}, \xi, \xi') = \frac{1}{2} \mathbf{w}^T \mathbf{w} + C \sum_{i=1}^{N} (\xi_i + \xi_i')
$$  

sotto i vincoli:

$$
\begin{cases}
    d_i - \mathbf{w}^T \Phi(\mathbf{x}_i) \leq \epsilon + \xi_i \\
    \mathbf{w}^T \Phi(\mathbf{x}_i) - d_i \leq \epsilon + \xi_i' \\
    \xi_i \geq 0 \\
    \xi_i' \geq 0
\end{cases}
\quad \forall i = 1, \dots, N
$$  

---

Questa formulazione rappresenta il problema di **regressione con margine $\epsilon$**, tipico delle **Macchine a Vettori di Supporto per la Regressione (SVR)**.
