---
Course: "[[Algebra Lineare (AL)]]"
tags:
  - AL
topic:
---

# Dipendenza Lineare
---
_sia_ 
- $V$ uno [[Spazi Vettoriali|spazio vettoriale]]  
- $v_{1},\dots v_{k} \in V$ [[Vettori|vettori]] con $k \geq 2$ 
_allora_ questi sono detti _dipendenti_ 
_se_ esiste almeno un coefficiente $\lambda_i \not= 0$  tale che$$
\lambda_1v_1+...+\lambda_kv_k=0$$
la _dipendenza lineare_ rende i vettori esprimibili in termini degli altri infatti possiamo scrivere$$
v_i=-\frac{\lambda_1}{\lambda_i}v_1-\dots-\frac{\lambda_k}{\lambda_i}v_k$$sono invece _linearmente indipendenti_ se **non** sono _linearmente dipendenti_

altre informazioni rilevanti
- Se $v_1, . . . , v_k$ sono indipendenti, allora qualsiasi sottoinsieme di $\{v1, . . . , vk \}$ è anch’esso formato da vettori indipendenti (questo perché se un sottoinsieme fosse dipendente renderebbe tutto l insieme dipendente basterebbero che i coefficienti rimasti fossero a 0)
- in un insieme di vettori indipendenti i vettori sonno a coppie non multiple e nessuno è il vettore nullo
