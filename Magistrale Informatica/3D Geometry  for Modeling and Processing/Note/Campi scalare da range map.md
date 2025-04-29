---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Campi scalare da range map
---
Il passaggio da [[Range map|range map]] a una [[Superfici implicite|superficie implicita]] in particolare le range map definiscono una superfici con [[Normale di una superfice parametrica|normale]]. Ogni superficie definisce di un **campo di distanza orientato**, cioè una funzione scalare che associa a ogni punto nello spazio la distanza **orientata** dalla superficie stessa, positiva da un lato e negativa dall’altro.
![[IMG - range map superfici con normali.png]]
Questo processo produce un campo tridimensionale continuo, detto **signed distance field**, che cattura la geometria locale della superficie osservata.
![[IMG - distance field con segno da superfici con normali.png]]
Considerando due di questi campi, $f_1(\mathbf{x})$ e $f_2(\mathbf{x})$, una prima operazione naturale è la loro combinazione tramite media aritmetica:$$
f_{\text{media}}(\mathbf{x}) = \frac{f_1(\mathbf{x}) + f_2(\mathbf{x})}{2}
$$Questo comporta che la nuova [[Superfici implicite|superficie implicita]] $S=\{x\mid f_{\text{media}}(\mathbf{x})=0\}$ si troverà all'incirca nel mezzo tra le due originali, secondo il contributo locale di ciascuna.
![[IMG - sommare e mediare i distance field.png]]
Tuttavia, questa media semplice può generare discontinuità evidenti. Nelle zone in cui le superfici sono molto vicine o si sovrappongono, il campo risultante presenta gradienti bruschi o superfici spurie, dovuti alla semplice interpolazione tra valori di distanza anche opposti.
![[IMG - salto improviso mediando i distance field.png]]
Per ottenere un risultato più coerente, si adotta una **media pesata** dei campi, dove il contributo di ciascun campo viene modulato in base alla distanza dal bordo della superficie originale. In questo modo, i punti lontani dal bordo influenzano maggiormente la media, mentre quelli vicini hanno peso minore. Formalmente:$$
f_{\text{pesato}}(\mathbf{x}) = \frac{w_1(\mathbf{x}) \cdot f_1(\mathbf{x}) + w_2(\mathbf{x}) \cdot f_2(\mathbf{x})}{w_1(\mathbf{x}) + w_2(\mathbf{x})}
$$dove $w_1$ e $w_2$ sono funzioni di peso che decrescono in prossimità dei bordi delle rispettive superfici.
![[IMG - media di distance field pesare la media con la distanza.png]]