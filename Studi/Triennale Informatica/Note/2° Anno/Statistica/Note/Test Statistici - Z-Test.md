---
Subject: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Z-Test
---
gli _Z-Test_  il [[Test Statistici|test statistico]] sulla [[Statistica descrittiva - Dati Numerici#Media (definizione)|media]] di un [[Campione Statistico|campione]] [[Variabili Aleatorie Notevoli - Gaussiane|gaussiano]] con [[Variabili aleatorie - Varianza|varianza]] _nota_ 


#### Formulazione del test
_sia_
- $X_1\dots,X_{n}$ un [[Campione Statistico|campione statistico]] con legge [[Variabili Aleatorie Notevoli - Gaussiane|gaussiana]] $N(m,\sigma^{2})$ 
-  $\sigma^{2}>0$  la [[Variabili aleatorie - Varianza|varianza]] _nota_

_vogliamo_ effettuare un [[Test Statistici|test]] per determinare se la media $m$ coincide con un certo valore $m_{0}$.
Formalmente stiamo cercando $m=\theta \in \Theta=\mathbb{R}$ e $$\Theta_{0}=\{ m_{0} \}\ \ \  e\ \ \   \Theta_{1}=\mathbb{R} \backslash \{ m_{0} \}$$
e abbiamo quindi le ipotesi $$\mathcal{H}_{0})\ m=m_{0} \ \ \ \ \ \ \ \mathcal{H}_{1})\ m \not = m_{0}$$
Siccome la [[Idd - Media Campionaria|media campionaria]] $\overline{X}$ è uno [[Stimatori statistici#Stimatore corretto (Definizione)|stimatore corretto e consistente]] di $m$ allora possiamo definire la _regione critica_ come $$C = \{ |\overline{X}-m_{0}| >d \}$$dove il numero $d>0$ deve essere determinato in funzone del _livello_ $\alpha$  scelto e quindi $$\mathcal{P}_{m_{0}}\{ C \} \leq \alpha=\mathcal{P}_{m_{0}} \{ |\overline{X}-m_{0}| >d \} \leq \alpha$$Siccome vogliamo ottenere una _regione critica_ il più grande possibile per poter aumentare la _potenza del test_  possiamo imporre $$\mathcal{P}_{m_{0}} \{ |\overline{X}-m_{0}| >d \} = \alpha$$e quindi siccome $Z=\cfrac{\sqrt{n}(\overline{X}-m)}{\sigma}$ è [[Variabili Aleatorie Notevoli - Gaussiane|gaussiana standard]] vale che $$\begin{array}{}
\mathcal{P}_{m_{0}} \{ |\overline{X}-m_{0}| >d \} &  = \\
 \mathcal{P}_{m_{0}} \left\{  \cfrac{\sqrt{ n }}{\sigma}|\overline{X}-m_{0}| >\cfrac{d  \sqrt{ n  }}{\sigma}\right\} & = \\
\mathcal{P}\left\{  |Z| > \cfrac{d\sqrt{n}}{\sigma} \right\} & = \\
\alpha \\
\end{array}$$ e valendo $\cfrac{d\sqrt{ n }}{\sigma}=q_{1-\frac{\alpha}{2}}$ possiamo definire la _regione critica_ come $$
\begin{array}{}
C & = & \left\{  \sqrt{ n }\frac{|\overline{X}-m_{0} |}{\sigma}>q_{1-\frac{\sigma}{2}}  \right\} & \\ & =    & 
\left\{  | \overline{X}-m_{0} |> \frac{\sigma}{\sqrt{ n }}q_{1-\frac{\alpha}{2}}  \right\}
\end{array}$$
in pratica data una realizzazione $x_{1},\dots, x_{n}$ si calcola la _media_ $\overline{x}_{n}$ e 
si _rifiuta_ l ipotesi $\mathcal{H}_{0}$ se $|\overline{x}_{n}|>\sigma q_{1-\alpha/2}\sqrt{ n }$, 
si _accetta_ l ipotesi $\mathcal{H}_{0}$ in caso contrario.

>[!tip]
>Si nota facilmente che l'ipotesi $\mathcal{H}_0: m = m_0$ è accettata al livello $\alpha$ se e solo se $m_0$ appartiene all'intervallo di fiducia per la media con livello di fiducia $1-\alpha$. Questa è una proprietà generale: si può dimostrare che è equivalente identificare un intervallo di fiducia al livello $1-\alpha$ oppure un test nel quale l'ipotesi è semplice, cioè ridotta a un solo parametro. 

#### Calcolo del p-value
per calcolare il _p-value_ della realizzazione $(x_{1},\dots,x_{n})$ si procede usando la definizione _informale_ e quindi calcoliamo il p-value come probabilita di ottenere i _valori piu estremi_ rispetto al ipotesi $\mathcal{H}_{0}$ e in questo caso sono.
Considerando $(y_{1},\dots,y_{n})$ e $\overline{x}_{n}$ e $\overline{y}_{n}$ le rispettive [[Idd - Media Campionaria|medie campionarie]] sono valori piu estremi quelli per cui vale $$|\overline{y}_{n}-m_{0}| > |\overline{x}_{n}-m_{0}|$$  e quindi il _p-value_ $$\begin{array}{}
\overline{\alpha}=\overline{\alpha}(x_{1},\dots,x_{n}) & = \\
\mathcal{P}_{m_{0}}\left\{ \sqrt{ n }\cfrac{|\overline{X}-m_{0}|}{\sigma}>\cfrac{\sqrt{ n }}{\sigma}|\overline{x}-m_{0}|   \right\} & = \\
2\left[ 1-\Phi\left( \frac{\sqrt{ n }}{\sigma}|\overline{x}-m_{0}| \right) \right]
\end{array}
$$
in l ultimo passaggio è giustificato dal fatto che $Z=\sqrt{ n }(\overline{X}-m_{0})/\sigma$ è [[Variabili Aleatorie Notevoli - Gaussiane|gaussina standard]].

dobbiamo ora verificare che questa rispetti la _[[Test Statistici#P-value|definizione rigorosa]]_ del _p-value_, dobbiamo quindi verificare che il test di livello $\alpha$ rifiuta $\mathcal{H}_{0}$ solo se $\alpha>\overline{\alpha}$. 
sappiamo che $\mathcal{H}_{0}$ è rifiutata al livello $\alpha$ se s solo se $\frac{\sqrt{ n }}{\sigma}|\overline{x}-m_{0}|>q_{1-\alpha/2}$. quindi in caso di rifiuto abbiamo $$ \begin{array}{}
\overline{\alpha} & = & \mathcal{P}_{m_{0}}\left\{  \sqrt{ n }\frac{|\overline{X}-m_{0}|}{\sigma}>\frac{\sqrt{ n }}{\sigma}| \overline{x}-m_{0}|  \right\} \\
 &  < & \mathcal{P}_{m_{0}} \left\{  \sqrt{ n }\frac{|\overline{X}-m_{0}|}{\sigma}>q_{1-\alpha/2}  \right\}  \\
	 & = & \alpha
\end{array}$$
mentre in caso di _accettazione_ vale la diseguaglianza opposta e quindi $\overline{\alpha}$ soddisfa la definizione di _p-value_.

#### Curva operativa
Calcoliamo ora la curva operativa $\beta(m)$ (probabilità di accettare quando $m$ è il valore del parametro) al livello $\alpha$ :
$$
\begin{aligned}
\beta(m) & =\mathcal{P}_m\left\{\frac{\sqrt{n}}{\sigma}\left|\bar{X}-m_0\right| \leq q_{1-\frac{\alpha}{2}}\right\}=\mathcal{P}_m\left\{-q_{1-\frac{\alpha}{2}} \leq \frac{\sqrt{n}}{\sigma}\left(\bar{X}-m_0\right) \leq q_{1-\frac{\alpha}{2}}\right\} \\
& =\mathcal{P}_m\left\{\sqrt{n} \frac{\left(m_0-m\right)}{\sigma}-q_{1-\frac{\alpha}{2}} \leq \frac{\sqrt{n}}{\sigma}(\bar{X}-m) \leq \sqrt{n} \frac{\left(m_0-m\right)}{\sigma}+q_{1-\frac{\alpha}{2}}\right\} \\
& =\Phi\left(\sqrt{n} \frac{\left(m_0-m\right)}{\sigma}+q_{1-\frac{\alpha}{2}}\right)-\Phi\left(\sqrt{n} \frac{\left(m_0-m\right)}{\sigma}-q_{1-\frac{\alpha}{2}}\right)=: h\left(\sqrt{n} \frac{m-m_0}{\sigma}\right) .
\end{aligned}
$$ si puo dimostrare che la [[Funzioni|funzione]] $h$ è pari, cioè $$h(x)=h(|x|)= \Phi(|x|+q_{1-\alpha/2})$$
ed è decrescente in $x \geq 0$ (ad $\alpha$ fissato). Quindi più $\sqrt{n} \frac{\left|m-m_0\right|}{\sigma}$ è grande, più piccola è la curva operativa $\beta(m)$, e quindi più grande è la potenza $1-\beta(m)$. Ne segue che, per aumentare la potenza lasciando fisso il livello $\alpha$ del test, si può aumentare la taglia $n$ del campione. Più precisamente, fissati $m \neq m_0$ e $\beta_0 \in(0,1)$, usando la semplice stima
$$\begin{array}{}
 &  & \beta(m)   \\
 & = &  \Phi\left(\sqrt{n} \frac{\left|m_0-m\right|}{\sigma}+q_{1-\frac{\alpha}{2}}\right)-\Phi\left(\sqrt{n} \frac{\left|m_0-m\right|}{\sigma}-q_{1-\frac{\alpha}{2}}\right)  \\
 & \leq &  1-\Phi\left(\sqrt{n} \frac{\left|m_0-m\right|}{\sigma}-q_{1-\frac{\alpha}{2}}\right)
\end{array}
$$
e imponendo che
$$
1-\Phi\left(\sqrt{n} \frac{\left|m_0-m\right|}{\sigma}-q_{1-\frac{\alpha}{2}}\right) \leq \beta_0
$$
si trova il valore $n$ per cui la curva operativa del test è inferiore a $\beta_0$ (cioè la potenza in $m$ è superiore a $\left.1-\beta_0\right)$. Si può infine dimostrare che, a $m$ fissato, la curva operativa aumenta all'aumentare di $\alpha$.


### Z-test Unilatero
Occupiamoci ora, questa volta senza ripetere tutti i dettagli, dello Z-test per la media di un campione Gaussiano a varianza nota con ipotesi alternative
$$
\left.\left.\mathscr{H}_0\right) m \leq m_0 \quad \text { contro } \quad \mathscr{H}_1^{\prime}\right) m>m_0 .
$$

Lo sviluppo del test è analogo al caso bilatero, e ometteremo i dettagli.
- Formulazione del test: L'intuizione ci spinge a rifiutare l'ipotesi se $\left(\bar{X}-m_0\right)$ è troppo grande, cioè a considerare una regione critica della forma $C=\left\{\left(\bar{X}-m_0\right)>d\right\}$, e la condizione sul livello diventa
$$
\forall m \leq m_0, \quad \mathbb{P}_m\left\{\left(\bar{X}-m_0\right)>d\right\} \leq \alpha .
$$

Si vede facilmente che la probabilità sopra scritta cresce al crescere di $m$ e si arriva (procedendo come nel caso precedente) a
$$
\mathbb{P}_{m_0}\left\{\left(\bar{X}-m_0\right)>d\right\}=\mathbb{P}_{m_0}\left\{\frac{\sqrt{n}}{\sigma}\left(\bar{X}-m_0\right)>\frac{d \sqrt{n}}{\sigma}\right\}=\alpha,
$$
da cui segue $\frac{d \sqrt{n}}{\sigma}=q_{1-\alpha}$ : la regione critica al livello $\alpha$ diventa pertanto
$$
C=\left\{\sqrt{n} \frac{\left(\bar{X}-m_0\right)}{\sigma}>q_{1-\alpha}\right\}=\left\{\left(\bar{X}-m_0\right)>\frac{\sigma}{\sqrt{n}} q_{1-\alpha}\right\} .
$$

La dipendenza dell'ampiezza della regione di accettazione $C^{\complement}$ dai parametri $\alpha, \sigma, n$ è la stessa del caso bilatero.
- Calcolo del p-value: Calcoliamo il $p$-value dei dati $\left(x_1, \ldots x_n\right)$. In questo caso, $\mathrm{i}$ dati $\left(y_1, \ldots y_n\right)$ sono "più estremi" di $\left(x_1, \ldots x_n\right)$ rispetto ad $\mathscr{H}_0: m \leq m_0$ se $\bar{y}_n-m_0>\bar{x}_n-m_0$. La probabilità, per $m \leq m_0$ di avere "dati più estremi" di $\left(x_1, \ldots x_n\right)$ e
$$
\mathbb{P}_m\left\{\sqrt{n} \frac{\left(\bar{X}-m_0\right)}{\sigma}>\frac{\sqrt{n}}{\sigma}\left(\bar{x}-m_0\right)\right\}
$$

Come $p$-value si prende il massimo di tali probabilità per $m \in \mathscr{H}_0: m \leq m_0$, che si realizza in $m_0:$ il $p$-value diventa
$$
\bar{\alpha}\left(x_1, \ldots x_n\right)=\mathbb{P}_{m_0}\left\{\sqrt{n} \frac{\left(\bar{X}-m_0\right)}{\sigma}>\frac{\sqrt{n}}{\sigma}\left(\bar{x}-m_0\right)\right\}=1-\Phi\left(\frac{\sqrt{n}}{\sigma}\left(\bar{x}-m_0\right)\right)
$$
e si può verificare che tale valore verifica la definizione rigorosa di $p$-value.

- _Curva operativa_: La curva operativa è la funzione
$$
\beta(m)=\mathbb{P}_m\left\{\frac{\sqrt{n}}{\sigma}\left(\bar{X}-m_0\right) \leq q_{1-\alpha}\right\}=\Phi\left(\sqrt{n} \frac{\left(m_0-m\right)}{\sigma}+q_{1-\alpha}\right) .
$$

Poiché $\Phi$ è crescente, per $m>m_0$ la curva operativa è decrescente in $\sqrt{n} \frac{\left(m_0-m\right)}{\sigma}$. In particolare, a $m$ e $\beta_0$ fissati, imponento $\beta(m)=\beta_0$ si può trovare $n$ tale che il test abbia potenza $1-\beta_0$ per il valore $m$ fissato.

Se l'ipotesi è della forma $\left.\mathscr{H}_0\right) m \geq m_0$, si invertono tutte le diseguaglianze e si sostituisce $q_{1-\alpha}$ con $q_\alpha$. Precisamente, la regione critica è
$$
C=\left\{\sqrt{n} \frac{\left(\bar{X}-m_0\right)}{\sigma}<q_\alpha\right\},
$$
il $p$-value è
$$
\bar{\alpha}\left(x_1, \ldots x_n\right)=\mathbb{P}_{m_0 0}\left\{\sqrt{n} \frac{\left(\bar{X}-m_0\right)}{\sigma}<\frac{\sqrt{n}}{\sigma}\left(\bar{x}-m_0\right)\right\}=\Phi\left(\frac{\sqrt{n}}{\sigma}\left(\bar{x}-m_0\right)\right)
$$
e la curva operativa è
$$
\beta(m)=\mathbb{P}_m\left\{\frac{\sqrt{n}}{\sigma}\left(\bar{X}-m_0\right) \geq q_\alpha\right\}=1-\Phi\left(\sqrt{n} \frac{\left(m_0-m\right)}{\sigma}+q_\alpha\right) .
$$