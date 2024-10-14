---
Subject: Interazione Uomo Macchina
topic: nota
tags: IUM
---

Prev: [[Interazione Uomo Macchina (IUM)]]

# User experience per IOT
---
## The internet of Things
l _Internet of things_ (Iot) è un sistema di dispositivi computazionali, meccanici, digitali o oggetti, animali e persone che hanno un _Identificati univoco_ (UID) e hanno l _abilita_ di trasferire dati sulla [[Tipi di rete|rete]] senza l interazione umano-umano o umano-macchina.

### Industria 4.0
per _industra 4.0_ si intende l _organizzazione dei processi produttivi_  basata su dispositivi e tecnologie capaci di comunicare autonomamente tra di loro per tutta la _value chain_ (tutta la catena produttiva dalle materie prime al produtto): questo è un modello di fabbriche _intelligenti_ dove i computer monitorano i _processi finisci_ creando una copia digitale del mondo fisico e fanno decisione decentralizzate basandosi su meccanismi che si auto organizzano.
![[Pasted image 20230614183148.png]]

un grande problema del industria 4.0 é la quantità di dati che devono essere processati.
![[Pasted image 20230614183211.png]]
nella storia la complessità e la quantità di dati è cresciuta esponenzialmente ad ogni rivoluzione industriale.
i dati sono cosi tanti per via della alla necessita di un _digital Twin_ della fabbrica
questo è una _replica digitale_ del mondo fisico e mondo fisico e digitale hanno bisogno di essere sempre sincronizzati tra di loro.


![[Pasted image 20230614184319.png]]

### UX per IOT
Rispetto al normale UX design  per il software il _design per  IOT_ è estremamente più complesso. questo ha varie ragioni
- lo stato delle tecnologia
- una comprensione ancora inaccurata della value proposition del Iot
- ci sono più cose da tenere in considerazione e farlo in modo indipendente puo portare ad una _user exeperince_ incoerente

infatti fare un buon design per la UX  richiede un Approccio olistico ovvero vanno considerate contemporaneamente più aspetti.
es industria 4.0
![[Pasted image 20230614184255.png]]

in piu le differenze  tra software UX e IOT UX in generale sono

1. la natura dei _device specializzati_ del IOT
	essendo gli oggetti del IOT specializzati per fare poche cose  e sono ottimizzati per fare quelle cose specifiche. il che vuol dire che la forma fisica del oggetto deve essere progetata e ingegnerizzata.

	in più l UI è di tipo molto diverso. varia a seconda del oggetti e puo andare da uno _schermo_ a un _bottone_ o a _controllo fisici_ o interazioni diverse come audio, gesture e cosi via

	un altro problema e che il design degli oggetti IOT non si puo poggiare su guide linea che invece ci sono per i siti web e per le app mobile.

1. l abilita di connettere _mondo digitale_ e _Mondo reale_
	gli  prodotti sono nel mondo reale e questi ci permette di avere molti più dati di tipologia diversa, questi vanno presi in considerazione e usati al meglio.

	le azioni che gli _oggetti IOT_ compileranno nel mondo fisico sono spesso non reversibili cosa che nel mondo software solitamente lo è
	![[Pasted image 20230614192601.png]]

	 va anche considerato il contesto di utilizzo
	 - gli oggetti utilizzati fuori casa devono essere più resistente ai danni
	 - gli oggetti da usare in macchina non devono distrarre troppo il guidatore
	 - ecc
	 tutte le soluzioni troppo _Tecno centriche_ che non prendono in considerazione queste problematiche falliranno 

1. distribuzione su piu device
 
	Molti prodotti IOT sono in realtà un sistema di _più dispositivi_ e _Servizi_ questo crea molte problematiche. Dispositivi diversi hanno capacita diverse e interazioni diverse questo porta dal designer il compito di decidere come _distribuire le funzionalità_ sui vari device.

	il Design del UI deve essere fatto considerando _tutto il sistema_ non solo il singolo device, questi permette di creare una UX _coerente_. questo riguarda anche i _servizi_ e dove vengono processati i dati 
	
	es. interfaccia simile tra oggetto fisico e app di controllo
	![[Pasted image 20230614193405.png]]

	in pratica il compito di design e ingegneri e creare un _ambiente unificato_  per l intero sistema IOT 

	un altro problematica e la gestione di possibili azioni che rompono la connessione tra _interazione_ e  _conseguenza visibile_
	se lo fanno _spazialmente_ allora abbiamo un _controllo remoto_
	se lo fanno _temporalmente_ allora abbiamo un _automazione_

4. design per il Network
	 ci sono dei device che prima o poi saranno sconnessi e questo va gestito. questo è un problema che non abbiamo ne per il nomali software ne per i nomali oggetti fisici. Ma i problemi di connettività fanno parte di come funziona la rete e questo puo influire sulla UX

![[Pasted image 20230614194432.png]]
![[Pasted image 20230614194443.png]]
