---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Inferenza logica - Regola risoluzione binaria per FOL
---
La **regola di risoluzione per clausole** per la [[Logica del primo ordine (FOL)|logica del primo ordine]] rappresenta un'estensione della corrispondente[[Inferenza logica per dimostrazione di teoremi| regola proposizionale]] quindi è la sua versione [[Inferenza logica - regole di inferenza lifted|lifted]]

prese due setti di clausole, opportunamente standardizzate per non condividere variabili, possono essere risolte se contengono letterali complementari ovvero se uno [[FOL - Algoritmo di unificazione|unifica]] con la **negazione dell'altro**.  Formalmente $$\frac{l_1 \vee \cdots \vee l_i \vee \cdots \vee l_k, \quad m_1 \vee \cdots \vee m_j \vee \cdots \vee m_n} {\text{SUBST}(\theta, l_1 \vee \cdots \vee l_{i-1} \vee l_{i+1} \vee \cdots \vee l_k \vee m_1 \vee \cdots \vee m_{j-1} \vee m_{j+1} \vee \cdots \vee m_n)}
$$  dove $SUBST(\theta,\alpha)$ è l operazione di [[FOL - Sostituzione|Sostituzione]] e dove vale che $\text{UNIFY}(l_i, \neg m_j) = \theta$ che la sostituzione viene applicata a tutto il risultante che non hanno piu le due clausole complementari. Questa è **binary resolution rule** perche elimina esattamente due letterali.




> ![warning] 
> probabilmete esiste una versione estesa che risolve sub set