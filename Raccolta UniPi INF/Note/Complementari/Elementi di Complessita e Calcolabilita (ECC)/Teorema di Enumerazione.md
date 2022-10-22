---
type: nota
course: Elementi di calcolabilita e complessita
topic: 
tags: ECC
---

Prev: [[Elementi di Complessità e Calcolabilità (ECC)]]

# Teorema di Enumerazione
---

## Teorema
esiste una  [[Funzioni Parziali|funzione parziale ]][[Nozione di Calcolabilità|calcolabile]]  $\varphi$ tale che  
$$\exists z \ | \ \forall i,x \ \varphi_z(i,x) = \varphi_i(x)$$
#### dimostrazione
la funzione $U$ definita nel [[Teorema di forma normale]]  è una funzione calcolabile in due argomenti quindi questa funzione avrà un indice che noi chiamiamo $z$ quindi avremo che $\varphi_z(i,x) = U(\mu.T(i,x,y))$ e applicando il teorema di forma normale alla funzione $\varphi_z$ otteniamo che $U(\mu.T(i,x,y)) = \varphi_i(x)$ quindi   $$\varphi_z(i,x) = U(\mu.T(i,x,y)) = \varphi_i(x)$$ per transì vita la tesi è dimostrata. 
