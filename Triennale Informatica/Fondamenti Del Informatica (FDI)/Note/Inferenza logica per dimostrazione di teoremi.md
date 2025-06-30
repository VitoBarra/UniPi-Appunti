---
Corse 1: "[[Artificial Intelligence Fundamentals (AIF)]]"
Course: "[[Fondamenti Del Informatica (FDI)]]"
tags:
  - FDI
  - AIF
  - IA
Area: "[[Logica]]"
topic: 
SubTopic:
---

# Inferenza logica con dimostrazione di teoremi (Theorem Proving)
---
il **theorem proving** è un approccio per l'[[Sistemi di inferenza logica|inferenza logica]] che permette di stabilire la [[Conseguenza Logica (Deduzione)|conseguenza logica]] tra due [[Logica|enunciati]] applicando **regole di inferenza** direttamente sugli **enunciati** presenti nella **knowledge base**

la notazione per una **regola di inferenza** è la seguente $$\frac{p_1, \dots,p_n}{c_1,\dots,c_m}$$ dove $p_i$ sono le **premesse** necessarie a dedurre le $c_i$ **conclusioni**, sia $p_i$ che $c_j$ sono **[[Logica|enunciati]]**


Questo metodo risulta particolarmente vantaggioso quando il numero di modelli è molto elevato ma la lunghezza della dimostrazione è contenuta.

Questa strategia si basa sullo sfruttare tue teoremi: 
**siano**  $\alpha$ e $\beta$ due **enunciati**

il **teorema di deduzione** afferma che: $$\alpha \models \beta \iff (\alpha \Rightarrow \beta) \text{ è tautologia}$$ovvero, per verificare che  $\beta$ sia [[Conseguenza Logica (Deduzione)|conseguenza logica]] $\alpha$, si può controllare che l'implicazione $(\alpha \Rightarrow \beta)$ sia $True$ in tutti i **modelli**, oppure si può dimostrare che tale implicazione è [[Equivalenza logica|logicamente equivalente]] a $\mathit{True}$. 


mentre il **Teorema di refutazione** afferma che:
$$\alpha \models \beta \iff (\alpha \land \lnot \beta) \text{ è insodisfacibbile}$$
ovvero, per verificare che  $\beta$ sia [[Conseguenza Logica (Deduzione)|conseguenza logica]] $\alpha$ si puo verificare l'insoddisfacibilità di $(\alpha \land \neg \beta)$  questo ci permette di riportare il problema ad un problema [[Problemi della Sodisfacibilita (SAT)|SAT]]

il **teorema di refutazione** è alla base della tecnica della [[Dimostrazione di Teoremi per assurdo|reductio ad absurdum, o prova per contraddizione]]




### Regole di inferenza
L'**un sistema di inferenza per generare dimostrazioni** si basa sulla [[Logica proposizionale|Logica proposizionale]] e su un insieme di regole che permettono di derivare deduzioni a partire da premesse note, costruendo così una catena di [[Conseguenza Logica (Deduzione)|conseguenze logiche]] coerenti. 



Tutte le [[Equivalenza logica|equivalenze logiche]] del [[Logica proposizionale|calcolo proposizionale]] possono essere riscritte con questa notazione di inferenza, altre regole invece sono:

 **Modus Ponens**, letteralmente "modo che afferma", formalizzato come:
  $$\frac{\alpha \Rightarrow \beta , \ \alpha} {\beta}$$
**And-Elimination**, la quale stabilisce che, data una congiunzione, è possibile inferire ciascun congiunto separatamente, formalizzabile come $$\frac{\alpha \land \beta }{\alpha}$$


La **regola di risoluzione** permette di eliminare due **enunciati** che sono in contradizione tra di loro. è espressa formalmente come:$$
\frac{\ell_1 \lor \cdots \lor \ell_k, \quad m}{\ell_1 \lor \cdots \lor \ell_{i-1} \lor \ell_{i+1} \lor \cdots \lor \ell_k}
$$dove $\ell_i$ e $m$ sono letterali complementari ovvero uno è il negato del altro.
Più in generale, la risoluzione si estende alla forma completa, applicabile a due clausole qualsiasi:$$
\frac{\ell_1 \lor \cdots \lor \ell_k, \quad m_1 \lor \cdots \lor m_n}{\ell_1 \lor \cdots \lor \ell_{i-1} \lor \ell_{i+1} \lor \cdots \lor \ell_k \lor m_1 \lor \cdots \lor m_{j-1} \lor m_{j+1} \lor \cdots \lor m_n}
$$con $\ell_i$ e $m_j$ letterali complementari. 
La regola prevede che si possa risolvere **una sola** coppia di letterali complementari per ciascuna applicazione, evitando di trattare più coppie simultaneamente. 
es. $$\frac{P\lor Q, \ \ \  \lnot P \lor \lnot Q}{\{\}}$$questo porterebbe ad una **contradizione** ma è un infatti l applicazione corretta è:$$\frac{P\lor Q ,\ \ \  \lnot P \lor  \lnot Q}{P\lor \lnot P} \ \ \ \ \ \frac{P\lor Q, \ \ \  \lnot P \lor  \lnot Q}{Q\ \lor\lnot Q} $$ ovvero risultano che sono due **tautologie**

in caso di **ripetizioni di letterali** nella conclusione ottenuta del applicazione di questa regola si fa il ***factoring***, ovvero le si unisce in un unico letterale. es $A \lor A\equiv A$

La correttezza della risoluzione deriva da una semplice osservazione sulla verità dei letterali coinvolti. infatti siccome $\ell_i, m_j$ sono contrapposti si ha che $\ell_i= True\implies m_j=False$, ma siccome $m_1 \lor \cdots \lor m_n=True \ \land\ m_j=False\implies m_1 \lor \cdots \lor m_{j-1} \lor m_{j+1}=True$  è quindi l'espressione finale è $True$ Viceversa, analogo vale per il caso inverso.


### Proprietà
Applicando queste di inferenza il cambiamento del **numero di conoscenze** in $KB$ è monotonica crescente, questo è vero perche l'aggiunta di nuove informazioni non può **invalidare inferenze già effettuate**
Formalmente abbiamo che:
***siano***  $\alpha$ e $\beta$ due **enunciati**
**vale sempre** $$KB \models \alpha \implies KB \land \beta \models \alpha$$
## Dimostrazione tramite ricerca
Al fine di effettuare una dimostrazione, ovvero raggiungere la conclusione che uno **enunciato** è $True$ o $False$ si possono usare le regole di inferenza per **dimostrazione** per formalizzare un [[Problemi di ricerca|problema di ricerca]] in cui lo 
- **stato iniziale**: è costituito dalla **base di conoscenza**
- **le azioni**: sono le applicazioni delle **regole d'inferenza**, 
- **i risultati delle azioni**:  consiste nell'aggiungere nuove proposizioni inferite
- **il goal**: è raggiungere lo stato in cui la proposizione da dimostrare è presente.

Questo approccio si rivela particolarmente efficiente nei sistemi complessi, poiché permette di ignorare proposizioni irrilevanti rispetto all'obiettivo, indipendentemente dalla loro numerosità.


