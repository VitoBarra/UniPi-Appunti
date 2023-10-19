---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Test Statistici
---
I _test statistici_ sono dei test che ci permettono di decidere se una data ipotesi che abbiamo formulato è accettabile o va rifiutata a seconda dei dati che abbiamo a disposizione.

siamo nella situazione in cui abbiamo molte osservazioni del fenomeno che vogliamo analizzare e riusciamo a specificare un _modello matematico probabilistico_ che dipende da alcuni parametri ignoti.  
Per fare un test statistico prima _pianificarlo_, ovvero dobbiamo _formulare un ipotesi sui parametri_ e poi _pianificare un esperimento_ per verificarla con i dati che abbiamo.

Assunzioni:
- I modelli dipendono da 1 o 2 parametri (esistono pero teorie piu generali)
osservazioni: 
- i risultati ottenuti sono un approssimazione al interno del modello matematico e rapresentano la realtà con un certo [[Intervalli di fiducia|intervallo di fiducia]]


#### Ipotesi nulla e alternativa (Definizione)
_sia_
- $X_{1},\dots,X_{n}$ un [[Campione Statistico|campione statistico]] la cui [[Probabilita sui numeri Reali|legge]] dipende da un parametro $\theta \in \Theta\subseteq \mathbb{R}$ e quindi la [[Funzione di Ripartizione|legge di ripartizione]] $F_{\theta}=F_{X}$
- un [[Partizione|partizione]] $\Theta= \Theta_{0} \cup \Theta_{1}$ in due sotto insiemi disgiunti
_allora_ 
- l _iptesi nulla_ $\mathcal{H}_{0}$ è l affermazione logica $\theta \in \Theta_{0}$ 
- l _iptesi alternatica_ $\mathcal{H}_{1}$ è l affermazione logica $\theta \in \Theta_{1}$ 
dove
- $\Theta_{0}$ è detto l [[Insiemi Matematici|insieme]] dei parametri del _ipotesi nulla_
- $\Theta_{1}$ è detto l [[Insiemi Matematici|insieme]] dei parametri dell _ipotesi alternativa_ 




 Aquesto livello non vi è differenza tra i ruoli delle ipotesi $\mathcal{H}_0$ e $\mathcal{H}_1$, ma vi è una distizione fondamentale contenuta invece nella definizione di test statistico. Un test statistico è una _procedura_ per decidere se accettare o rifiutare l’ipotesi nulla $H_0$ a partire dai valori assunti dal [[Campione Statistico|campione]] $X_{1},\dots X_{n}$: 
 - si accetta l’ipotesi nulla $\mathcal{H}_0$ se i valori assunti dal campione sono con essa _compatibili_: in questo caso si parla di esito _negativo del test_; 
 - si rifiuta $\mathcal{H}_0$ in favore di $\mathcal{H}_1$ se, con alto _[[Intervalli di fiducia|grado di fiducia]]_, i valori non sono _compatibili_ con $\mathcal{H}_0$ e sono in favore di $\mathcal{H}_1$, cioè se c’è evidenza statistica contro $\mathcal{H}_0$ (e per $\mathcal{H}_1$): in questo caso si parla di esito positivo del test. 
 
 > [!tip]
 >  _rifiutare_ $\mathcal{H}_0$ vuol dire che i dati forniscono una evidenza contro l’_ipotesi nulla_; 
 >  _accettare_ $\mathcal{H}_0$ invece non implica un’evidenza per $\mathcal{H}_0$, ma ci dice solo che i dati non forniscono evidenza contro $\mathcal{H}_0$.


#### Regione critica e Test (Definizione)
_sia_
- La _regione critica_ o _regione di raggiunto_ per l iptesi nulla $\mathcal{H}_{0}$ è un evento $C \subset \Omega$ 
- mentre $A=\Omega\backslash C$ è detto _regione di accettazione_ 
- $X_{1},\dots X_{n}$ un [[Campione Statistico|campione statistico]] e $(x_{1},\dots x_{n})$ una sua _realizzazione del campione_ 
_allora_ vale che l ipotesi è 
- _respinta_ se il vettore di variabili aleatorie $X_{1}(\omega),\dots,X_{n}(\omega)$ assume valore $(x_{1},\dots x_{n})$ per un qualunque $\omega \in C$
- _accettata_ se invece all interno della regione critica $\omega \in C$ il fattore $X_{1}(\omega),\dots,X_{n}(\omega)$ non coincide mai con i dati $(x_{1},\dots x_{n})$

