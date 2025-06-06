---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Variabili Aleatorie notevoli - Student
---
#### Densita di student (Definizione)
_siano_ $X,C_{n}$ due [[Variabili Aleatorie (Casuali)|variabili aleatorie]] 
- $X \sim N(0,1)$  [[Variabili Aleatorie Notevoli - Gaussiane|gaussiana standard]] 
- $C_{n} \sim \chi^{2}$ ovvero [[Variabili Aleatorie Notevoli - Chi-quadro|chi-quadro]]  
_se_ queste sono [[Indipendenza di Variabili aleatorie|indipendenti]] 
_allora_ per $n>1$ la variabile aleatoria $$T_{n}=\frac{X}{\sqrt{ \frac{C_{n}}{n} }}=\sqrt{ n }\frac{X}{C_{n}}$$ ha _[[Probabilita sui numeri Reali#Densità di probabilità (Definizione)|densita]]_ valida che è $$f_{T_{n}}(t)=\frac{\Gamma(n/2+1/2)}{\sqrt{ n \pi }\Gamma(n/2)}\left( 1+\frac{t^{2}}{n} \right)^{-n/2-1/2}$$ che dipende dalla [[Funzione Gamma di Eulero|funzione gamma]]. e questa è detta _variabile di student_ a $n$ gradi di liberta



#### Proposizione
la densita $T_{n}$ è una [[Funzioni|funzione pari]], di conseguenza indichiamo con 
- $F_{n}(x)$ la [[Funzione di Ripartizione|funzione di ripartizione]] 
- $\tau_{(\alpha,n)}$ il $\alpha$-[[Quantili di variabili aleatorie|quantile]]
 e questi valgono $$F_{n}(-x)=1-F_{n}(x)\ \ \ \ \ \ \ \ \ \ \tau_{(\alpha,n)}=\tau_{(1-a,n)} $$la variabile $T_{n}$ ha [[Variabili aleatoria - Momenti|momenti]] fino al ordine $n-1$ e i momenti di ordine _dispari_ sono nulli. 



#### Teorema 
_sia_ $T_{n}$ la [[Variabili Aleatorie (Casuali)|variaible]] di _student_
_allora_ questa per $n$ grande la successione $(T_{n})_{n\geq 1}$ [[Convergenza in distribuzione|converge in distribuzione]] ad $N(0,1)$ ovvero ad una [[Variabili Aleatorie Notevoli - Gaussiane|gaussiana standard]].

##### Teoria
per via di questo teorema quando si usano le variabili di Student e si hanno tanto esperimenti questa viene sostituita con una _gaussiana standard_.

La differenza tra  variabile di _student_ e _gaussiana_ le due e che la variabile di _student_  per $|x| \to \infty$ tende a $0$ più lentamente 



#### Tavola quantili Student
![[IMG_0864.jpeg]]
 