---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Intervalli di fiducia - Variabile di bernulli
---

_Sia_  $X_{1},\dots,X_{n}$ un [[Campione Statistico|campione statistico]]  con [[Probabilita sui numeri Reali|legge di probabilita]] di [[Variabili Aleatorie Notevoli - Binomiale#Variabile di bernulli|bernulli]]  $B(p)$. Avremmo che la [[Idd - Media Campionaria|media campionaria]]  $\overline{X}_{n}$è un [[Stimatori statistici#Stimatore corretto (Definizione)|buon stimaotore]] del parametro $p$  e quindi cerchiamo degli [[Intervalli di fiducia|intervalli di fiducia]] della forma $$[\overline{X}_{n}\pm d]$$la variabile di [[Variabili Aleatorie Notevoli - Binomiale#Variabile di bernulli|bernulli]] ha [[Quantili di variabili aleatorie|quantili]] piu complicati rispetto alla [[Variabili Aleatorie Notevoli - Gaussiane|gaussiana standard]] siccome il [[Campione Statistico|campione]] $X_{1}+\dots+X_{n}$ ha legge [[Variabili Aleatorie Notevoli - Binomiale|binomiale]] $B(n,p)$   abbiamo che i quantili, usati nella determinazione del [[Intervalli di fiducia|intervallo di fiducia]], dipendono anche da $n$.
Usando il [[Teorema centrale del limite|teorema centrale del limite]] possiamo dire che $$\frac{X_{1}+\dots+X_{n}-np}{\sqrt{ np(1-p) }}=\sqrt{ n }\frac{\overline{X}_{n}-p}{\sqrt{ p(p-1) }}$$ è approssimativamente una [[Variabili Aleatorie Notevoli - Gaussiane|gaussiana standard]]. la _[[Variabili aleatorie - Varianza|varianza]]_ non è ancora nota ma è in funzione di $p$ infatti $var(X_{1})=p(1-p)$ e siccome $\overline{X}_{n}$ è un [[Statistica Parametrica#Stimatore corretto (Definizione)|buon stimatore]] di $\mathbb{E}[X_{i}]=p$ (e questo viene dal fatto che $X_{i}$ è una [[Variabili Aleatorie Notevoli - Bernulli|variaible di bernulli]] ) vale che la _varianza_ sia stimabile da $\overline{X}_{n}(1-\overline{X}_{n})$ è si dimostra che $$\frac{X_{1}+\dots+X_{n}-np}{\sqrt{ n\overline{X}_{n}(1-\overline{X}_{n}) }}=\sqrt{ n }\frac{\overline{X}_{n}-p}{\sqrt{ \overline{X}_{n}(\overline{X}_{n}-1) }}$$[[Convergenza in distribuzione|converge in distribuzione]] ad una [[Variabili Aleatorie Notevoli - Gaussiane|gaussiana standard]] per $n \to \infty$


#### Intervallo di fiducia per la media 
_sia_
- $X_{1},\dots,X_{n}$ un [[Campione Statistico|campione]] con legge di [[Variabili Aleatorie Notevoli - Binomiale#Variabile di bernulli|bernulli]]
- dato $\alpha \in (0,1)$
_allora_ l [[Intervalli di fiducia#Intervallo aleatorio o casuale (Definizione)|intevallo aleatorio]] $$\left[ \overline{X}_{n}\pm \sqrt{\frac{\overline{X}_{n}(1-\overline{X}_{n})}{n}}q_{1-\alpha/2} \right]$$
è un [[Intervalli di fiducia|interevalli di fiducia]] per la media $p$ del [[Campione Statistico|campione]] $X_{1},\dots X_{n}$ con un livello di fiducia approssimativamente $1-\alpha$. Si ha $$\lim_{ n \to \infty }\mathcal{P}\left\{ p \in  \left[ \overline{X}_{n}\pm \sqrt{\frac{\overline{X}_{n}(1-\overline{X}_{n})}{n}}q_{1-\alpha/2} \right] \right\} = 1-\alpha $$
dove il termine _aprossimativo_ si riferisce al fatto che $\alpha$ fissato il _livello di fiducia_ non è esattamente $1-\alpha$  ma al aumentare di $n$ l errore è trascurabile.

la precisone della stima   $$d=\sqrt{ \frac{\overline{X}_{n}(1-\overline{X}_{n})}{n} }q_{1-\alpha/2}$$è anche essa _approssimativa_ 
  