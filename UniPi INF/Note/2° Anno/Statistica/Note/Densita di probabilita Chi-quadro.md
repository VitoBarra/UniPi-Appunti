---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Variabili aleatorie Chi-quadro
---
#### Densita chi-quadro
_siano_ $X_{1}\dots,X_{n}$ [[Variabili Aleatorie (Casuali)|variabili aleatorie]] [[Variabili Aleatorie Notevoli|gaussiane standard]] 
_se_  sono [[Indipendenza di Variabili aleatorie|indipendenti]] 
_allora_ la variabile $(X_{1}^{2}+\dots+X_{n}^{2})$ ha [[Densita di probabilita Gamma|densita]] $\Gamma\left( \frac{n}{2},\frac{1}{2} \right)$. ed è chiamata _densita chi-quadro_ con $n$ _gradi di libertà_ indicata con $\chi^{2}(n)$

_dimostrazione_
	per completare la dimostrazione basta dimostrare che se $X$ è gaussiana allora $X^{2}$ è $\Gamma\left( \frac{1}{2},\frac{1}{2} \right)$
	e per fare ciò vale $$
	\begin{array}{}
F_{Z}(t)=\mathcal{P}(X^{2} \leq t)= \\
\begin{cases}
0  &  t < 0 \\
\mathcal{P}(-\sqrt{t} \leq X\leq \sqrt{ t })=2F_{X}(\sqrt{ t })-1  & t \geq 0 
\end{cases}
\end{array}
$$ dunque la [[Probabilita sui numeri Reali#Densità di probabilità (Definizione)|densita di probabilita]] si ricava calcolando $f_{Z}(t)= \frac{d}{dt}F_{Z}(t)$ e per $t>0$ vale $$\begin{array}{} & 
\displaystyle 2\frac{d}{dt}F_{X}(\sqrt{ t }) & = & \displaystyle\frac{2}{\sqrt{ 2\pi }}\frac{d}{dt}\int ^{\sqrt{ t }}_{-\infty} e^{-x^2/2} \, dx  \\
 = & \displaystyle\frac{2}{\sqrt{ 2\pi }}\cdot  \frac{e^{-t/2}} {2\sqrt{t}} & = & \displaystyle\frac{e^{-t/2}(t)^{-1/2}} {2^{1/2}\Gamma\left( \frac{1}{2} \right)}
\end{array}$$dove abbiamo usato $\Gamma\left( \frac{1}{2} \right) = \sqrt{ \pi }$



#### Proposizione
_siano_ $X,Y$  due _[[Variabili Aleatorie (Casuali)|variabili aleatorie]]_ con desnita _chi quadro_  $\chi^{2}(n), \chi^{2}(m)$
_se_ queste sono [[Indipendenza di Variabili aleatorie|indipendenti]]
_allora_ vale che $X+Y$ ha densita $\chi^{2}(n+m)$


#### Proposizione
_sia_ $C_{n}$ una [[Variabili Aleatorie (Casuali)|Variabile aleatoria]] con _densta_ $\chi^{2}$ 
_allora_ si può pensare a $C_{n}$ come $C_{n}=X^{2}_{1},\dots X^{2}_{n}$ dove le $X_{i}$ sono [[Variabili Aleatorie Notevoli|gaussiane standard]] dove vale che 
- il [[Variabili aleatoria - Momenti|momento primo]] vale $\mathbb{E}[X_{i}^{2}]=1$ 
- la [[Variabili aleatorie - Varianza]] vale $Var(X_{i}^{2})=2$
e valgono i seguenti fatti
- per la [[Teorema debole dei grandi numeri|teorema dei grandi numeri]] vale che $\frac{C_{n}}{n}\xrightarrow{n \to \infty}1$ con  [[Convergenza in probabilita|converge in probabilita]] 
- Per il [[Teorema centrale del limite|Teorema centrale del limite]] la successione $\cfrac{C_{n}-n}{\sqrt{ 2n }}$ [[Convergenza in distribuzione|converge in dostribuzione]] alla variabile $N(0,1)$ e quindi $\cfrac{C_{n}-n}{\sqrt{ 2n }}$ è approssimativamente una [[Variabili Aleatorie Notevoli|gaussiana standard]]
	