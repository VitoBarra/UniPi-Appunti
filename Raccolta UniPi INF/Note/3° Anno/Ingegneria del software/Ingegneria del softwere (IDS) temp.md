




### narrativa dei casi d uso 
Spiega con parole le funzionalità dei singoli casi d usi 

È fatto da 
- nome
- ID
- Breve Descrizione
- Attore primario
- Attore secondari
- Precondizione
- Sequenza degli eventi principali: sequenza di passi per arrivare alla post condizione  
- Post condizione:
- Sequenza alternativa degli eventi: casi in cui ci sono errori, o ci sono delle interruzioni dei generici problemi nel raggiungere la post condizione. Magari gli eventi meno probabili  
- 

[[Triple di Hoare]]

Le erediriata nel UML esiste si può applicare sia a attori che a componenti. Deve rispettare il [[principio di sostituzione di Liskov]]

Esistono anche le dipendenze ovvero il caso il caso d uso uno ha bisogno di usare un altra cosa d uso


Un caso d uso incluso non necessariamente ha un attore principale 

Si puo fare estensione di un caso d uso significa al volere si possono ottenere sia la post condizione della classe che stende che quella che si sta usando 

Nei passi vanno scritti le interazioni tra l attore e il sistema oltre ai passi che deve fare effettivamente il sistema 

Il sistema che si sta implementando non è un attore 

Ci sono attori esterni la semantica e che non va implementato nel sistema esempio un DB




2022-10-05:

Diagramma delle classi e diagrammi oggetti
LEZIONE SINTASSI

2022-10-10:
COn il diagramma delle classi si può auto enervare lo scheletro delle classi 

Reverse ingegnearing: passare dalla struttura della classi all diagramma delle classi fino a ritrovare i requsiti

BlueJ: tentativo di fare la auto generazione del codice dal diagramma delle classi (indicato come probabilmente impossibile) 



## Diagramma dellle attività:

Descrivo processo ovvero una sequenza di azioni 

Il diagramma è un grafo orientato

Le azioni sono atomiche.
La semantica è descritta dal token game 

IMMAGINE SINTASSI 


Nel nodo di divisione ha bisogno che il token vada almeno da una porta
-  se più condizioni sono vere il token prende una strada non deterministica 


I nodi Azzione hanno un UNICA entrata e un UNICA uscita questo per distingue i casi di merge o sincronizzazione 

Le azioni in UML sono modellate sul [[Interliving]] E NON su true concurrency 

Il nodo di fine attività fa finire TUTTE le attività quindi tutti i token spariscono 


Eventi esterni sia segnale 
	- verso l esterno :  
	 - dal esterno : questa azione puo sia far aspettare un token che generarlo  
	Eventi del tempo.
	- relativo 
	- Assoluto : puo sostituire lo stato iniziale 


Sottoazioni: 
	Sono azioni modellate come un diagramma delle attività e si possono richiamare 


Partizione: 
	Si definisce una seri di zone in cui si divide la responsabilità tra ottoni 

## Diagramma di macchine a stati 
descrivono le evoluzioni degli stati 

È un grado in cui i nodi sono stati e gli archi sono transizioni da uno stato al altro 

L azione è nella transizione i nodi sono STATI 


Le transizioni  hanno una sintassi ECA
- evento: obbligatorio 
- Condizioni : posizionale se c è tra parentesi quadre, se si verifica l evento e la condizione è vera si prende la transizione 
- Azione: azioni compiute  con la transizione 


due eventi con condizioni  entrambi vene si scelgono in modo non deterministico 

Se sono in uno stato in cui non c è nessuna transizione per un avento che accade l evento viene perso 



- Operazioni o segnali
	- normali eventi
- eventi di variazione _quando(__con__)_
	- al varirare di una condizione NON METTERE LE PARENTESI QUADRE 
- TEmporale
	- TIme out dove un certo tempo in uno stato 





Alcune azioni si possono fare senza cambiare stato 
### Entry exit Transaction
- Entry: appena entrato nello stato si eseguono le azioni 
- do: azione che si fa continuativamente finché si è nello stato 
- Exit: apre azioni ch e si fanno al uscita dallo stato 
- Transizioni interne : risposte a certi eventi ma rimanendo nello stato corrente 


L ordine di azioni è uscendo da uno stato 
Exit, Azioni transizioni , entry 


Stati compositi 

Transizioni di completamento: sono senza evento e si fanno in casi particolari come la fine di un nodo composito 

Stavo composito a stati paralleli 
	Aspetta che tutti i sotto nodi arrivano a completamente 


Posso fattorizzare più macchine a stati per riusarli come stati  in altri diagrammi 
	Notazioni sul bordo per gli stati che bucano oil bordo 