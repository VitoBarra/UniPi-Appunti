---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# Ricerca conformazionale
---
La **ricerca conformazionale** studia come una [[Molecole|molecola]] possa cambiare geometria attraverso variazioni degli [[Meccanica molecolare|angoli torsionali]] dei legami. Lo studio delle [[Geometrica Molecolare|geometrie]] accessibili e delle [[Energia Molecolare e conformazioni|energie associate]] è definito **analisi conformazionale**.  
![[IMG - analisi Conformazionale componenti.png]]

Per una molecola con un solo legame rotabile, la superficie di potenziale conformazionale è rappresentata da una curva che descrive l’energia molecolare in funzione dell’angolo di torsione: i minimi della curva corrispondono alle **conformazioni** a bassa energia quindi a **conformeri** Nel caso di due legami rotabili, l’energia totale dipende da due angoli torsionali variabili, generando una superficie energetica bidimensionale.  
![[IMG - energia potenziale per 1 e 2 bond rotabili.png]]

La maggior parte delle molecole possiede però più di due torsioni variabili, quindi la superficie conformazionale non è visualizzabile direttamente perché definita in uno spazio con più di tre dimensioni. Essa può essere schematizzata tramite un parametro astratto $p$, privo di significato geometrico reale, che mostra:
- **minimi locali** (conformeri a bassa energia)  
- **barriere** (regioni ad alta energia)  
- **minimo globale** (conformazione di minima energia)  
Barriere superiori a 80 kJ/mol rendono l’interconversione impossibile a temperatura ambiente.  
![[IMG - energia ridotta da un parametro.png]]

### Algoritmi di ricerca conformazionale
Un metodo concettualmente semplice per esplorare la superficie conformazionale consiste nella scansione sistematica di tutte le geometrie possibili, ma per molecole con molti legami rotabili questo approccio diventa rapidamente impraticabile a causa della crescita combinatoria del numero di configurazioni. Inoltre, molte conformazioni generate risultano tra loro molto simili e ricadono nello stesso “pozzo” energetico: esse appartengono quindi alla stessa famiglia di **conformeri**, differendo solo per piccole variazioni geometriche attorno a uno stesso minimo locale.  

Per questo motivo, dopo una fase iniziale di **ricerca conformazionale**, è necessario uno step di minimizzazione, che fa collassare tutte le strutture appartenenti allo stesso pozzo verso il minimo locale corrispondente, eliminando ridondanze e producendo [[Energia Molecolare e conformazioni|energie]] confrontabili.  

Poiché non è possibile generare esplicitamente tutti i conformeri, si ricorre ad algoritmi che mirano a produrre conformazioni **tipicamente diverse**, cioè appartenenti a regioni energetiche distinte della superficie. Questo permette di identificare i principali minimi locali senza campionare inutilmente configurazioni ripetitive. Le strategie più comuni includono approcci deterministici come la **ricerca sistematica** e approcci stocastici come il **Monte Carlo**. Ogni conformero generato deve essere infine minimizzato per ottenere valori energetici significativi.
![[IMG - step della ricerca conformazionale.png]]

La **ricerca sistematica** (*systematic conformational search*) è un metodo deterministico che mira a esplorare in modo estensivo lo spazio conformazionale di una molecola.  
 - Nel caso di molecole **acicliche**, l’algoritmo ruota ciascun legame rotabile secondo incrementi angolari prefissati (tipicamente di circa 120°) e, per ogni configurazione generata, identifica i **minimi energetici** corrispondenti. Questo approccio consente generalmente di campionare in modo efficace tutte le conformazioni rilevanti per molecole di piccole dimensioni.  
- Per le molecole **cicliche**, una procedura analoga viene applicata introducendo deformazioni progressive dell’anello per ottenere differenti geometrie accessibili.  
Tuttavia, per molecole più grandi, il metodo diventa rapidamente impraticabile, poiché il numero di combinazioni torsionali cresce in maniera esponenziale. Per questo motivo, la ricerca sistematica è indicata soprattutto per molecole **piccole** e preferibilmente **non cicliche**.  


Nel metodo **Metropolis-Hastings Monte Carlo** l’esplorazione conformazionale avviene come campionamento statistico guidato dalla [[Distribuzione di Boltzmann|distribuzione di Boltzmann]]. A partire da una geometria iniziale, una perturbazione casuale genera una nuova configurazione con [[Energia Molecolare e conformazioni|energia]] $E_{new}$, confrontata con quella corrente $E_{old}$. Se $$\Delta E = E_{new}-E_{old}<0$$ la configurazione viene accettata. Se invece $\Delta E>0$ l’accettazione avviene con probabilità $$P=e^{-\Delta E/kT}$$ confrontata con un numero casuale $R$ ($0\le R\le1$). Se $P>R$ la struttura è accettata, altrimenti si mantiene quella precedente. Ripetendo questo processo si ottiene una sequenza di **conformazioni campionate**, concentrate nelle regioni a bassa energia ma con la possibilità di superare barriere e accedere a stati meno favorevoli, in modo tale che la frequenza con cui vengono visitati i diversi conformeri rappresenti la loro popolazione relativa all’equilibrio secondo la [[distribuzione di Boltzmann|distribuzione di Boltzmann]]. Le configurazioni accettate vengono poi selezionate e minimizzate per identificare i principali minimi locali.  
![[IMG - schema Metropolis-Hastings MC Algorithm per la ricerca conformazionale.png]]

La conformazione assunta da una molecola al momento del legame con un target biologico è detta **bioattiva**. Essa non coincide necessariamente con il minimo globale e può essere meno stabile, purché l’energia rilasciata dalle interazioni favorevoli compensi l’energia richiesta per assumere una conformazione più tesa. La differenza energetica tra la conformazione bioattiva e il minimo globale è generalmente inferiore a 13 kJ/mol.
