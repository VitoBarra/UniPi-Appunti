---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# DNA Struttura e funzionalità
---
il **DNA** è una [[Molecole|molecola]] che immagazzina le **informazioni genetiche** necessarie per la **sintesi proteica** e la **regolazione dell’espressione genica**. 

Il **DNA** è composto **due filamenti** intrecciati ad **elica**.
ogni **filamento** è una catena dei **[[Nucleotidi|Nucleotidi]]** che quindi formano una **backbone zucchero-fosfato** che è **idrofila** e interagisce bene con l’acqua grazie ai gruppi polari che possono formare legami a idrogeno e le basi azotate che invece, sono **idrofobiche** e tendono a raggrupparsi per evitare il contatto con l’acqua, conferendo alla catena proprietà **non polari**.
![[IMG - BSB Dna con basi esplicitate.png]]  
La catena di [[Nucleotidi|Nucleotidi]] è intrinsecamente **direzionale**: l’estremità **5’** porta in genere un **gruppo fosfato libero**, mentre l’estremità **3’** presenta un **gruppo –OH**. L’estensione della catena avviene sempre in direzione **5’ → 3’** perché il nuovo nucleotide può formare il legame fosfodiesterico solo attraverso il suo gruppo fosfato e l’ossidrile **–OH** presente al **3’** del nucleotide precedente.  

Le designazioni **5’** e **3’** indicano la posizione degli atomi di carbonio sullo scheletro del desossiribosio o ribosio, a cui sono legati rispettivamente il fosfato (C5) e l’ossidrile reattivo (C3).
![[IMG - direzione della catena.png]]
I due filamenti, cioè le due catene di [[Nucleotidi|Nucleotidi]], si associano in modo **complementare** tramite **legami a idrogeno** tra basi azotate: l’**adenina** si appaia con la **timina**, mentre la **guanina** si appaia con la **citosina**. Questo processo, definito anche **ibridazione**, garantisce la stabilità strutturale della molecola e la possibilità di una **replicazione accurata**, poiché ogni filamento contiene l’informazione necessaria a ricostruire l’altro, rendendoli di fatto **ridondanti**.

. I due filamenti scorrono in orientamenti opposti, risultando **antiparalleli** ($5' \to 3'$ e $3' \to 5'$). 
![[IMG - BSB DNA proprieta anti-paralela e complementarieta.png]]
La complementarietà implica che la distanza tra le coppie di basi sia **costante**
![[IMG - DNA struttura secondaria.png]]  
e in 3D questo contribuisce alla formazione della **doppia elica** di cui si conoscono le dimensioni 
![[IMG - BSB DNA struttura terziaria.png]]

La **duplicazione del DNA** avviene principalmente per la conservazione dell’**informazione genetica** attraverso le **generazioni cellulari**,  e per poter permettere alla cellula di duplicarsi mantenendo i propri **tratti**.

come questa divisione avviene era inizialmente sconosciuto e le ipotesi erano
- **distruttiva**: dove parti replicate sono inserite assieme a le parti originali
- **semi-conservativa**: dove un filamento resta quello originale mentre l altor è quello duplicato
- **conservativa**: dove si mantiene la coppia di filamenti originale e se ne genera una coppia nuova 
oggi si sa che il meccanismo è **semi-conservativo**
![[IMG - DNA tipi di replicazione.png]]

