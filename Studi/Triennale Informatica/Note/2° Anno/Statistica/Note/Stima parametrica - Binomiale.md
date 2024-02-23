---
Subject: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Stima parametrica - Binomiale
---
per stimale il parametro $\theta$ ignoto nella [[Variabili Aleatorie Notevoli - Binomiale|distribuzione binomiale]] $B(m,\theta)$ si usano i metodi   

notiamo che 
##### Metodo della massima verosomiglianza
_sia_
- $X$ una [[Variabili Aleatorie Notevoli - Binomiale|variabile aleatoria binomiale]] $B(m,\theta)$ 
- $X_{1},\dots X_{n}$ un [[Campione Statistico|campione statistico]] di _taglia_ $n$
_allora_ la _stima_ ottenuto dal metodo di [[Stima Parametrica - Metodo di Massima Verosomiglianza|massima verosomiglianza]] è    
$$\hat{\theta}=\frac{1}{m}\sum^{n}_{i=1}\frac{x_{i}}{n}$$_dimostrazione_: seguenti la definizione si ha che $$L(\theta)=\theta^{\sum^{n}_{i}x_{i}}(1-\theta)^{mn-\sum^{n}_{i}x_{i}}\prod^n_{i=1}\begin{pmatrix}
m  \\ x_{i}
\end{pmatrix}$$usando il _[[Stima Parametrica - Metodo di Massima Verosomiglianza#Criterio per trovare il massimo|criterio per trovare il parametro massimo]]_ si ha che  $$
\begin{array}{}
& \displaystyle  \frac{d}{d\theta}\log(L(\theta)) & = & 0\\ \\
 & \displaystyle \frac{d}{d\theta}\left[ \sum^{n}_{i=1}x_{i}\log(\theta)+mn -\sum^{n}_{i=1}x_{i}\log(1-\theta)+\log\left( \prod^n_{i=1}\begin{pmatrix}
m  \\ x_{i}
\end{pmatrix} \right) \right] & = & 0\\
& \displaystyle  \frac{\sum^n_{i=1}x_{i}}{p}+\frac{mn-\sum^{n}_{i=1}x_{i}}{1-p}(-1)  & = & 0  \\
& \hat{\theta} & = & \displaystyle\frac{1}{m}\sum^{n}_{i=1}\frac{x_{i}}{n}
\end{array}
$$
e lo _stimatore_ è uno [[Stimatori statistici#Stimatore corretto (Definizione)|stimatore corretto]]  siccome vale che $$\mathbb{E}\left[ \frac{\overline{X}}{m} \right]=\frac{mp}{m}=p$$ 
 
##### Metodo dei momenti
per il [[Stima parametrica - Metodo dei momenti|metodo dei momenti]] si ha per definizione di [[Variabili aleatoria - Momenti|momento]] e per le priorità della [[Stima parametrica - Binomiale|variaible binomiale]]  abbiamo che $$
\begin{array}
\mathbb{E}[X] & = & m\theta  \\ \end{array}
$$ e per definizione di _[[Stima parametrica - Metodo dei momenti|metodo dei momenti]]_ $\tilde{\theta}$ e la soluzione di $\mathbb{E}[X]=\sum^{n}_{i=1}\frac{x_{i}}{n}$ e quindi vale che  $$\begin{array}{}  m\tilde{\theta}=\displaystyle\sum^{n}_{i=1}\frac{x_{i}}{n} 
 & \implies &\displaystyle \tilde{\theta}=\frac{1}{m}\sum^m_{i=1}\frac{x_{i}}{n} \\
	 & \implies & \displaystyle\tilde{\theta}=\hat{\theta}


\end{array}$$i due metodi restituiscono la _stessa stima_ 


