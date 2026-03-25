---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Medicine network
---
La **Medicine network** descrive l'applicazione delle [[Protein-Protein interaction network (PPIN)|protein-protein interaction networks]] allo studio di malattie e farmaci.
L'**assunzione centrale** e che una patologia non corrisponda a geni dispersi casualmente nell'[[Interactomics|interactoma]], ma a una regione topologicamente e funzionalmente correlata.

Si definiscono:
- **Disease [[Network Science - Community o moduli|module]]**: insieme delle proteine associate a una malattia nell'[[Interactomics|interactoma]].
- **Drug [[Network Science - Community o moduli|module]]**: insieme delle proteine bersaglio di un farmaco.

L'**ipotesi di base** e che i geni associati alla stessa malattia tendano a localizzarsi nello stesso intorno topologico della rete. La **conseguenza funzionale** e che i nodi del **disease module** mostrano spesso co-espressione, condivisione di pathway e alterazioni coordinate.

La nozione di modulo puo essere distinta in tre livelli:
- **Modulo topologico**: sottoinsieme di nodi con densita locale elevata di interazioni.
- **Modulo funzionale**: intorno della rete arricchito in nodi con funzione biologica correlata.
- **Disease [[Network Science - Community o moduli|module]]**: insieme di nodi la cui perturbazione e associata a uno specifico fenotipo patologico.

L'assunzione della network medicine e che questi tre livelli si sovrappongano almeno in parte, per cui una malattia puo essere interpretata come alterazione di un modulo funzionale.
![[IMG - Medicine network - module and disease module.png]]

L'identificazione di geni candidati associati a una malattia puo seguire due strategie principali:
- metodi basati su [[Network Science - Community o moduli|moduli]], che cercano cluster o partizioni della rete compatibili con una funzione patologica;
- metodi di [[Network Science - Network propagation|diffusione]], in cui da un insieme iniziale di proteine note associate alla malattia si propaga un segnale sulla rete per assegnare a ogni nodo uno score di associazione.
![[IMG - Medicine network - predizione di associzione gene-malattia.png]]

Alcune proprieta si possono spiegare tramite misure di **[[Network Science - Community o moduli|network proximity]]**, in particolare l'**[[Network Science - Community o moduli|average shortest path distance]]** e, piu spesso, la **[[Network Science - Community o moduli|closest-path distance]]**. In questo contesto servono a stimare quanto il modulo di un farmaco sia vicino al modulo patologico nell'[[Interactomics|interactoma]].

La **[[Network Science - Community o moduli|separation]]** viene invece usata soprattutto per confrontare due **disease module**. Se $s_{AB}<0$, la distanza tra i due moduli di malattia e minore della loro distanza media interna, quindi le malattie risultano topologicamente vicine o parzialmente sovrapposte; se $s_{AB}>0$, i moduli risultano separati. In questa interpretazione la separation segnala possibile condivisione di meccanismi molecolari e costituisce un forte predittore delle relazioni di comorbidita osservate a livello epidemiologico.
![[IMG - Visualizazione di separation.png]]

Nelle applicazioni ai farmaci si usa spesso la **[[Network Science - Community o moduli|closest-path distance]]** tra il **drug module** e il **disease module**, perche misura per ciascun gene target $T$ la distanza dal gene di malattia piu vicino e risulta piu robusta della media completa dei cammini minimi. Tuttavia un insieme di target ricco di [[Network Science|hub]] puo apparire artificialmente vicino al **disease module**, per cui la distanza osservata deve essere normalizzata rispetto a un **modello nullo** che conserva il grado dei nodi.

Per questo si introduce uno **z-score di prossimita drug-disease**: $$z_c=\frac{d_c^{obs}-\mu_{rand}}{\sigma_{rand}}$$ dove $d_c^{obs}$ e la **closest-path distance** osservata tra l'insieme dei target del farmaco $T$ e il **disease module** $S$, mentre $\mu_{rand}$ e $\sigma_{rand}$ sono media e deviazione standard ottenute da molti insiemi casuali di target con la stessa distribuzione dei gradi di $T$. In questo modo si verifica se la vicinanza osservata e specifica oppure se potrebbe dipendere soltanto dalla presenza di nodi altamente connessi. Un valore di $z_c$ basso, in particolare negativo, indica che il farmaco e piu vicino al **disease module** di quanto ci si aspetterebbe per caso.
![[IMG - drug-disese proximity.png]]

L'AUC puo essere usata per confrontare il potere discriminante di diverse misure di prossimita. In generale la **closest-path distance** $d_c$ risulta piu robusta della media completa dei cammini minimi $d_{avg}$, mentre altre misure possono enfatizzare aspetti diversi della relazione topologica tra moduli.

### Drug Repurposing
Il **Drug Repurposing** consiste nell'identificazione di nuovi **usi terapeutici** per **farmaci** gia noti e approvati dagli enti regolatori.

Per fare ciò si sfruttando la loro posizione topologica rispetto al **disease module**I.  Il work flow generare:
- L'**input** dell'analisi e costituito da una **PPI network curata**, da un insieme $S$ di geni di malattia e da un insieme $T$ di target  del farmaco. 
- Il workflow essenziale consiste nel calcolare la **[[Network Science - Community o moduli|closest-path distance]]** osservata tra $T$ e $S$, 
- costruire un controllo casuale con insiemi di target aventi la stessa distribuzione dei gradi di $T$
- Calcolare il relativo $z$-score e infine valutare se la vicinanza osservata sia piu forte di quanto atteso per caso.
- In questo schema un farmaco con $z_c$ sufficientemente basso, ad esempio $z_c<-2$, viene considerato un candidato di **repurposing topologicamente plausibile**

I metodi basati solo sui cammini minimi hanno pero un limite importante: considerano solo il **cammino minimo e ignorano tutti i percorsi alternativi**, per cui una **PPI network sparsa o rumorosa** puo alterare in modo rilevante la distanza osservata. Per questo si possono usare anche metodi di **propagazione o diffusione** sulla rete, che distribuiscono l'informazione dei nodi sorgente sull'intero [[Interactomics|interactoma]] invece di fermarsi al solo cammino minimo.

Un'impostazione classica e il **random walk with restart**, in cui un camminatore casuale si muove lungo la rete ma con probabilità $\alpha$ torna ai nodi sorgente.
Se $p_t$ e il vettore di [[Definizione di Probabilita|probabilita]] al passo $t$, la dinamica e $$p_{t+1}=(1-\alpha)Wp_t+\alpha p_0$$dove $W$ e la matrice di adiacenza normalizzata per colonna e $p_0$ rappresenta i nodi sorgente. Il processo converge a uno stato stazionario $p_{\infty}$ che descrive l'influenza globale delle sorgenti sulla rete: $$p_{\infty}=\alpha(I-(1-\alpha)W)^{-1}p_0$$ questa equazione è solitamente risolta analiticamente e $K=\alpha(I-(1-\alpha)W)^{-1}$ è chiamato **Diffuzion kernel** $K-{ij}$ quantifica la probabilita che una partenza alla posizione $i$ ti porto alla posizione $j$ 

In questa prospettiva non si misura soltanto una distanza minima, ma la diffusione complessiva del segnale. Si puo quindi propagare il set dei geni di malattia ottenendo un profilo $p_{\infty}^S$, propagare i target del farmaco ottenendo un profilo $p_{\infty}^T$ e confrontare i due profili per stimare quanto malattia e farmaco insistano sulle stesse regioni funzionali della rete.


