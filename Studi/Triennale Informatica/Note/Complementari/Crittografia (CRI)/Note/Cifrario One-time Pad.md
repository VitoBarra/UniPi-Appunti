---
Subject: "[[Crittografia (CRI)]]"
topic: nota
tags:
  - CRI
---
# Cifrario One-time Pad
---
l _One-time Pad_ é un [[Cifrari perfetti|cifrario perfetto]]


#### Fatti storici
inventato nel 1917 da Mauborgne e vernan, usato da Washinton e Mosca per le comunicazione e diventato famoso per questo sotto il nome di _telefono rosso_


#### Definizione
Per utilizzare questo cifrario dobbiamo assumere che messaggi e chiavi siano in [[Rappresentazione di oggetti matematici con sequenze|rappresentazione binaria]]. Non una grande limitazione siccome comunque questo cifrario è utilizzo tramite _calcolatori_ quindi non potrebbe essere altrimenti.

le stringhe binarie verranno riconvertite da binario a _linguaggio naturale_ e i metodi di conversione sono _pubblici_ (esempio l ASCII) ma ciò non influisce sulla sicurezza quindi non sono oggetto di studio.


Dati
- un _messaggio_ $m$ una sequenza di $m_{1}m_{2}\dots m_{n}$ _bit_ 
- una _chiave_ $k$ una sequenza di $k_{1}k_{2}\dots k_{n}\dots k_{m}$ _bit_ [[Sequenza casuali|scelti perfettamente a caso]] e conosciuti sia da _mittente_ che _destinatario_

