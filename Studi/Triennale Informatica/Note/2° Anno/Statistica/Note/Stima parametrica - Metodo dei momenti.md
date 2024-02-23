---
Subject: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Stima parametrica - Metodo dei momenti
--- 

#### Metodo dei momenti
_sia_ $X_{1},\dots X_{n}$ un [[Campione Statistico|campione statistico]] la cui [[Probabilita sui numeri Reali|legge di probabilita]] dipende da un _parametro_ $\theta \in \Theta$ 
nel _metodo dei momento_ si confronta i [[Variabili aleatoria - Momenti|mementi teorici]] in questo caso il valore atteso  $$m_{k}(\theta)=\mathbb{E}[X^{k}]$$con i _momenti empirici_ (la [[Idd - Media Campionaria|media campionaria]])$$\sum^{n}_{i=1}\frac{x_{i}^{k}}{n}$$ la media campionaria è un [[Statistica Parametrica#Stimatore corretto (Definizione)|buon stimatore]]  del _valore atteso_ e quindi si ò scegliere  uno stimatore di $\theta$ un $\tilde{\theta}$ che realizzi l e uguaglianza tra _momenti teorici_ e _momenti empirici_

##### Stima con il metodo dei momenti (Definizione)
_sia_ $X_{1},\dots X_{n}$ un [[Campione Statistico|campione statistico]]
_allora_ si chiama _stima col metodo dei momenti_ se esiste una [[Statistica Parametrica#Statistica campionaria (definizione)|statistica campionaria]] $\tilde{\theta}=\tilde{\theta}(X_{1},\dots ,X_{n})$ che permetta di eguagliare alcuni _momenti teorici_ con alcuni _momenti empirici_ ovvero vale per 1 o più $k$ positivi $$\mathbb{E}\left[X^{k}\right]=\frac{1}{n}\sum^{n}_{i=1}x^{k}_{i} \ \ \ \ \ \forall  (x_{1},\dots, x_{n})$$