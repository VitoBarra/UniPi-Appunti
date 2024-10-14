---
Subject: "[[Algebra Lineare (AL)]]"
tags:
  - AL
topic:
---


# Autospazio
---
_Sia_ 
- $T : V \rightarrow V$ un [[Isomorfismo e Endomorfismo#Endomorfismo|endomorfismo]]. 
 - [[Autovettori e Autovalori|autovalore]] $\lambda$ di $T$
  _allora_  $\forall \lambda$ definiamo l’__autospazio__ $V_{\lambda} \subset V$ come$$
V_\lambda = \{v \in V \ | \ T(v) = \lambda v \}
$$
L'autospazio $V_\lambda$ è composto da tutti gli [[Autovettori e Autovalori|autovettori]] $v$ con [[Autovettori e Autovalori|autovalore]] $\lambda$, più I' origine $0 \in  V$ 

Per ogni autovalore $\lambda$ di $T$, ha senso considerare I'[[Isomorfismo e Endomorfismo|endomorfismo]] $T - \lambda \cdot id$ di $V$ che manda $v$ in $T(v)-\lambda v$ e la proposizione seguente lo mette in relazione con l'autospazio $V_\lambda$. 

##### Preposizione
Per ogni autovalore $\lambda$  di $T$ abbiamo $$V_\lambda = ker(T - \lambda\cdot id)$$dove $ker$ indica il [[Nucleo di un applicazione lineare|nucleo]]

###### Corollario
sia $V_\lambda \subset V$ un __autospazio__ 
_allora_ $V_\lambda$ è un [[Sottospazio Vettoriale|sottospazio vettoriale]] di $V$



##### Proposizione
_Sia_ 
- $T:V \to V$ un [[Isomorfismo e Endomorfismo|endomorfismo]]
- $\lambda_1 \dots \lambda_k$ i [[Calcolo di autovalori|autovalori]] di $T$
_allora_ vale che $$V_{\lambda_1}\oplus\dots \oplus V_{\lambda_k}$$
Ovvero gli __autospazzi__ di un endomorfismo sono sempre in [[Spazi vettoriali in somma diretta|somma diretta]]

###### Corollario
L [[Isomorfismo e Endomorfismo|endomorfismo]] $T$ é [[Matrici Diagonalizzabili|diagonalizzabile]] $\iff$ $$V=V_{\lambda_1}\oplus\dots \oplus V_{\lambda_k}$$ ovvero se la somma degli auto spazzi di $V$ generano tutto $V$ 

