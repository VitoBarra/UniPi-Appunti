---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Meccanica molecolare
---
la **meccanica molecolare** considera le [[Molecole|molecole]] come un insieme di **masse atomiche collegate** da **forze attrattive**, modellate come **sfere connesse da molle**. Un insieme empirico di funzioni energetiche, noto come **force field** (FF), permette di simulare queste interazioni.
Un tipico FF include contributi per 
1. l’allungamento dei legami
2. flessione degli angoli
3. rotazione torsionale
4. le interazioni van der Waal
5. le interazioni elettrostatiche 
6. i legami a idrogeno. 
L’energia complessiva di un conformero, detta anche energia sterica della molecola, è la somma di tutti questi contributi. 
![[IMG - modello delle molecole a molle.png]]

Un legame chimico tra due atomi possiede una posizione di equilibrio naturale. Considerando il legame come una molla, si associa una penalità energetica a qualsiasi variazione della lunghezza del legame. L’energia di allungamento può essere approssimata tramite la legge di Hooke:$$E(L) = \sum k(L)(L - L_0)^2$$dove $k(L)$ è la costante di forza di allungamento e $L_0$ la posizione di equilibrio. Le costanti di forza per l’allungamento sono determinate sperimentalmente mediante spettroscopia vibrazionale, risultando accurate vicino alla geometria di equilibrio.

![[IMG - livelli di energia bond stretching.png]]

Un angolo di valenza formato da tre atomi ha anch’esso una posizione di equilibrio naturale. La variazione dell’angolo rispetto al valore di equilibrio comporta una penalità energetica, espressa tramite una legge simile alla Hooke:$$E(\Theta) = \sum k(\Theta)(\Theta - \Theta_0)^2$$dove $k(\Theta)$ è la costante di forza per la flessione e $\Theta_0$ l’angolo di equilibrio. Anche queste costanti sono solitamente determinate sperimentalmente.

L’energia associata a un angolo torsionale origina da interazioni steriche ed elettroniche tra atomi non legati direttamente. l energia minima richiesta per un rotazione completa attorno a un legame è detta **barriera energetica per la rotazione**. 
L’energia torsionale si esprime come: $$E_\Theta = \sum V_i \big[1 + \cos(n|\Theta| + \tau)\big]$$Tre diversi termini $V_i$ sono generalmente considerati per descrivere la barriera alla rotazione.
![[IMG - sfere di influenze per componente tornsionale.png]]

Le interazioni tra atomi non legati direttamente sono note come interazioni van der Waals. A breve distanza si manifesta repulsione dovuta all’interpenetrazione delle nuvole elettroniche, mentre a lunghe distanze è presente una debole attrazione di dispersione. Queste interazioni sono descritte dal potenziale di Lennard-Jones:$$V_{LJ} = 4 \varepsilon \Big[ \Big(\frac{\sigma}{r}\Big)^{12} - \Big(\frac{\sigma}{r}\Big)^6 \Big]$$dove $\varepsilon$ e $\sigma$ sono parametri specifici per ciascuna coppia di particelle.
![[IMG - interazioni van der waals.png]]

Le interazioni tra atomi o legami polari possono comportare attrazioni o repulsioni. Al primo livello di approssimazione, possono essere modellate assegnando cariche atomiche o utilizzando un dipolo di legame. L’energia elettrostatica tra cariche puntiformi è: $$E_{el}(R_{AB}) = \frac{Q_A Q_B}{\varepsilon R_{AB}}$$mentre tra dipoli di legame è:$$E_{el}(R_{AB}) = \frac{\mu_A \mu_B}{\varepsilon R_{AB}^3} (\cos \chi - 3 \cos \alpha_A \cos \alpha_B)$$dove $Q$ è la carica atomica, $R$ la distanza tra atomi, $\varepsilon$ la costante dielettrica e $\mu$ il momento di dipolo.

![[IMG - contribuzione bipolare eletrostatica.png]]

Un legame a idrogeno è un’interazione attrattiva tra un idrogeno covalentemente legato a un elemento elettronegativo e un secondo elemento elettronegativo. L’energia di un forte legame a idrogeno varia tra 12 e 21 kJ/mol, mentre un legame covalente possiede circa 418 kJ/mol. La sua energia può essere calcolata come:$$E_{HB} = \frac{332}{\varepsilon} \sum \Big( \frac{q_D q_A}{d_{DA}} + \frac{A_K}{d_{HA}^{12}} - \frac{B_K}{d_{HA}^{10}} \Big)$$dove $\varepsilon$ è la costante dielettrica, $q$ la carica atomica, $d$ le distanze e $A_K$, $B_K$ sono parametri specifici.

![[IMG - contribuzione per interazioni idrogeno.png]]


### Calcolo del force field (FF)
I calcoli mediante Force Field si basano sulle coordinate tridimensionali e permettono di determinare l'energia associata alla conformazione molecolare considerata. Un esempio di calcolo con il Force Field MM2 illustra come la geometria e le interazioni tra atomi contribuiscano alla stabilità della molecola.  
![[IMG - calcolo Force filed.png]]
Il concetto di “tipi di atomo” rappresenta uno degli elementi fondamentali nella meccanica molecolare. I tipi di atomo sono essenziali per la valutazione delle interazioni, poiché le proprietà chimiche e geometriche degli atomi influenzano le energie di legame, di angolo e torsionali. Essi possono essere definiti sulla base di: a) ibridazione, b) carica atomica e c) atomi legati. 
Ad esempio, nel Force Field Amber i tipi di ossigeno sono distinti in cinque categorie:  
- O: ossigeno del gruppo carbonilico  
- OW: ossigeno nell'acqua  
- OH: ossigeno nei gruppi idrossilici  
- OS: ossigeno in eteri ed esteri  
- O2: ossigeni dei gruppi carbossilici e fosfato  
Le interazioni tra atomi vengono calcolate in base ai tipi di atomo e non ai soli elementi chimici, permettendo una descrizione più accurata delle energie conformazionali e delle proprietà dinamiche delle molecole.  
![[IMG - esempio tipi di atomo.png]]
