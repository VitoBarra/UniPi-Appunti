---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Planning Multi agente - Decision maker singolo
---
un caso del [[Planning Multi agente|Planning Multi agente]] è quello in cui esistono più agenti ma **un solo decision maker**, questo **sviluppa** i piani anche per tutti gli altri attori. Si assume la **benevolent agent assumption**, ovvero che gli altri agenti seguano sempre le istruzioni ricevute. Ci sono vari casi specifici del tipo con un **solo agente decision maker**:  
- **multieffector planning**: l’agente decisore possiede più effettori e deve gestire le interazioni positive e negative tra essi.  
- **multibody planning**: se gli effettori sono fisicamente separati in unità indipendenti, come una flotta di robot, il problema può essere trattato come single-agent finché le informazioni sensoriali possono essere aggregate centralmente o localmente, formando uno stato comune del mondo. La presenza di vincoli di comunicazione introduce problemi di **decentralized planning**, dove la fase di pianificazione resta centralizzata ma l’esecuzione diventa parzialmente decentrata, richiedendo azioni comunicative tra le unità.

La presenza di più attori richiede sincronizzazione delle azioni:  
- **simultaneamente** per azioni congiunte  
- **momenti diversi** se mutuamente esclusive  
- **in sequenza** quando una azione costituisce precondizione per un’altra  

La correttezza di un piano dipende dalla capacità degli attori di raggiungere l’obiettivo pianificato. La gestione della concorrenza tra azioni è cruciale: occorre considerare interferenze, risorse condivise, azioni mutualmente esclusive o cooperative. I modelli di azione concorrente si articolano principalmente in tre approcci:  
- **interleaved execution**: le azioni rispettano l’**ordine sequenziale del piano individuale**, generando combinazioni multiple per l’esecuzione simultanea.  
- **true concurrency**: lascia parzialmente ordinate le azioni, consentendo **esecuzione simultanea** senza un ordinamento completo.  
- **perfect synchronization**: assume un orologio globale e azioni eseguite in **lockstep**, ogni azione dura lo stesso tempo e tutti gli agenti agiscono simultaneamente.

Per formalizzare la dinamica in contesti multiactor, si estende il modello di transizione del singolo agente deterministico, $\text{RESULT}(s, a)$, al caso multiactor sostituendo l’azione singola $a$ con una **joint action** $\langle a_1, \dots, a_n \rangle$, dove $a_i$ è l’azione del $i$-esimo attore. Ciò comporta un aumento esponenziale del fattore di ramificazione, $b^n$, e rende necessario decouplare gli attori quando possibile, riducendo idealmente la complessità a crescita lineare in $n$. Se gli attori sono totalmente indipendenti, si risolvono $n$ problemi separati; se sono **loosely coupled**, si possono applicare metodi di decoupling simili a quelli utilizzati in [[Problemi di soddisfacibilita vincolata (CSP)|CSP]] come ad sempio i problemi tree like. un alternativa e ignorare le interazione e aggiustarle dopo.

Le **action schemas** possono essere arricchite con **concurrent action constraint** espandendo cosi il [[Planning - Planning Domain Definition Language (PDDL)|PDDL]], indicando quali azioni devono o non devono essere eseguite contemporaneamente. Alcune azioni producono l’effetto desiderato solo se eseguite simultaneamente, altre richiedono che nessun altro le esegua nello stesso istante. Formalmente, per un’azione $Hit(actor, Ball)$ si può definire:$$
\begin{align*}
\text{Action}(&Hit(actor, Ball), \\
&\text{CONCURRENT:} \forall b\ b \neq actor \Rightarrow \neg Hit(b, Ball), \\
&\text{PRECOND:} Approaching(Ball, loc) \land At(actor, loc),\\
&\text{EFFECT:} Returned(Ball))
\end{align*}
$$Per azioni cooperative, come trasportare un oggetto pesante da due agenti:  $$
\begin{align*}

\text{Action}(&Carry(actor, cooler, here, there), \\
&\text{CONCURRENT:} \exists b\ b \neq actor \land Carry(b, cooler, here, there), \\
&\text{PRECOND:} At(actor, here) \land At(cooler, here) \land Cooler(cooler), \\
&\text{EFFECT:} At(actor, there) \land At(cooler, there) \land \neg At(actor, here) \land \neg At(cooler, here))
\end{align*}
$$Con tali schemi, gli algoritmi di [[Planning|pianificazione single-agent]] possono essere adattati con modifiche minime.



### ### Cooperazione e coordinazione 

Nel contesto **multi agente reale**, ogni agente elabora il proprio piano individuale. Si assume che gli agenti condividano sia gli obiettivi sia la base di conoscenza. In tale configurazione, potrebbe sembrare che la situazione coincida con il caso **multibody**, in cui ogni agente calcola una soluzione congiunta ed esegue la propria parte. Tuttavia, l’idea di una “soluzione unica” è fuorviante: possono infatti esistere più piani corretti che conducono al raggiungimento dello stesso obiettivo.

Il problema principale risiede nella **coordinazione delle scelte**: se gli agenti selezionano piani differenti che si escludono a vicenda, l’obiettivo globale fallisce. Anche se entrambi conoscono l’insieme dei piani possibili, l’assenza di accordo impedisce la coerenza nell’esecuzione. Per garantire la coordinazione è quindi necessario introdurre **meccanismi di consenso** o vincoli esterni alla pianificazione autonoma dei singoli agenti.

Una possibile soluzione è l’adozione di una **convenzione**, ossia un vincolo condiviso nella selezione dei piani congiunti. La convenzione impone una regola di comportamento comune che permette agli agenti di scegliere coerentemente piani compatibili. Le convenzioni eliminano l’ambiguità nella scelta e garantiscono la prevedibilità reciproca, risultando particolarmente efficaci in ambienti ripetitivi o standardizzati. Quando tali convenzioni diventano pervasive e istituzionalizzate, assumono la forma di **social laws**, ovvero norme sociali che disciplinano il comportamento collettivo e assicurano la coordinazione sistemica.

In assenza di convenzioni, la coordinazione può essere raggiunta tramite **comunicazione**. Gli agenti possono scambiarsi informazioni per stabilire una conoscenza comune del piano da adottare. La comunicazione consente di ridurre l’incertezza sulla scelta del piano congiunto, rendendo esplicito il coordinamento. Tuttavia, la comunicazione non deve necessariamente essere verbale: può avvenire anche in modo implicito attraverso l’**esecuzione parziale di un piano** che renda evidente la scelta dell’agente. In tali casi, un agente può dedurre le intenzioni dell’altro osservandone le azioni iniziali.

Questa forma di coordinazione è nota come **plan recognition**, in cui un’azione o una breve sequenza di azioni da parte di un agente permette agli altri di identificare in modo univoco il piano collettivo in corso. Tale meccanismo è efficace quando le azioni sono sufficientemente distintive da non lasciare ambiguità interpretative e consente di ottenere un coordinamento implicito anche in assenza di comunicazione diretta.
