---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Z-Test
---
gli _Z-Test_  il [[Test Statistici|test statistico]] sulla [[Statistica descrittiva - Dati Numerici#Media (definizione)|media]] di un [[Campione Statistico|campione]] [[Variabili aleatorie Gaussiane|gaussiano]] con [[Variabili aleatorie - Varianza|varianza]] _nota_ 



#### formulazione del testo
_sia_ $X_1\dots,X_{n}$ un [[Campione Statistico|campione statistico]] con legge [[Variabili aleatorie Gaussiane|gaussiana]] $N(m,\sigma^{2})$ e supponendo di conosce la [[Variabili aleatorie - Varianza|varianza]] $\sigma>0$. 

_vogliamo_ effettuare un [[Test Statistici|test]] per determinare se la media $m$ coincide con un certo valore $m_{0}$. Ovvero formalmente $m=\theta \in \Theta=\mathbb{R}$ e $\Theta_{0}=\{ m_{0} \}$ e $\Theta_{1}=\mathbb{R} \backslash \{ m_{0} \}$ 
e abbiamo quindi le ipotesi $$\mathcal{H}_{0})\ m=m_{0} \ \ \ \ \ \ \ \mathcal{H}_{1})\ m \not = m_{0}$$



Siccome $\overline{X}$ è uno [[Statistica Parametrica#Stimatore corretto (Definizione)|stimatore corretto e consistente]] di $m$ allora possiamo definire la _regione critica_ come $$C = \{ |\overline{X}-m_{0}| >d \}$$dove il numero $d>0$ deve essere determinate in funzone del _livello_ $\alpha$  scelto e quindi $$\mathcal{P}_{m_{0}}\{ C \} \leq \alpha=\mathcal{P}_{m_{0}} \{ |\overline{X}-m_{0}| >d \} \leq \alpha$$. Siccome vogliamo ottenere una _regione critica_ il più grande possibile per poter aumentare la _potenza del test_  possiamo imporre $$\mathcal{P}_{m_{0}} \{ |\overline{X}-m_{0}| >d \} = \alpha$$e quindi siccome $Z=\frac{\sqrt{n}(\overline{X}-m)}{\sigma}$ è [[Variabili aleatorie Gaussiane|gaussiana standard]] vale che $$\begin{array}{}
\mathcal{P}_{m_{0}} \{ |\overline{X}-m_{0}| >d \} &  = \\
 \mathcal{P}_{m_{0}} \left\{  \cfrac{\sqrt{ n }}{\sigma}|\overline{X}-m_{0}| >\cfrac{d  \sqrt{ n  }}{\sigma}\right\} & = \\
\mathcal{P}\left\{  |Z| > \cfrac{d\sqrt{n}}{\sigma} \right\} & = \\
\alpha \\
\end{array}$$ e valendo $\frac{d\sqrt{ n }}{\sigma}=q_{1-\frac{\alpha}{2}}$ possiamo definire la _regione critica_ come $$
\begin{array}{}
C & = & \left\{  \sqrt{ n }\frac{|\overline{X}-m_{0} |}{\sigma}>q_{1-\frac{\sigma}{2}}  \right\} & \\ & =    & 
\left\{  | \overline{X}-m_{0} |> \frac{\sigma}{\sqrt{ n }}q_{1-\frac{\alpha}{2}}  \right\}
\end{array}$$
in pratica data una realizzazione $x_{1},\dots, x_{n}$ si calcola la _media_ $\overline{x}_{n}$ e si rifiuta l ipotesi $\mathcal{H}_{0}$ se $|\overline{x}_{n}|>\sigma q_{1-\alpha/2}\sqrt{ n }$, si accetta $\mathcal{H}_{0}$ in caso contrario.



#### Calcolo del p-value
per calcolare il _p-value_ della realizzazione $(x_{1},\dots,x_{n})$ si procede usando la definizione _informale_ e quindi calcoliamo il p-value come probabilita di ottenere i _valori piu estremi_ rispetto al ipotesi $\mathcal{H}_{0}$ e in questo caso sono.
Considerando $(y_{1},\dots,y_{n})$ e $\overline{x}_{n}$ e $\overline{y}_{n}$ le rispettive [[Idd - Media Campionaria|medie campionarie]] sono valori piu estremi quelli per cui vale $$|\overline{y}_{n}-m_{0}| > |\overline{x}_{n}-m_{0}|$$  e quindi il _p-value_ $$\begin{array}{}
\overline{\alpha}=\overline{\alpha}(x_{1},\dots,x_{n}) & = \\
\mathcal{P}_{m_{0}}\left\{ \sqrt{ n }\cfrac{|\overline{X}-m_{0}|}{\sigma}>\cfrac{\sqrt{ n }}{\sigma}|\overline{x}-m_{0}|   \right\} & = \\
2\left[ 1-\Phi\left( \frac{\sqrt{ n }}{\sigma}|\overline{x}-m_{0}| \right) \right]
\end{array}
$$
in l ultimo passaggio è giustificato dal fatto che $Z=\sqrt{ n }(\overline{X}-m_{0})/\sigma$ è [[Variabili aleatorie Gaussiane|gaussina standard]].

dobbiamo ora verificare che questa rispetti la _[[Test Statistici#P-value|definizione rigorosa]]_ del _p-value_, dobbiamo quindi verificare che il test di livello $\alpha$ rifiuta $\mathcal{H}_{0}$ solo se $\alpha>\overline{\alpha}$. 
sappiamo che $\mathcal{H}_{0}$ è rifiutata al livello $\alpha$ se s solo se $\frac{\sqrt{ n }}{\sigma}|\overline{x}-m_{0}|>q_{1-\alpha/2}$. quindi in caso di rifiuto abbiamo $$ \begin{array}{}
\overline{\alpha} & = & \mathcal{P}_{m_{0}}\left\{  \sqrt{ n }\frac{|\overline{X}-m_{0}|}{\sigma}>\frac{\sqrt{ n }}{\sigma}| \overline{x}-m_{0}|  \right\} \\
 &  < & \mathcal{P}_{m_{0}} \left\{  \sqrt{ n }\frac{|\overline{X}-m_{0}|}{\sigma}>q_{1-\alpha/2}  \right\}  \\
	 & = & \alpha
\end{array}$$
mentre in caso di _accettazione_ vale la diseguaglianza opposta e quindi $\overline{\alpha}$ soddisfa la definizione di _p-value_.

#### Curva operativa
