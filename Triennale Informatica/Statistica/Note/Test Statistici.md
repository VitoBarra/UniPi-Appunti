---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Test Statistici
---
I **_test statistici_** sono dei _test_ che ci permettono di verificare un ipotesi che abbiamo formulato è accettabile o rifiutata a seconda dei dati che abbiamo a disposizione.

siamo nella situazione in cui abbiamo molte osservazioni del fenomeno che vogliamo analizzare e riusciamo a specificare un _modello matematico probabilistico_ che dipende da alcuni parametri ignoti.  
Per fare un test statistico prima _pianificarlo_, ovvero dobbiamo _formulare un ipotesi sui parametri_ e poi _pianificare un esperimento_ per verificarla con i dati che abbiamo.

Assunzioni:
- I _modelli_ dipendono da 1 o 2 parametri (esistono pero teorie più generali)
Osservazioni: 
- i risultati ottenuti sono un approssimazione al __interno del modello matematico__ e rappresentano la realtà con un certo [[Intervalli di fiducia|intervallo di fiducia]]


#### Ipotesi nulla e alternativa (Definizione)
_sia_
- $X_{1},\dots,X_{n}$ un [[Campione Statistico|campione statistico]] la cui [[Probabilita sui numeri Reali|legge]] dipende da un parametro $\theta \in \Theta\subseteq \mathbb{R}$ e quindi la [[Funzione di Ripartizione|legge di ripartizione]] $F_{\theta}=F_{X}$
- un [[Partizione di un insieme|partizione]] $\Theta= \Theta_{0} \cup \Theta_{1}$ in due sotto insiemi disgiunti
_allora_ 
- l _ipotesi nulla_ $\mathcal{H}_{0}$ è l affermazione logica $\theta \in \Theta_{0}$ 
- l _ipotesi alternativa_ $\mathcal{H}_{1}$ è l affermazione logica $\theta \in \Theta_{1}$ 
dove
- $\Theta_{0}$ è detto l [[Insiemi Matematici|insieme]] dei parametri del **_ipotesi nulla_**
- $\Theta_{1}$ è detto l [[Insiemi Matematici|insieme]] dei parametri del **_ipotesi alternativa_** 

 A questo livello non vi è differenza tra i ruoli delle ipotesi $\mathcal{H}_0$ e $\mathcal{H}_1$, ma vi è una distinzione fondamentale contenuta invece nella definizione di test statistico. 
 
 Un test statistico è una _procedura_ per decidere se accettare o rifiutare l’ipotesi nulla $H_0$ a partire dai valori dalla realizzazione dal [[Campione Statistico|campione]] $X_{1},\dots X_{n}$: 
 - Si accetta l’ipotesi nulla $\mathcal{H}_0$ se i valori assunti dal campione sono con essa _compatibili_: in questo caso si parla di esito _negativo del test_; 
 - Si rifiuta $\mathcal{H}_0$ in favore di $\mathcal{H}_1$ se, con alto _[[Intervalli di fiducia|grado di fiducia]]_, i valori non sono _compatibili_ con $\mathcal{H}_0$ e sono in favore di $\mathcal{H}_1$, cioè se c’è evidenza statistica contro $\mathcal{H}_0$ (e per $\mathcal{H}_1$): in questo caso si parla di esito _positivo del test_. 
 
 > [!tip]
 >  _rifiutare_ $\mathcal{H}_0$ vuol dire che i dati forniscono una evidenza contro l’_ipotesi nulla_; 
 >  _accettare_ $\mathcal{H}_0$ invece non implica un’evidenza per $\mathcal{H}_0$, ma ci dice solo che i dati non forniscono evidenza contro $\mathcal{H}_0$


#### Regione critica e Test (Definizione)
_sia_
- La _regione critica_ o _regione di rifiuto_ per l ipotesi nulla $\mathcal{H}_{0}$ è un evento $C \subset \Omega$ 
- mentre $A=\Omega\backslash C$ è detto _regione di accettazione_
- $X_{1},\dots X_{n}$ un [[Campione Statistico|campione statistico]] 
_allora_ vale che l _ipotesi nulla_ $\mathcal{H}_{0}$ è 
- _respinta_ se il vettore di variabili aleatorie $X_{1}(\omega),\dots,X_{n}(\omega)$ coincide con i dati $(x_{1},\dots x_{n})$ per un qualsiasi $\omega \in C$
- _accettata_ se invece all interno della regione critica $\omega \in C$ il vettore $X_{1}(\omega),\dots,X_{n}(\omega)$ non coincide mai con i dati $(x_{1},\dots x_{n})$

Essenzialmente la _regione critica_ è la _regione di eventi_ che si controllano 



