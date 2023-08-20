---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrari ibridi
---
i _Cifrari ibridi_ sona tipologia di _cifrario_ che utilizzano un [[Cifrari a chiave Simmetrica|cifrario asimmetrico]] e uno [[Cifrari a chiave Asimmetrica|asimmetrico]]

questo si fa perché solitamente i cifrari _asimmetrici_ sono molto meno efficienti dal punto di vista del tempo di crittazione e decriptazione ma non richiedono lo scambio di una chiave, mentre quelli _simmetrici_ sono molto veloci ma ha bisogno dello scambio.

per prendere il meglio dei due mondi si utilizza un cifrario _asimmetrico_ solo per lo scambio delle chiavi del cifrario _Simmetrico_  detta _chiave di sessione_ $k[sesion]$, ad ogni scambio di messaggi si varia la chiave per aumentare la sicurezza di questo tipi di cifrario, si potrebbe non fare ma se ne perde in sicurezza 

e abbiamo che lo schema dello scambio di messaggi è 
$$
\begin{array} {}
  \langle \mathcal{C}_{asim}(k[session],k[pub]) & \mathcal{C}_{sim}(m,k[session]) \rangle \\
  \langle \mathcal{D}_{asim}(k[session],k[priv]) & \mathcal{D}_{sim}(c,k[session]) \rangle
\end{array}
$$
