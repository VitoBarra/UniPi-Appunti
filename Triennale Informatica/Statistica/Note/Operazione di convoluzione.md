---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Operazione di convoluzione
---
La __convoluzione__ è un'[[Operazioni algebriche|operazione matematica]] solitamente denotata con  $*$ e viene utilizzata in diversi ambiti, come nelle [[Convolutional Neural Network  (CNN)|Convolutional Neural Network  (CNN)]] che prendono il nome proprio da questa operazione e nell'_[[Immage Processing|image processing]]_, dove viene impiegata per il [[Filtering|filtraggio]] delle immagini.  

L'idea generale di questa operazione è quella di calcolare una media pesata di una funzione $f$ utilizzando i pesi definiti da un'altra funzione $g$. 
Formalmente, la convoluzione discreta tra due funzioni $f$ e $g$  è definita come:  $$
(f * g)(n) = \sum_{m=-\infty}^{\infty} f(m) g(n-m)
$$Mentre, nella forma continua è data da:  $$
(f * g)(t) = \int_{-\infty}^{\infty} f(\tau) g(t - \tau) d\tau
$$
Questa operazione ha molteplici applicazioni:  
- **Elaborazione delle immagini**: applicazione di filtri convoluzionali per il miglioramento e l'estrazione di caratteristiche nelle immagini.  
- **Elaborazione del segnale**: utilizzata nei sistemi di filtraggio per migliorare la qualità del segnale o rimuovere rumori indesiderati.  
- **Riconoscimento dei pattern**: fondamentale nelle reti neurali convoluzionali (CNN), dove viene utilizzata per l'estrazione di caratteristiche significative dalle immagini.  
- **Equazioni differenziali**: la convoluzione aiuta a risolvere equazioni differenziali lineari e sistemi dinamici.  

La convoluzione possiede anche alcune proprietà fondamentali, tra cui:  
- [[Proprietà del operazioni - Commutativita|Commutatività]]:   $f * g = g * f$ 
- [[Proprietà del operazioni - Associativa|Associatività]]:   $f * (g * h) = (f * g) * h$
- [[Proprietà del operazioni - Distributività|Distributività]]: $f * (g + h) = (f * g) + (f * h)$
- __[[Operazioni - Elemento Neutro o identita|Elemento neutro]]__: la convoluzione con la delta di Dirac o con l'impulso unitario lascia invariata la funzione originale.  


>[!tip] intuizione visiva
>questo da un [idea visuale](https://youtu.be/IaSGqQa5O-M?si=H2xv8S8jRUAUTuHl) di cosa rappresentano le convoluzioni



