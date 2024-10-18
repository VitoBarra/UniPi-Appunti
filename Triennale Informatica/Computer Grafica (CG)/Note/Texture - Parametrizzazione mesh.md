---
Course: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Texture Mapping]]"
SubTopic:
---

# Texture - Parametrizzazione mesh
---
per __parametrizzazione di una mesh__ si intende la pratica di definire una [[Funzioni|funzione]] $g$ _[[Applicazioni tra insiemi#Iniettiva|iniettiva]]_ che mappa  una [[Mesh Poligonali|mesh]] $S$ ad una dominio di una [[Texture|texture]] $\Omega$, Questo ci permette di applicare facilmente le [[Texture|Texture]]. basta iniettiva siccome la mesh non deve necessariamente usare tutta la texture.
In pratica si vuole trasformare la mesh in una [[Superfici parametriche|superfice parametrica]].


si trasforma in [[Superfici parametriche|superfici parametriche]] trovare questo mapping è triviale siccome vale che
_sia_ $f:[0,1]^2\to\mathbb{R}^3$ una [[Superfici parametriche|superfice parametrica]]
_allora_ il suo mapping dal dominio di una texture alla superfice è $$g(x,y,z)=f^{-1}(x,y,z)$$


la funzione di __parametrizzazione di una mesh__ $g$ esiste sempre in generale.
l'esistenza di $g$ non ne garantisce pero l'usabilità pratica siccome potrebbe essere non _[[Continuità di una funzione|continua]]_ e questi punti di discontinuità sono chiamate __seams__  (cuciture).

Nel caso peggiore possiamo mappare ogni triangolo della [[Mesh Poligonali|mesh]] in un triangolo in texture space in modo che non ci siano overlap. In questo mode ogni bordo di un triangolo è un __seams__.
![[Pasted image 20240305171421.png]]
la continuità è importane siccome il [[Texture Filtering|texture filtering]]  funziona correttamente sotto l assunzione che parti vicine della superfice mappano a parti vicine della [[Texture|texture]].

una funzione di __parametrizzazione di una mesh__ $g$ __CONTINUA__ non esiste in generale e se esiste non è necessariamente unica, quindi c è bisogno di definire un modo di scegliere la migliore. Questo non è possibile siccome non esiste "la migliore" in generale ma dipende dalla metrica scelta

un modo per capire se esiste una funzione $g$ continua è controllare se la mesh puo essere appiattita su un piano in quel caso allora $g$ esiste continua. Solitamente basta che la mesh abbia un __[[Mesh Poligonali#Classificazione mesh|bordo]]__, ad esempio un emisfero puo essere appiattito mentre una sfera no.
l Appiattimento pero puo introdurre delle deformazioni, in questo modo puo succedere che triangoli della stessa aria mappino in aree diverse in texture space. 
![[Pasted image 20240305171446.png]]Questo pero non è un caso comune, piu comunemente si utilizzano mesh dove la funzione $g$ non esiste continua e si aggiungono delle __seams__ 
![[Pasted image 20240305171509.png]]

#### Qualita della parametrizzazione
la qualità di una parametrizzazione $g$ è una caratteristica della parametrizzazione stessa ed è misurata in quanta __distorsione__ introduce. la __distorsione__ e di quanto  la superfice deve essere stretchata per essere appiattita sul piano. La distorsione puo essere misurata in due modi, Preservazioni del area e preservazione degli angoli
_sia_
- $S$ una [[Mesh Poligonali|mesh]]
- $p$ un punto su $S$
- $\Omega$ il dominio di una [[Texture|texture]] 
- $g:S \to \Omega$
- $q$ un quadrato di aria infinitesimale  centrato in $p$ 
_allora_ abbiamo tre tipi di mapping $g(q)$
1.  __Equiareal__: $q$ viene mappato in un quadrato con stessa area e diversi [[Angoli|angoli]]
2.  __Conforme o angle preserving__: $q$ viene mappato in un quadrato diversa area e stessi [[Angoli|angoli]]
3.  __Isomerico__: $q$ viene mappato in un quadrato con stessa area e stessi angoli e implica anche __equiareal__ e __conforme__

le parametrizzazioni isometriche esistono per tutte quelle mesh che possono essere fatte a partire da un pezzo di carta quindi senza stretch. Queste sono dette __Developable__.


Limitare la distorsione è importante siccome una __parametrizzazione__ con molta distorsione porta a mappare parti di superfici grandi in pochi [[Texture|texel]]
![[Pasted image 20240305171528.png]]
per ridurre la quantità di distorsione è si possono aggiungere delle __seams__, che rendono la superfice quasi __Developable__ in modo da aggiungere poca distorsione
![[Pasted image 20240305171536.png]]
ma questo da il problema della [[Continuità di una funzione|discontinuita]]. bisogna trovare il giusto compromesso