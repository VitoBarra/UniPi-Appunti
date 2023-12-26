---
type: nota
course: Interazione Uomo Macchina
topic: 
tags: IUM
---

Prev: [[Interazione Uomo Macchina (IUM)]]

# Front-End Design Wireframing
---
i _Wireframe_ sono _Progetti_ che aiutano la comunicazione tra Designer e programmatori riguardo la struttura del interfaccia del website o del app che stanno sviluppando.

senza strumenti come i _Wireframe_  la comunicazione sarebbe difficile e ogni persona potrebbe semplicemente fare qualsiasi cosa che creda essere la migliore. In pratica costruendo qualcosa completamente diverso da ciò che è stato descritto dai designer 

i Wireframe solitamente sono fatti anche su carta e
Sono disegni basilari con peche informazioni aggiunte che _mostrano_ la struttura e il layout del sito o app che si vuole sviluppare
![[Pasted image 20230611023453.png]]

![[Pasted image 20230611023718.png]]

i Wirefrase sono categorizzati per quantità di dettagli
infatti abbiamo i 
_Low-Fidelity Wireframes_: semplici disegni che si concertano sul mostrare la struttura e il layout del interfaccia
_High-fidelity Wireframe_: una rappresentazione più dettagliata del interfaccia con una tipografia di base, icone e dettagli di documentazione 
![[Pasted image 20230611023932.png]]
questi sono senza colori  o altri dettagli grafici. Si concentrano solo sulla struttura l aspetto grafico sono analizzati nel [[Prototipi e Mockup|Mocup]]


per capire come struttura un Wireframe si da attenzione al _contesto_ per cui si sta progettando. esempi di contesti diversi sono ad esempio due utenti che guardano il sito da device mobile o da desktop avranno un eserienza e un comportamento diverso. in piu altri fattori sono la demografica, la cultura, le capacita ecc.
infatti per un buon UX design è importante condurre prima uno studio di _ricerca sugli utente e testing_. 

un concetto importante è l
_Adaptability_: l adattabilità di un interfaccia in UX design si riferisce al abilita del design di sistemarsi e rispondere a bisogni, contesti, abilita e preferenze diverse  per ogni utente.
copre i concetti di 
- Design responsivo
- Accessibilità

#### Responsive Design
il _Design Responsivo_ è un modo di fare un design unico che riesca ad adattarsi a tutti i dispositivi. 
la necessita di creare un design con questa caratteristica nasce per via del esplosione di tipi di dispositivi con grandezze di schermo diverse.
il _Design Responsivo_ da al utente un interfaccia _utilizzabile e coerente_ a prescindere dal device in uso per l accesso al sito.
![[Pasted image 20230611024951.png]]
é utile anche dal punto di vista del business siccome invece di gestire versioni multiple se ne gestisce una che si _adatta_.

##### Tecniche per il design responsivo
Delle tecniche per assicurare il _design Responsivo_ sono

_griglia flessibile_:  una griglia flessibile permette agli elementi di aggiustarsi a seconda della dimensione dello schermo. l implementazione dipende dal framework che si sta usando
![[Pasted image 20230611115436.png]]
_Immagini Flessibili_: fare in modo che le immagini scalino con la dimensione dello schermo
![[Pasted image 20230611115427.png]]
_Media Querues & breackpoint_: applica stili diversi a seconda della necessita che si presentano sul tipo di dispositivo
![[Pasted image 20230611115417.png]]

una filosofia spesso applicata per fare _responsive design_ è sviluppare prima per i di dispositivi mobile in modo che la pagina sia ottimizzata per quella categoria di device che solitamente ha meno feature per via dello schermo piccolo e ha bisogno di più ottimizzazioni per la connettività lenta. questo permette anche di fare _progress advancement_  si parte da una versione con funzionalità minimali più adattate ai dispositivi mobile e poi si espandono nella versione desktop. Fare l opposto significa fare _graceful degradation_ ma questo puo essere più difficile.

altre _best Practis_ sono
- _mantenere l interfaccia semplice_: evitare di usare layout complessi
- _priorità al contenuto_: il contenuto deve essere l elemento a cui si da più importanza e deve essere leggibile su tutti i dispositivi
- _Design for touch_: assicurarsi che bottoni e link siano  abbastanza grandi per essere toccati
- _Ottimizzare i tempi di caricamento_: grandi i immagini o elementi pesanti possono allungare i tempi di caricamento. ottimizzare il caricamento di queste risorse migliora la UX.
- _Test_: fare spesso molti test su la più vasta varietà di dispositivi possibili.

