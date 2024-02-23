---
Subject: "[[Data Base (DB)]]"
topic: nota
tags:
  - DB
---

# Schema relazionali - Assiomi di Armstrong
---
#### Assiomi di Armstrong (Definizione)
gli _assiomi di Armstrong_ sono un insieme di [[Regole di inferenza]] per la [[Schemi relazionali - Dipendenze funzionali derivate|derivazione]] di [[Schemi relazionali - Dipendenze funzionali|Dipendenze funzionali]] _corretto_ e _completo_

- _Riflessività_: se $Y \subseteq X$ allora $X \rightarrow Y$
- _Arricchimento_: se $X \rightarrow Y$ e $W \subseteq T$ allora $XW \rightarrow YW$
- _Transitività_: se $X \rightarrow Y$ e $Y \rightarrow Z$ allora $X \rightarrow Z$

##### Regole derivate
Dagli assiomi base si possono dimostrare le seguenti formule:
- _Identità_ $\{ \} \vdash X \rightarrow X$
- _Decomposizione_: $\{ X \rightarrow YZ \} \vdash X \rightarrow Y,X \rightarrow Z$
- _Unione_: $\{ X \rightarrow Y,X \rightarrow Z \} \vdash X \rightarrow YZ$
- _Indebolimento_: $\{ X \rightarrow Y \} \vdash XZ \rightarrow Y$

#### Teorema
Gli _assiomi di Armstrong_ sono __corretti__ e __completi__

###### _Dimostrazione_
	Supponiamo di avere un insieme di dipendenze funzionali $F$ su $T$, e una dipendenza $X \to Y$.
Correttezza. Si deve dimostrare che se F ` X → Y allora F |= X → Y. Si procede
per induzione sulla lunghezza della derivazione. Sia f1, . . . , fm la derivazione
di X → Y da F, e supponiamo che il teorema valga per tutte le derivazioni piu`
corte. La dipendenza fm = X → Y e un elemento di ` F, oppure e stata derivata `
usando un assioma di Armstrong. Nel primo caso e implicata logicamente in `
maniera banale. Supponiamo che fm sia stata inferita con la regola riflessiva,
allora Y ⊆ X. Quindi, fm e implicata logicamente in maniera banale. `
Supponiamo che fm sia stata ottenuta da fi usando la regola di arricchimento,
allora fi ha la forma X
0 → Y
0
, con X
0
e Y
0
tali che X = X
0Z e Y = Y
0Z per qualche
Z. Per l’ipotesi induttiva F |= fi
. Siano t e t
0 due ennuple con t[X
0Z] = t
0
[X
0Z].
Allora t[X
0
] = t
0
[X
0
], quindi, per fi
, t[Y
0
] = t
0
[Y
0
], per cui t[Y
0Z] = t
0
[Y
0Z]. Quindi
fm e implicata logicamente da ` F.
Infine, supponiamo che fm sia stata ottenuta da fi = X → W e fj = W → Y, per
qualche W, usando la regola transitiva. Per l’ipotesi induttiva F |= fi e F |= fj
.
Siano t e t
0 due ennuple con t[X] = t
0
[X]; per fi
, t[W] = t
0
[W] e quindi, per fj
,
t[Y] = t
0
[Y]. Dunque, X → Y e implicata logicamente da ` F.
Completezza. Si deve dimostrare che se F |= X → Y, allora F ` X → Y.
Si consideri una relazione r su T di due ennuple costruita come segue: r = {t, t0
}
con t[X
+] = t
0
[X
+] e t[A] 6= t
0
[A] per ogni A ∈ T − X
+; r soddisfa F. Infatti, sia
V → W una dipendenza di F. Se V 6⊆ X
+, allora t[V] 6= t
0
[V], ed r soddisfa
ovviamente la dipendenza. Se invece V ⊆ X
+, si ha che F ` X → V e poiche´
V → W, per transitivita,` F ` X → W, da cui W ⊆ X
+ e quindi t[W] = t
0
[W].
Pertanto V → W e soddisfatta in ` r.
Mostriamo ora la tesi, cioe` F |= X → Y ⇒ F ` X → Y. Da F |= X → Y segue che r
soddisfa X → Y. Poiche´ X ⊆ X
+, e t[X
+] = t
0
[X
+], segue che t[Y] = t
0
[Y] per cui
Y ⊆ X
+ e F ` X → Y per il Teorema 5.2. 