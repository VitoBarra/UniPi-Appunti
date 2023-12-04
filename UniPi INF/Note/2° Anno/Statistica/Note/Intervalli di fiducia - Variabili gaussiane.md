---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Intervalli di fiducia - Variabili gaussiane
---

#### Intervalli di fiducia per variabili gaussiane
_sia_ $X_{1},\dots,X_{n}$ un [[Campione Statistico|campione statistico]] con [[Probabilita sui numeri Reali|legge di probabilita]] [[Variabili Aleatorie Notevoli - Gaussiane|gaussiana]] $N(m,\sigma^{2})$  questa ha due parametri la media $m$ e la varianza $\sigma^{2}$

un [[Statistica Parametrica#Stimatore corretto (Definizione)|buon stimatore]] per la [[Statistica descrittiva - Dati Numerici#Media (definizione)|media]] è la [[Idd - Media Campionaria|medica campionaria]] $\overline{X}$  quindi cerchiamo [[Intervalli di fiducia#Intervallo di fiducia|Intervallo di fiducia]] della forma $$I=[\overline{X}-d,\overline{X}+d]= [\overline{X} \pm d]$$dove $d> 0$ e l ultima espressione è un abbreviazione della prima, $d$ deve assicurare livello di _[[Intervalli di fiducia|fiducia alto]]_ ma non deve o essere _troppo grande_

#### Precisione della stima (Definizione)
_se_ $[\overline{X}\pm d]$ con $d>0$  è un intervallo di fiducia per $m$
_allora_ è detto
- _precisione della stima_ il valore $d$
- _precisione relatova della stima_ il valore $\cfrac{d}{\overline{X}_{n}}$

#### Intervalli di fiducia per la media di un campione gaussiano, varianza nota
_Sia_
- $X_{1},\dots X_{n}$ un [[Campione Statistico|Campione Statistico]] con _legge di probabilita_ [[Variabili Aleatorie Notevoli - Gaussiane|gaussiana]]
-  $\overline{X}_{n}$ la [[Idd - Media Campionaria|media campionaria]] 
- $\alpha \in (0,1)$  un numero 
-  $\sigma > 0$ la [[Variabili aleatorie - Varianza|varianza]] nota 
_allora_ l [[Intervalli di fiducia#Intervallo aleatorio o casuale (Definizione)|intervallo aleatorio]] $$I=\left[ \overline{X}_{n}\pm \frac{\sigma}{\sqrt{ n }}q_{1-\frac{\alpha}{2}} \right] $$ è un [[Intervalli di fiducia|intervallo di fiducia]] per la media $m$ del campione $X_{1},\dots,X_{n}$ con _livello di fiducia_ $1-\alpha$
 
_dimostrazione_
dobbiamo imporre che $$
\begin{array}{}
i -\alpha  & \leq \\
 \mathcal{P}_{m}(m \in  I)  & = \\
\mathcal{P}_{\theta}(|\overline{X}-m |\leq d) & = \\
\mathcal{P}_{\theta}\left( \cfrac{\sqrt{ n }}{\sigma}|\overline{X}-m| \leq \cfrac{d\sqrt{ n }}{\sigma} \right)
\end{array}
$$
da cui l ultimo passaggio è giustificato da fatto che $\sqrt{ n }|\overline{X}_{n}-m|/\sigma$ è [[Variabili aleatorie Gaussiane|gaussiana standard]]. 
Stiamo cercando di minimizzare $d$ e questo è minimo scegliendo il [[Quantili di variabili aleatorie|quantile]] $\cfrac{d\sqrt{ n }}{\sigma}=q_{1-\frac{\alpha}{2}}$ da cui la tesi.


_Osservazioni_
si osserva che la precisione $d$
- creresce al cresce del _[[Intervalli di fiducia|Livello di fiducia]]_ $1-\alpha$
- cresce al cresce della _[[Idd - varianza campionaria|varianza]]_ $\sigma^{2}$
- decresce al crescere di $n$ ovvero il numero di esiti
 

#### Intervalli di fiducia per la media di un campione gaussiano, varianza NON nota
_Sia_
- $X_{1},\dots X_{n}$ un [[Campione Statistico|Campione Statistico]] con _legge di probabilita_ [[Variabili aleatorie Gaussiane|gaussiana]]
-  $\overline{X}_{n}$ la [[Idd - Media Campionaria|media campionaria]] 
- $\alpha \in (0,1)$  un numero 
-  $S^{2}_{n}$ la  [[Idd - varianza campionaria|varianza campionaria]]  (questa è [[Statistica Parametrica#Stimatore corretto (Definizione)|stimatore corretto]]  della varianza $\sigma^{2}$)
_allora_ l [[Intervalli di fiducia#Intervallo aleatorio o casuale (Definizione)|intervallo aleatorio]] $$I=\left[ \overline{X}_{n}\pm \frac{S^{2}_{n}}{\sqrt{ n }}\uptau_{1-\frac{\alpha}{2},n-1} \right] $$dove $\uptau$ è il [[Quantili di variabili aleatorie|quantile]] della [[Densita di probabilita Student|variabile di student]]  
è un [[Intervalli di fiducia|intervallo di fiducia]] per la _media_ $m$ del campione $X_{1},\dots,X_{n}$ con _livello di fiducia_ $1-\alpha$ 


>[!tip]
>se $n\geq 60$ si puo a prossimare il quantile $\tau$ con quella della [[Variabili aleatorie Gaussiane|variabile gaussiana standard]]



#### Intervalli di fiducia unilaterali per la media, Varianza nota
_Sia_
- $X_{1},\dots X_{n}$ un [[Campione Statistico|Campione Statistico]] con _legge di probabilita_ [[Variabili aleatorie Gaussiane|gaussiana]]
-  $\overline{X}_{n}$ la [[Idd - Media Campionaria|media campionaria]] 
- $\alpha \in (0,1)$  un numero 
-  $\sigma > 0$ la [[Variabili aleatorie - Varianza|varianza]] nota 
_allora_ l [[Intervalli di fiducia#Intervallo aleatorio o casuale (Definizione)|gli intervalli]] $$
\begin{array}{}
I_+  & = & \left(-\infty, \overline{X}_{n}+ \frac{\sigma}{\sqrt{ n }}q_{1-\frac{\alpha}{2}} \right] \\ I_-  & = &  \left[\overline{X}_{n}- \frac{\sigma}{\sqrt{ n }}q_{1-\frac{\alpha}{2}},+\infty \right)
\end{array}
$$ è un [[Intervalli di fiducia|intervallo di fiducia]] per la media $m$ del campione $X_{1},\dots,X_{n}$ con _livello di fiducia_ $1-\alpha$




#### Intervalli di fiducia  unilaterali per la media di un campione gaussiano, varianza NON nota
_Sia_
- $X_{1},\dots X_{n}$ un [[Campione Statistico|Campione Statistico]] con _legge di probabilita_ [[Variabili Aleatorie Notevoli - Gaussiane|gaussiana]]
-  $\overline{X}_{n}$ la [[Idd - Media Campionaria|media campionaria]] 
- $\alpha \in (0,1)$  un numero 
-  $S^{2}_{n}$ la  [[Idd - varianza campionaria|varianza campionaria]]  (questa è [[Statistica Parametrica#Stimatore corretto (Definizione)|stimatore corretto]]  della varianza $\sigma^{2}$)
_allora_ l [[Intervalli di fiducia#Intervallo aleatorio o casuale (Definizione)|gli intervalli]] $$
\begin{array}{}
I_+  & = & \left(-\infty, \overline{X}_{n}+ \frac{S^{2}_{n}}{\sqrt{ n }}\uptau_{1-\frac{\alpha}{2},n-1} \right] \\ I_-  & = &  \left[\overline{X}_{n}- \frac{S^{2}_{n}}{\sqrt{ n }}\uptau_{1-\frac{\alpha}{2},n-1},+\infty \right)
\end{array}
$$$$I=\left[  \right] $$dove $\uptau$ è il [[Quantili di variabili aleatorie|quantile]] della [[Variabili aleatorie notevoli - Student|variabile di student]]  
è un [[Intervalli di fiducia|intervallo di fiducia]] per la _media_ $m$ del campione $X_{1},\dots,X_{n}$ con _livello di fiducia_ $1-\alpha$ 





#### Intervalli di fiducia per la varianza
_Sia_
- $X_{1},\dots X_{n}$ un [[Campione Statistico|Campione Statistico]] con _legge di probabilita_ [[Variabili Aleatorie Notevoli - Gaussiane|gaussiana]]
- $\overline{X}_{n}$ la [[Idd - Media Campionaria|media campionaria]] 
- $S^{2}_{n}$ la  [[Idd - varianza campionaria|varianza campionaria]]  (questa è [[Statistica Parametrica#Stimatore corretto (Definizione)|stimatore corretto]]  della varianza $\sigma^{2}$)
- $\alpha \in (0,1)$  un numero 
_allora_ l [[Intervalli di fiducia#Intervallo aleatorio o casuale (Definizione)|gli intervalli bilaterali]]   $$ \begin{array}{}
\displaystyle I_{-} & = & \displaystyle\left( 0,\frac{\sum^{n}_{i=1}(X_{i}-\overline{X}_{i})^{2}}{\chi^{2}_{\alpha,n-1}} \right]   \\
  & = & \displaystyle\left(0,\frac{(n-1)S^{2}_{n}}{\chi^{2}_{\alpha,n-1}}\right]\\ \\

\displaystyle I_{+} & = & \displaystyle\left[ \frac{\sum^{n}_{i=1}(X_{i}-\overline{X}_{i})^{2}}{\chi^{2}_{(\alpha-1,n-1)}} ,+\infty\right)   \\
& = & \displaystyle\left[\frac{(n-1)S^{2}_{n}}{\chi^{2}_{(1-\alpha,n-1)}},+\infty\right) 
\end{array}
$$Sono [[Intervalli di fiducia|intervalli di fiducia]] per la [[Variabili aleatorie - Varianza|Varianza]] per $\sigma^{2}$ rispettivamente _sinistro e destro_ con _livello di fiducia_ $1-\alpha$ 
Dove $\chi_{(\beta,n-1)}^{2}$ indica il [[Quantili di variabili aleatorie|quantile]] della variabile di tipo [[Variabili aleatorie Notevoli - Chi-quadro|Chi-quadro]] $\chi^{2}(n-1)$.

infatti questo dipende dal fatto che 
_se_ $X_{1},\dots,X_{n}$ è un campione di tipo [[Variabili Aleatorie Notevoli - Gaussiane|gaussiano]] $N(m,\sigma^{2})$
_allora_ la [[Variabili Aleatorie (Casuali)|variabile]]  $$\sum^{n}_{i=1}\frac{(X_{i}-\overline{X}_{n})^{2}}{\sigma^{2}}=(n-1)\frac{S^{2}_{n}}{\sigma^{2}}$$ è di tipo [[Variabili aleatorie Notevoli - Chi-quadro|chi-quadro]] $\chi^{2}(n-1)$

