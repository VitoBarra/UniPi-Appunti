---
Subject: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# convergenza in probabilita - criterio di sufficienza
---

#### Condizione sufficiente per la convergenza in probabilita
_siano_  $X_{1},X_{2},\dots$ una _successione_ di [[Variabili Aleatorie (Casuali)|variabili aleatorie]] definite sullo stesso [[Definizione di Probabilita|spazio di probabilita]] 
_se_  vale che$$\lim_{ n \to \infty }\mathbb{E}[X_{n}]=c \in  \mathbb{R} \ \ \ \ \ \ \ \ \ \ \lim_{ n \to \infty }Var(X_{n})=0  $$ ovvero se la il [[Variabili aleatoria - Momenti|valore atteso]] della successione _esiste_ e se la [[Variabili aleatorie - Varianza|varianza]] della successione è $0$ 
_allora_  la _successione_ $(X_{n})_{n \geq 1}$ _[[Convergenza in probabilita|converge in probabilita]]_ alla costante $c$ ovvero $$\lim_{ n \to \infty }\mathcal{P}(|X_{n}-\mathbb{E}[X_{n}]|>\varepsilon)=0 $$

_Dimostrazione_
	 Dalla [[Diseguaglianza di Markov|Diseguaglianza di Markov]] applicata alla variabile $(X_{n}-c)^{2}$ si ha che $$\mathcal{P}\{ |X_{n}-c|> \varepsilon \} \leq \frac{1}{\varepsilon^{2}}\mathbb{E}\left[(X_{n}-c)^{2}\right]$$ da cui espandendo il membro a destra si ottiene $$\begin{array}{}
	 \mathbb{E}\left[(X_{n}-c)^{2}\right]  & = &     \\ & = & 
\mathbb{E}\left[(X_n-\mathbb{E}[X_{n}]+\mathbb{E}[X_{n}]-c)^{2}\right]   \\  & = & 
\mathbb{E}\left[(X_{n}-\mathbb{E}[X_{n}])^{2}\right] +  2\mathbb{E}[X_{n}-\mathbb{E}[X_{n}]](\mathbb{E}[X_{n}]-c)+(\mathbb{E}[X_{n}]-c)^{2}  \\ & = & 
Var(X_{n})+(\mathbb{E}[X_{n}-c])^{2}
\end{array}$$ e di conseguenza vale che il [[Limiti di una funzione|limite]]$\lim_{ n \to \infty } \mathbb{E}\left[(X_{n}-c)^{2}\right]=0$ ed è _dimostrata la tesi_