#### Adaptive design
l _adaptive design_ è un modo per rendere l interfaccia automaticamente adattabile al tipo di dispositivo o utente
nel _adaptive design_ si creano più layout uno per ogni tipo di device.
è più costoso rispetto al _responsive design_ ma avvolte è una strategia migliore. ad esempio non bisogna fare retrofitting per la versione desktop.

Un altro vantaggio e che puo essere adattivo non solo al _device_ nello specifico ma anche al tipo di _utente_.
![[Pasted image 20230611124328.png]]

adattare l interfaccia _al utente_ permette anche una _UX adattiva_  alcune modi passano per l utilizzo di dati del utente come informazioni GPS, _colaborative filtering_ o analitica sulla tipologia di utente 

si definisce _colaborative filtering_ situazioni in cui 
- se ad utente X è piacuto contenuto A e B
- e utente Y piace contenuto A
- allora utente Y potrebbe essere interessato a B
essenzialmente è un modo per mettere in relazione utenti simili
es. consigliati di amazon
![[Pasted image 20230611125200.png]]
un altro modo è il _Content-base filtering_ ovvero si consiglia al utente del contenuto simile a quello a cui è interessato  

![[Pasted image 20230611125012.png]]

#### Accessibilità
l _accessibilità_ in _UX design_ è importante perché assicura che tutti possono usare il sito e si servizi che si stanno fornendo. l accessibilità deve essere pensata per aiutare tutti gli utenti che potrebbero avere vari _problemi_ al momento del utilizzo del interfaccia ad esempio
- _Visivi_: daltonismo
- _Motorie_: persone su sedie a rotelle
- _Auditori_: sordi e persone con difficolta a sentire
- _Epilessia_: in particolare quella fotosensibile
- _di apprendimento o cognitive_: persone con dislessia

altre barrire nel utilizzo possono essere date dal contesto momentaneo e sono di due tipi
- _accidentali_: cose che capitano come un utente ha dormito poco
- _ambientali_: l utente è in posti dove non riesce ad usare bene l interfaccia. es in metro 


##### Standard di accessibilità: WCAG
le _Web Content accesibilit gudeline_ (WCAG) sono delle guide linea che danno un framework per creare prodotti _accessibili_. 

alcuni esempi di _Best Practis_ di accessibilità:

- _Alternative testuali per contenuti non testuali_ : immagini, icone, grafici. 
- _Didascalie e altre alternative per i contenuti multimediali_: ad esempio, sottotitoli nei video. 
- _Possibilità di presentare i contenuti in modi diversi_ : fornire diverse opzioni di layout, possibilità di ingrandimento, lettura ad alta voce, diverse combinazioni di colori 
- _Contenuti più facili da vedere e ascoltare_:  dimensioni del font, colore di sfondo 
- _Gli utenti devono poter utilizzare modalità di input diverse oltre alla tastiera_:  comandi vocali o gestuali 
- _Gli utenti devono poter navigare facilmente_: trovare contenuti e capire dove si trovano (avere un'[[Information Architecture|architettura delle informazioni]] chiara e organizzare bene i contenuti).



#### Conclusioni

![[Pasted image 20230611131402.png]]

#### User flows
gli user flow servono a descrivere le possibili azioni che l utente puo fare sul interfaccia. questa è una cosa che i _Wireframe_ essendo statici non possono catturare.

##### Flowchart
un modo per rapresentar il un userflow è usare un flowchart.
si parte dalle [[User personas|personsa]] , [[IUM - Scenario|scenari]] e si descrive il viaggio del utente sul interfaccia.
![[Pasted image 20230611161016.png]]
bisogna pensare ai possibili punti di concontatto tra l utente e il sistema per poter costruire questo flowchart

##### Wireflow
come i flow chart ma invece di descrizioni astratte si usano i _wireframe_;
![[Pasted image 20230611161433.png]]
solitamente questi descrivono meglio l interazione utente-sistema
![[Pasted image 20230611161557.png]]