le operazioni di [[Cifratura e Decifratura|cifratura e decifratura]] si basano sullo [[Operazioni logiche#XOR|XOR]] bit a bit del _messaggio_ e della _chiave_ e abbiamo quindi che per $\forall i = 1 \dots n$
$$
\begin{array}
\mathcal{C}_{i}(m_{i},k_{i}) & = & m_{i} \oplus k_{i}\\
\mathcal{D}_{i}(c_{i},k_{i}) & = & c_{i} \oplus k_{i}
\end{array}
$$
il processi ci _cifratura e decifratura_ consuma la chiave scorrendola in avanti, non bisogna usare due volte la stessa porzione di chiave.

un vantaggio di questo cifrario e che cancella qualsiasi tipo di patern periodici nel messaggio ad esempio 
$m = 01010101$ e $k=01001110$ abbiamo che $c=00011011$

questo cifrario è semplice e _perfetto_ ma una problematica è l impossibilita di generare le chiavi in modo economico e veloce.

### Teorema
_Se_ 
- tutti i messaggi hanno la stessa lunghezza $n$
- tutte le sequenze di $n$ _bit_ sono messaggi possibili
- impiegando una chiave $k$ scelta perfettamente a caso per ogni messaggi
_Allora_ il cifrario _one time pad_ è [[Cifrari perfetti|perfetto]] e usa un numero _minimo_ di chiavi.

>[!warning]
>se tutti i messaggi non fossere tutto di dimensione $n$ la lunghezza del messaggio diventa un informazione per il crittoanalista e questo si evita con _padding_ se il messaggio è corto o dividendo in blocchi il messaggio se è troppo lungo 

#### Dimostrazione
la _minimalita delle chiavi_ discende dal fatto che $$|Mes|=2^{n} =|K|$$ ed essendo lo stesso numero allora è _minimo_

mentre per dimostrare che il _cifrario è perfetto_ dobbiamo distrare come _dalla definizione_ che 
$$\mathcal{P}(M=m|C=c)=\mathcal{P}(M=m)$$
e per farlo applichiamo la _definizione_ di  [[Probabilita condizionata|probabilita condizionata]] 
Abbiamo quindi che $$\mathcal{P}(M=M\mid C=c)=\frac{\mathcal{P}(M=m\cap C=c)}{\mathcal{P}(C=c)}$$con $\mathcal{P}(M=m\cap C=c)$ stiamo rappresentando i casi in cui il _messaggio_ sia generato da $mit$ è $m$ e il _crittogramma_ generato è esattamente $c$ 
per definizione di [[Operazioni logiche#XOR|XOR]] con un $m$ fissato abbiamo che _chiavi diverse_ danno _crittogrammi diversi_ e usando tutte le _chiavi possibili_ possiamo raggiungere ogni _crittogramma possibile_ ed ognuno di questi può essere generato con probabilità $\left( \frac{1}{2} \right)^{n}$ perciò abbiamo perciò che $\mathcal{P}(C=c)= \left( \frac{1}{2} \right)^{n} \ \ \forall c$  quindi $\mathcal{P}(C=c)$ è costante e di conseguenza è [[Indipendenza Stocastica|indipendente]] da $m$ e perciò vale che
$$\mathcal{P}(M=m\cap C=c) = \mathcal{P}(M=m) \times \mathcal{P} (C =c)$$
e quindi 
$$
\begin{array} {}
\mathcal{P}(M=m|C=c) & = &  
\cfrac{\mathcal{P}(M=m\cap C=c)}{\mathcal{P}(C=c)} \\
 & =& \cfrac{\mathcal{P}(M=m) \times \cancel{ \mathcal{P} (C =c) }}{\cancel{ \mathcal{P}(C=c) }} \\
& =&\mathcal{P}(M=m)
\end{array}
$$
e quindi vale 
$$\mathcal{P}(M=m|C=c) =\mathcal{P}(M=m)$$
che è la _definizione_ di [[Cifrari perfetti|cifrario perfetto]]


#### Riutilizzo delle chiavi
le chiavi per l _one-time pad_ deve essere scartata mano mano che viene usata altrimenti il cifrario sarebbe vulnerabile al [[Tipologia di attacchi ai cifrari|cipher text]] 
infatti abbiamo che se usiamo _la stessa chiave_ $k$ per cifrare i due _messaggi_ $m'$ e $m''$ otterremmo  i due _crittogrammi_ $c'_i=m'_i\oplus k_i$ e $c_i''=m_i''\oplus k_i$  da ci per proprietà dello [[Operazioni logiche|XOR]] abbiamo che
$$c'_i \oplus c''_i = m'_i \oplus m''_i$$ 
questa relazione puo dare informazioni al crittoanalista, ad esempio una parte di zeri consecutivi significa parti dei _messaggi identici_.


#### Generazione delle chiavi
Abbiamo quindi il problema di non poter _riutilizzare la chiave_ e la sequenza di bit deve essere _perfettamente casuale_ 
le chiavi sono lunghe sequenze di bit e poter generarle si potrebbero usare i [[Generatori di numeri Pseudo Casuali|generatori di numeri pseudo cusuale]] _crittograficamente sicuri_
cosi da dover gestre solo il problema di dover dare condividere il _seme_ del generatore.

ci sono due sistemi per utilizzare i generatori e sono

il primo _generatore è pubblicamente_ noto e seme segreto.
questo sistema è conforme alle [[Crittografia Concetti Generali#Metodo publico|ipotesi della crittografia]] ma espone il _cifrario_ ad un attacco esauriente _sullo spazio dei semi_ del generatore. Per risolvere questo problema c è bisogno di semi molto lunghi. 
un altro problema è che essendo il generatore pubblico si conosce la grandezza del _periodo_ e quindi il cifrario potrebbe essere attaccato usando il problema del riuso una volta finito la prima volta il periodo. questo si puo risolvere accordandosi _su più semi_, ma ciò è costoso

un secondo approccio è _generatore e seme_ segreti. ciò è in contrasto con i principi di _algoritmi pubblici_  fattibile solo perché i generatori sono solitamente poche istruzioni. ma richiede a $mit$ e $dest$ di implementare un proprio generatore e i proprio semi.

un compromesso su i due approcci è quello di concordare un file ed utilizzare quello come sorgente della chiave tenendo segreto il punto di inizio. 
	Un esempio di file utilizzabile è un genomico di un DNA.

#### Ridurre il numero di chiavi necessarie
Un approccio diverso quello di cercare di ridurre il numero di _bit casuali_ necessari alla chiave mantenendo la _perfezione_ del cifrario. 
Si toglie la codinzone del  [[#Teorema]] che dice _tutte le sequenze di bit_ sono messaggi validi e si cerca di ridurre lo spazio dei messaggi in modo da poter ridurre anche quello delle chiavi.
Anche senza quella condizione si puo dimostrare che il cifrario resta _perfetto_ ma il numero di chiavi non è piu minimo.

si utilizza quindi un [[Critto analisi Statistica|approccio statistico]] e partendo dal _ipotesi_ che
- il mittente manda messaggi fatti in accordo alla [[distribuzione di probabilita|distribuzioni di probabilità]] delle lettere della lingua scelta 
- che la probabilità del prossimo carattere è in funzione dei $q-1$ precedenti
- e in accordo alla distribuzione dei q-grammi della lingua
si ha la "fedeltà" tanto migliore tanto piu è grande $q$ e non si generano messaggi con sequenze inesistenti nel linguaggio.

il modello risultante e solo un approssimazione ma è abbastanza buona per poterci condurre studio statistici.

si stima che nei linguaggio naturali il numero di sequenze di $n$ bit significative siano $\alpha^{n}$ con $\alpha<2$ ed è una _costante diversa_ per ogni lingua.

essendo il numero dei messaggi possibili $\alpha^{n}$ possiamo cercare di abbasssare il numero di bit casuali necessari a mantenere le proprietà del _cifrario perfetto_ per poi aggiungere in modo deterministico gli $n-t$ bit mancati che servo per poter utilizzare Onte-Time Pad .
per fare ciò cerchiamo il limite inferiore $t$ di _bit casuali_ partendo dal  [[Cifrari perfetti#Teorema|teorema del cifrario perfetto]] abbiamo che per l inglese $$N_{k}=2^{t} \ \geq \alpha ^{n}=N_{m} \implies t \geq n \log_{2}\alpha \approx 0.12n$$
e quindi abbiamo che il numero di _bit casuali_ necessari è $0.12n$, 

con questo numero di bit  è poco probabile che _messaggi diversi_ portino a _crittogrammi uguali_ con _chiavi diverse_, cosa che invece _sicuramente succede_ se sono validi tutte le sequenze di lunghezza $2^{n}$ . questo è un problema perche critto analista potrebbe attaccare il cifrario con un _attacco esauriente_ invece se _più crittogrammi_ possono esserere decifrati in _piu messaggi significativi_ con _chiavi diverse_  il crittoanalista non puo essere sicuro di quale messaggio è stato effettivamente mandato
![[Pasted image 20230706210518.png]]
 se vogliamo associare ogni messaggio a piu crittogrammi con chiavi diverse dobbiamo avere $$\alpha^{n} \cdot 2^{t} \gg 2^{n}$$
 dove  $a^{n}\cdot 2^{t}$ è il numero di crittogrammi ottenibili cifrando ogni messaggio con ogni chiave e $2^{n}$ è il numero di sequenze binarie ottenibile con $n$ cifre e quindi il _numero di crittogrammi diversi_
 
da quella relazione si ricava
$$
\begin{array} {}
 \log_{2}(\alpha^{n}\cdot 2^{t}) & \gg &  \log_{2}(2^{n})  &  \implies\\  
\log_{2}(\alpha^{n})+\log_2(2^{t})  & \gg   & \log_{2}(2^{n})&  \implies\\
n\log_{2}\alpha+t & \gg &  n  & \implies \\
 t  & \gg  & n - n\log_2 a  &  \implies\\
t  & \gg &  0.88n &
\end{array}
$$
ricordando che $n\log_{2}a \approx 0.12$ abbiamo che $t$ è comunque molto _vicino_ ad $n$ e di conseguenza _comunque molto costoso_ anche riducendo lo spazio dei messaggi.


 