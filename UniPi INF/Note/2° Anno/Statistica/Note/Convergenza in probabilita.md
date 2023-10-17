---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Convergenza in probabilita
---
la _convergenza in probabilità_ esprime il concetto 

#### Convergenza in probabilità (definizione)
_siano_ $X$ e $X_{1},X_{2},\dots$ [[Variabili Aleatorie (Casuali)|variabili aleatorie]] definite sullo stesso [[Definizione di Probabilita|spazio di probabilita]] 
_allora_ $X_{n}$ _converge in probabilità_ ad $X$ per $n \to \infty$ 
_se_  $\forall  \varepsilon > 0$  vale $$\lim_{ n \to \infty } \mathcal{P}(|X_{n}-X| >\varepsilon )=0$$Ovvero, se la probabilita che $X_{n}$ _disti_ da $X$ piu di $\varepsilon$ è in [[Limiti|limite]] $0$

notiamo che potrebbe anche essere che $X=c$ ovvero il limite vada ad una costante.



#### Condizione sufficiente per la convergenza in probabilita
_siano_ $X$ e $X_{1},X_{2},\dots$ [[Variabili Aleatorie (Casuali)|variabili aleatorie]] definite sullo stesso [[Definizione di Probabilita|spazio di probabilita]] 
_se_  vale che$$\lim_{ n \to \infty }\mathbb{E}[X_{n}]=c \in  \mathbb{R} \ \ \ \ \ \ \ \ \ \ \lim_{ n \to \infty }Var(X_{n})=0  $$ ovvero se la il [[Variabili aleatoria - Momenti|valore attes]] della successione _esiste_ e se la [[Variabili aleatorie - Varianza|varianza]] della successione è $0$ 
_allora_  la _successione_ $(X_{n})_{n \geq 1}$ _converge in probabilita_ alla costante $c$


_Dimostrazione_
	 Dalla [[Diseguaglianza di Markov|Diseguaglianza di Markov]] applicata alla variabile $(X_{n}-c)^{2}$ si ha che $$\mathcal{P}\{ |X_{n}-c|> \varepsilon \} \leq \frac{1}{\varepsilon^{2}}\mathbb{E}\left[(X_{n}-c)^{2}\right]$$ da cui espandendo il membro a destra si ottiene $$\begin{array}
	 \mathbb{E}\left[(X_{n}-c)^{2}\right]  & =    \\
\mathbb{E}\left[(X_n-\mathbb{E}[X_{n}]+\mathbb{E}[X_{n}]-c)^{2}\right]  & = \\
\mathbb{E}\left[(X_{n}-\mathbb{E}[X_{n}])^{2}\right] +  2\mathbb{E}[X_{n}-\mathbb{E}[X_{n}]](\mathbb{E}[X_{n}]-c)+(\mathbb{E}[X_{n}]-c)^{2}  & = \\
Var(X_{n})+(\mathbb{E}[X_{n}-c])^{2}
\end{array}$$ e di conseguenza vale che $\lim_{ n \to \infty } \mathbb{E}\left[(X_{n}-c)^{2}\right]=0$ ed è dimostrata la tesi.