#### Errori (Definizione)
Il risultato del test (accettare o rifiutare $\mathcal{H}_{0}$) e soggetto a due tipi di errori
- _Errore di prima specie_(falso positivo): Viene rifiutata l ipotesi $\mathcal{H}_{0}$ quando questa è soddisfatta.   
	- se $\theta \in \Theta_{0}$ la probabilita di commettere un _falso positivo_ è $\mathcal{P}_{\theta}(C)$   
-  _Errore di seconda specie_(falso negativo): si accetta $\mathcal{H}_{0}$ anche quando le condizioni non sono verificate
	- se $\theta \in \Theta_{1}$ la _probabiltia_ di commettere un falso negativo è $\mathcal{P}_{\theta}(A)$
	


#### livello e poterne a di un test
_sia_ $\alpha \in (0,1)$ un numero 
_allora_ si disce che il _test_ è di _livello_ $\alpha$
_se_ $$\forall  \theta \in  \Theta_{0} \ \ \ \ \mathcal{P}_{\theta}(C)\leq a$$_allora_ si chiama _potenza_ del test la [[Funzioni|funzione]] definita sui parametri del alternativa $$\Theta_{1} \ni \theta \to \mathcal{P}_{\theta}(C) \in  [0,1] $$

dove 
- il _livello del test_ rappresenta un _limite superiore_ per la probabilita del errore di _prima specie_ 
	- piu piccolo è $\alpha$ piu evidenze chiediamo per rifiutare $\mathcal{H}_{0}$
- la _potenza del test_ è la probabilita $\mathcal{P}_{\theta}$ di rifiutare correttamente $\mathcal{H}_{0}$  e quindi $1-\mathcal{P}_{\theta}$ è la probabilita di errore di _secondao sepecie_
	- ovvero è la capacita di accorgerci che $\mathcal{H}_{0}$ non è soddisfatta   
	 

#### Curva operative
una definizione alternativa e equivalente è la _curva operativa_
##### Curva operative (Definizione)
si chiama _curva operativa_ la [[Funzioni|funzione]] definita sull’ intererò insieme dei parametri $$\Theta \ni \theta \mapsto \beta(\theta)=\mathcal{P}_{\theta}(C^{c})=1-\mathcal{P}_{\theta}\in  [0,1] $$
ovvero, la [[Probabilita sui numeri Reali|probabilita]], in fu zone del parametro $\theta$, di accettare l _ipotesi nulla_ si diche che:
- se $\theta \in \Theta_{0}, \beta(\theta)$ è il _tasso di falso postivo_
- se $\theta \in  \Theta_{1},1- \beta(\theta)$ è il _tasso di falso negativo_


> [!tip] Curve operative vs livello e potenza
> Il _tasso di falso negativo_ coincide con la _potenza del test_
> il _livello del test_ è il minimo valore _tasso di falso positivo_  su $\Theta_{0}$



#### P-value
la _regione critica_ viene scelta a priori cercando di soddisfare il livello rischiesto $\alpha$ ma ci sono metodologie alternative che dipendono direttamente dalla realizzazione $(x_{1},\dots,x_{n})$ del campione $X_{1},\dots,X_{n}$


##### P-value (Definito)
_sia_
- $\{ C(\alpha) \}_{\alpha \in (0,1)}$ una _famiglia di regioni critiche_ tali che il test con ipotesi nulla $\mathcal{H}:\theta \in \Theta_{0}$ con regione critia $C(\alpha)$ abbia _livello_ $\alpha$ 
- data una realizzazione $(X_{1},\dots x_{n})$ del [[Campione Statistico|campione]] $(X_{1},\dots,X_{n})$
_allora_ il $p-$value  è il numero $\overline{\alpha}=\overline{\alpha}(x_{1},\dots,x_{n})$ tale che:
- se $\alpha < \overline{\alpha}$ l ipotesi nulla viene accettata dal test di regione critica $C(\alpha)$ e si dice che viene _accettata al livello_ $\alpha$
- se $\alpha > \overline{\alpha}$ l ipotesi viene rifiutata dal _test di regione critica_ $C(\alpha)$