il processo di duplicazione del DNA avviene grazie alla **DNA polimerasi** una proteina in questo caso un **enzima** che catalizza l'aggiunta alla catena di DNA un **nucleotide** e è in piu aiutato dalla **pirofosfatasi** che converte il **pirofosfato** in fosfato libero che è poi usato dalla dal processo di duplicazone.
![[IMG - polimerizazione del DNA.png]]
la **DNA polimerasi** è un enzima a forma di mano destra semi chiusa che interagisce con un filamento di DNA scorrendoci sopra mentre sintetizza il nuovo filamento e mantiene nella posizione corretta il sito attivo, ovvero dove va inserito il nuovo nucleotide e 
![[IMG - DNA polimerasi.png]]
 i substrati necessari per la **sintesi del DNA** sono:
 1. un 2'-deossinucleoside trifosfato (immagine di sinistra) chiamati a seconda della base **dGTP, dATP, dTTP, dCTP**, d: deossi, \*:nomebase, TP:trifosfato  
 2. un primer ovvero una piccola sezione di poche basi che si puo **ibridare** co del DNA da duplicare (immagine di destra). la sintesi parte con la DNA polimerasi a partire dal estremita 3' del primer.  dsDNA: double strand DNA,  ssDNA: single strand DNA ![[IMG - substrai per sintesi DNA.png]]

la sintesi del DNA avviene in due direzioni, la direzione canonica chiamata **direzione di replicazione** e la direzione opposta che replica il secondo filamento. cosi da avere in fondo da una copia del DNA due copie.
![[IMG - loggistica della duplicazone del DNA.png]]
la molecola del DNA è molto stabile e quindi per aprire l elica richiede energia, in laboratorio questo si ottiene alzando la temperatura a 90 gradi e questo processo è detto **denaturalizzazione**. essendo pero una molecola molto stabile raffreddando il DNA tonerà ad essere unito


puo capitare che durante la replicazione ci siano degli errori, l’incorporazione di un nucleotide non corretto provoca un rallentamento della sintesi, poiché il gruppo 3′-OH non assume la disposizione geometrica ottimale per l’ulteriore allungamento. La presenza di un’estremità 3′ non appaiata induce la transizione degli ultimi 3–4 nucleotidi dal **primer** in una configurazione a **single strended**, condizione che favorisce l’ingresso nel sito **esonucleasico**. In questa sede il nucleotide non complementare, insieme ad un nucleotide in più, viene rimosso.
L’escissione consente di ristabilire una giunzione **primer-stampo** correttamente appaiata, permettendo la ripresa della sintesi.
![[IMG - Proff-reading durerante la replicazione del DNA.png]]
l’inserzione errata si verifica con una frequenza di circa $10^{-5}$, mentre l’attività di proofreading riduce l’errore a circa $10^{-7}$. I meccanismi di riparazione successivi conducono a un tasso di mutazione finale vicino a $10^{-10}$ per genoma.

Una **mutazione** è una modificazione permanente della sequenza del **DNA**, con estensione variabile da un singolo nucleotide a porzioni genomiche ampie. Nel genoma umano se ne accumulano in media tra 60 e 100 a ogni generazione e possono assumere forme distinte, tra cui mutazioni puntiformi, inserzioni, delezioni e riarrangiamenti cromosomici. 

La distinzione concettuale tra **mutazioni** e **polimorfismi** si fonda sulla frequenza nella popolazione: una mutazione presenta una frequenza $<1\%$ ed è associata con potenziali effetti patologici, mentre un polimorfismo $>1\%$ ed è generalmente neutro o tollerato.
In questo quadro rientrano gli SNPs, variazioni di singoli nucleotidi diffuse nel genoma.
![[IMG - mutazioni del DNA.png]]

graficamente tutto il processo è 
![[BSB - duplicazione del DNA.png]]


il DNA è detto **codice genetico** perche contiene **unità funzionali** chiamate **geni** ovvero sequenze di nucleotidi che **codificano** l’informazione necessaria per la produzione di proteine.
![[BSB - DNA che contiene geni per codificare proteine.png]]  


Il DNA per poter essere contenuto nel nucleo di una cellula deve essere compattato e ciò avviene grazie a proteine specializata. DNA+proteine è chiamata cromatina.

La regolazione dell’espressione genica dipende anche dal grado di compattazione del DNA, mediato infatti una cromatina più compatta limita l’accesso ai geni, riducendo l’espressione proteica.  

![[BSB - compattazione del DNA.png]]  


