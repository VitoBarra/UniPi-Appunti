---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Bias-Variance Decomposition
---
Ogni __set di training__ per un [[Concetti generali del Machine Learning|algoritmo di macchina learning]] è una realizzazione possibile dell'universo dei dati e ogni diverso set puo dare fornire predizioni differenti. 

sia un dataset $(\mathbf{x}_i,y_i)$ con $i = 1 \dots \ell$ e $y=f(x)+\varepsilon$ con $\varepsilon$ un rumore gaussiona con media $0$ e deviazione standard $\sigma$. 
Assumendo che ogni punto $\mathbf{x}$ preso da una [[Famiglia di variabili aleatorie Indipendenti e identicamente distribuite (IDD)|i.d.d.]] con la distribuzione di [[Definizione di Probabilita|probabilita]] $\mathcal{P}$, Allora vogliamo analizzare l' __errore atteso__ su un arbitrario nuovo punto $\mathbf{x}$  ovvero $$\mathbb{E}_\mathcal{P}[(y-h(\mathbf{x}))^2]$$l' __errore atteso__ è su __TUTTI__ i possibili dataset presi in accordo a $\mathcal{P}$ e dove per ogni estrazione di training set c è una nuova $y$ e una nuova __ipotesi__ $h$.


Andando a scomporre il valore otteniamo$$
  
 \begin{array}{}
  \mathbb{E}_\mathcal{P}[(h(x) - y)^2]  & = &   \mathbb{E}_\mathcal{P}[h(x)^2-2yh(x)+y^2]\\ 
  & = &     \mathbb{E}_\mathcal{P}[h(x)^2]+\mathbb{E}_\mathcal{P}[y^2]-2\mathbb{E}_\mathcal{P}[y]\mathbb{E}_\mathcal{P}[h(x)]

\end{array}
  $$ e  ponendo $$
\bar{h}(x) = \mathbb{E}_{\mathcal{P}}[h(x)]
$$ come il [[Variabili aleatoria - Momenti|valore atteso]] ovvero la __predizione media__ del ipotesi nel punto $x$ quando questa è scelta da una dataset preso sulla distribuzione $\mathcal{P}$ , possiamo quindi usare il lemma della [[Variabili aleatorie - Varianza|varianza]] per dire: $$
\begin{array}
\mathbb{E}_{\mathcal{P}}[h(x)^2]  & = &  \mathbb{E}_{\mathcal{P}}\left[(h(x) - \bar{h}(x))^2\right] + \bar{h}(x)^2 \\
\mathbb{E}_{\mathcal{P}}[y^2]  & = &  \mathbb{E}_{\mathcal{P}}\left[(y - \mathbb{E}_{\mathcal{P}}[y])^2\right] + \mathbb{E}_{\mathcal{P}}[y]^2
\end{array}
$$e poiché $y=f(x)+\varepsilon$ e  $f(x)$ è costante e $\varepsilon$ è un errore gaussiano con media $0$  vale che: $$
\mathbb{E}_{\mathcal{P}}[y] = \mathbb{E}_{\mathcal{P}}[f(x) + \varepsilon] = f(x)
$$ espandendo quindi i termini otteniamo $$
\begin{array}
\mathbb{E}_{\mathcal{P}}\left[(y - h(x))^2\right]  & = &  
\mathbb{E}_{\mathcal{P}}\left[(h(x) - \bar{h}(x))^2\right] & +\\  
  & &  \bar{h}(x)^2 -2f(x)\bar{h}(x) +f(x)^2 & +\\ 
 &  &  \mathbb{E}_{\mathcal{P}}\left[(y - f(x))^2\right]
\end{array}
$$che puo essere riscritto come$$
\begin{array}
\mathbb{E}_{\mathcal{P}}\left[(y - h(x))^2\right]  & = &  
\mathbb{E}_{\mathcal{P}}\left[(h(x) - \bar{h}(x))^2\right]  & +  & \text{(variance)}\\  
&  &  (\bar{h}(x)-f(x))^2   & + &  \text{(bias)}^2\\ 
&  &  \mathbb{E}_{\mathcal{P}}\left[(y - f(x))^2\right]  &  & \text{(noise)}^2
\end{array}
$$ e quindi brevemente $$
\mathbb{E}_{\mathcal{P}}\left[(y - h(x))^2\right] = 
\text{Var}[h(x)] + \text{Bias}[h(x)]^2 + \mathbb{E}_{\mathcal{P}}[\varepsilon^2]
$$e applicando il [[Variabili aleatorie - Varianza|lemma della varianza]] otteniamo che  $\mathbb{E}_{\mathcal{P}}[\varepsilon^2] = \sigma^2$  e quindi :$$
\mathbb{E}_{\mathcal{P}}\left[(y - h(x))^2\right] = 
\text{Var}[h(x)] + \text{Bias}[h(x)]^2 + \sigma^2
$$

ovvero abbiamo scomposto l errore atteso in 3 componenti:
- **Bias**: discrepanza media tra la funzione reale $f(x)$ e $h(x)$ su diversi set di addestramento (rigidità del modello). $[\bar{h}(x)-f(x)]^2$
- **Varianza**: variabilità del modello $h$ per realizzazioni diverse del set di addestramento (alta flessibilità). $\mathbb{E}_{\mathcal{P}}\left[(h(x) - \bar{h}(x))^2\right]$
- **Rumore**: errore casuale intrinseco nei dati, non eliminabile non dipende dal modello
![[Pasted image 20250203175744.png]]
![[Pasted image 20250203155239.png]]



#### Regolarizzazione e Trade-off Bias-Varianza
Assumendo la regolarizzazione $L_2$ con il termine di regolarizazione pesato da $\lambda$ si ha che:
1. Aumentare il parametro $\lambda$ (più regolarizzazione):
   - Riduce la complessità del modello.
   - **Alto bias**, **bassa varianza**.
2. Diminuire $\lambda$ (meno regolarizzazione):
   - Modelli più complessi.
   - **Basso bias**, **alta varianza**.
     
![[Pasted image 20250203185106.png]]
![[Pasted image 20250203185004.png]]