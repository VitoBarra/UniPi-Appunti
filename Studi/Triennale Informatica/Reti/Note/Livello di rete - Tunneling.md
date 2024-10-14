---
Subject: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
---

Prev: [[Reti]]

# Livello di rete - Tunneling
---
se si lavora in [[Livello di rete - IP#IPv6|IPv6]] e ci sono dei percorsi che hanno segmenti di rete con [[Livello di rete - IP#IPv4|IPv4]] 
![[Pasted image 20230109004908.png]]
per garantire la consegna si utilizza il tunneling ovvero
il datagramma che viaggia con il pv6 prima di passare ad un [[Livello di rete - Router]] ipv4 è incapsulato in un datagramma IPv4. una volta uscito da tunnel si decapsula e torna a viaggiare il datagramma originale 
nel ipv4 del header aggiunto la sorgente sara l indirizzo ipv4 di B e come destinazione E
![[Pasted image 20230109005738.png]]
Se c è Frammentazione nel tunnel viene riassemlato dal router che supporta Ipv6 alla fine del tunnel quindi in questo esempio E 


