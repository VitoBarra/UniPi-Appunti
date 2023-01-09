# Livello Rete - ICMP
il internet control messale Protocol (_ICMP_ ) è un [[protocollo]] di controllo di errore  del [[Livello di rete]] che si utilizza insieme a [[Livello di rete - IP|IP]] 
server per sopperire alcune mancanze di IP quali:
- Meccanismo per richiesta sullo _stato di un sistema_ 
- segnalazione degli _errori_
viene usato tra host e router per scambiarsi messaggi di errore o situazioni che richiedono intervento
questi messaggi sono incapsulati in datagrammi IP
- Sono comunque considerati parte integrande del [[Livello di rete]]
- chi iplementa Ip deveo supportare anche ICMP


-  Quando un router o un host di destinazione devono _informare il mittente_ di errori o di eventi avvenuti nell’inoltro di un pacchetto IP utilizzano il protocollo Internet Control Message Protocol (ICMP). 
- I pacchetti _ICMP_ vengono instradati dai router prima dei pacchetti IP ordinari 
	- Per pacchetti IP frammentati, i messaggi ICMP sono relativi al solo frammento con offset 0 (_il primo frammento_). 
	- I messaggi ICMP __NON__ sono mai inviati in risposta a pacchetti IP con indirizzo mittente che non rappresenta in modo univoco un host (es. 0.0.0.0, 127.0.0.1). 
	- I messaggi ICMP __NON__ sono mai inviati in risposta a pacchetti IP con destinazione IP broadcast o multicast (o link broadcast) 
- I messaggi _ICMP_ non sono mai inviati in risposta a messaggi di errore _ICMP_, ma possono essere inviati in risposta a messaggi ICMP di interrogazione.

### Tipi di messaggi
i messaggi si distinguono in messaggi di: 
- _segnalazione errore_ 
- _richiesta/_risposta
- Nell’header ICMP i campi Tipo (8 bit) e Codice (8 bit) indicano tipo e significato dei messaggi
![[Pasted image 20230107003445.png]]
![[Pasted image 20230107003436.png]]

