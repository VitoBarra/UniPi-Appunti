---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrario One-time Pad
---
l _One-time Pad_ é un [[Cifrari perfetti|cifrario perfetto]]


#### Fatti storici
inventato nel 1917 da Mauborgne e vernan, usato da Washinton e Mosca per le comunicazione e diventato famoso per questo sotto il nome di _telefono rosso_


#### Definizione
Per utilizzare questo cifrario dobbiamo assumere che messaggi e chiavi siano espresse in _binario_. Non una grande limitazione siccome comunque questo cifrario è utilizzo tramite calcolatori quindi non potrebbe essere altrimenti.

le stringhe binarie verranno riconvertite da binario a _linguaggio naturale_ e i metodi di conversione sono _pubblici_ (esempio l ASCII) ma ciò non influisce sulla sicurezza quindi non sono oggetto di studio.


Dati
ua, quanto e bell il cazz
- un _messaggio_ $m$ una sequenza di $m_{1}m_{2}\dots m_{n}$ _bit_ 
- una _chiave_ $k$ una sequenza di $k_{1}k_{2}\dots k_{n}\dots k_{m}$ _bit_ scelti perfettamente a caso e conosciuti sia da _mittente_ che _destinatario_

le operazioni di [[Cifratura e Decifratura|cifratura e decifratura]] si basano sullo [[Operazioni logiche#XOR|XOR]] bit a bit del _messaggio_ e della _chiave_ e abbiamo quindi che per $\forall i = 1 \dots n$
$$
\begin{array}
\mathcal{C}_{i}(m_{i},k_{i}) & = & m_{i} \oplus k_{i}\\
\mathcal{D}_{i}(c_{i},k_{i}) & = & c_{i} \oplus k_{i}
\end{array}
$$
il processi ci _cifratura e decifratura_ consuma la chiave scorrendola in avanti, non bisogna usare due volte la stessa porzione di chiave.

un vantaggio di questo cifrario e che cancella qualsiasi tipo di patern periodi con nel messaggio ad esempio 
$m = 01010101$ e $k=01001110$ abbiamo che $c=00011011$

questo cifrario è semplice e perfetto ma il problema serio e nella generazione economica e veloce delle chiavi.

### Teorema
_Se_ 
- tutti i messaggi hanno la stessa lunghezza $n$
- tutte le sequenze di $n$ _bit_ sono messaggi possibili
- impiegando una chiave $k$ scelta perfettamente a caso per ogni messaggi
_Allora_ il cifrario _one time pad_ è perfetto e usa un numero minimo di chiavi.

#### Dimostrazione
la _minimalista delle chiavi_ discende dal fatto che $|K|=|Mes|=2^{n}$

mentre per dimostrare che il _cifrario è perfetto_ dobbiamo distrare come dalla definizione che 
$$\mathcal{P}(M=m|C=c)=\mathcal{P}(M=m)$$
e per farlo applichiamo la _definizione_ di  [[Probabilità condizionata e indipendenza|probabilita condizionata]] 
abbiamo quindi che 
$$\mathcal{P}(M=m|C=c)=\frac{\mathcal{P}(M=m\cap C=c)}{\mathcal{P}(C=c)}$$
con $\mathcal{P}(M=m\cap C=c)$ stiamo rappresentando i casi in cui il _messaggio_ sia generato da $mit$ è $m$ e il _crittogramma_ generato è esattamente $c$ 
ora notiamo che fissato $m$ per definizione di [[Operazioni logiche#XOR|XOR]] abbiamo che _chiavi diverse_ danno _crittogrammi diversi_ e ogni chiave puo essere generata con probabilità $\left( \frac{1}{2} \right)^{2}$ e di conseguenza fissato $m$  abbiamo che $\mathcal{P}(C=c)= \left( \frac{1}{2} \right)^{2} \ \ \forall c$  quindi $\mathcal{P}(C=c)$ è costante e di conseguenza abbiamo che [[Indipendenza Stocastica|indipendente]] da $m$ e quindi vale 
$$\mathcal{P}(M=m\cap C=c) = \mathcal{P}(M=m) \times \mathcal{P} (C =c)$$
unendo le due equazione otteniamo

$$
\begin{array} {}
\mathcal{P}(M=m|C=c) & = &  
\cfrac{\mathcal{P}(M=m\cap C=c)}{\mathcal{P}(C=c)} \\
 & =& \cfrac{\mathcal{P}(M=m) \times \mathcal{P} (C =c))}{\mathcal{P}(C=c)} \\
& =&\mathcal{P}(M=m)
\end{array}
$$
e quindi vale 
$$\mathcal{P}(M=m|C=c) =\mathcal{P}(M=m)$$
che è la _definizione_ di [[Cifrari perfetti|cifrario perfetto]]


#### Riutilizzo delle chiavi
le chiavi per l _one-time pad_ deve essere scartata mano mano che viene usata altrimenti il cifrario sarebbe vulnerabile al [[Tipologia di attacchi per scoprire il messaggio criptato|cipher test]] 
infatti abbiamo che se usiamo _la stessa chiave_ $k$ per cifrare i due _messaggi_ $m'$ e $m''$ otterremmo  i due _crittogrammi_ $c'_i=m'_i\oplus k_i$ e $c_i''=m_i''\oplus k_i$  da ci per prosperità dello [[Operazioni logiche|XOR]] abbiamo che
$$c'_i \oplus c''_i = m'_i \oplus m''_i$$ 
questa relazione puo dare informazioni al crittoanalista, ad esempio una parte di zeri consecutivi significa parti dei _messaggi identici_.


#### Generazione delle chiavi
 abbiamo quindi il problema di non poter _riutilizzare la chiave_ e la sequenza di bit deve essere _perfettamente casuale_ 
le chiavi sono lunghe sequenze di bit e poter generarle si potrebbero usare i [[Numeri Pseudo Casuali|generatori di numeri pseudo cusuale]] _crittograficamente sicuri_
cosi da dover gestri solo il problema di dover dare condividere il _seme_ del generatore.

ci sono due sistemi per utilizzare i generatori e sono

il primo _generatore è pubblicamente_ noto e seme segreto.
questo sistema è conforme alle [[Crittografia Concetti Generali#Metodo publico|ipotesi della crittografia]] ma espone il _cifrario_ ad un attacco esauriente _sullo spazio dei semi_ del generatore. Per risolvere questo problema c è bisogno di semi molto lunghi. 
un altro problema è che essendo il generatore pubblico si conosce la grandezza del _periodo_ e quindi il cifrario potrebbe essere attaccato usando il problema del riuso. questo si puo risolvere accordandosi si piu semi, ma ciò è costoso

un secondo approccio è _generatore e seme_ segreti. ciò è in contrasto con i principi di _algoritmi pubblici_  fattibile solo perché i generatori sono solitamente poche istruzioni. ma richiede a $mit$ e $dest$ di implementare un proprio generatore e i proprio semi.

un compromesso su i due approcci è quello di concordare un file ed utilizzare quello come sorgente della chiave. un esempio di file utilizzabile è un genomico di un DNA.


un approccio diverso, si rilassano le condizioni del [[#Teorema]] lasciando il punto sulla significatività dei messaggi. si puo dimostrare che il cifrario resta perfetto ma il numero di chiavi non è piu minimo.

si utilizza quindi un [[Critto analisi Statistica|approccio statistico]] e partendo dal _ipotesi_ che
- il mittente mandi messaggi fatti in accordo alla distribuzioni di probabilità delle lettere della lingua scelta 
- che la probabilità del prossimo carattere è in funzione dei $q-1$ precedenti
- e in accordo alla distribuzione dei q-grammi della lingua
si ha la "fedeltà" tanto migliore tanto piu è grande $q$ e non si generano messaggi con sequenze inesistenti nel linguaggio.

il modello risultante e solo un approssimazione ma è abbastanza buona per poterci condurre studio statistici.

si stima che nei linguaggio natura il numero di seguente di $n$ bit significative siano $\alpha^{n}$ con $\alpha<2$ ed è una _costante diversa_ per ogni linguaggio.

essendo il npipoumero dei messaggi possibili $\alpha^{n}$ possiamo cercare di abbassare il numero dello _spazio delle chiavi_ $|K|$ mantenendo il numero dei bit $n$

cerchiamo quindi il limite inferiore $t$ di _bit casuali_ necessari per mantenere il _cifrario perfetto_ e aggiungendo il restanti $n-t$ bit in modo _deterministico_.

dal [[Cifrari perfetti#Teorema|teorema del cifrario perfetto]] abbiamo che $$2^{t} \ \geq \alpha ^{n} \implies t \geq n \log_{2}\alpha \approx 0.12n$$ e quindi abbiamo che il numero di bit casuali necessari è $0.12n$

per aumentare la sicurezza possiamo fare si che lo stesso crittogramma $c$ con _chiavi diverse_ venga decrittato in  _diversi messaggi significati_. il crittoanalista non potrebbe stabilire quale è l effettivo messaggio trasmesso anche completando un attacco esauriente.
![[Pasted image 20230706210518.png]]

allo stesso modo vale se messaggi diversi vengono con _chiavi diverse_ criptati nello stesso crittogramma.

per fare questo c bisogno che diversi messaggi crittati con tutte le chiavi generano piu volte lo stesso crittogramma $c$  

e questo è vero se $$\alpha^{n} \cdot 2^{t} \gg 2^{n}$$
e da qui si ricava subito che
$$t+n\log_{2}\alpha\gg n$$
ovvero $$t \gg 0.88n$$
quindi essenzialmente comunque molto vicino ad $n$ e di conseguenza comunque molto costoso

 