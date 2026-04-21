---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# DESeq2 - DE per RNAseq
---
**DESeq2** è un framework statistico per [[Analisi RNA-seq|RNA-seq]] basato su conteggi discreti che integra normalizzazione tra campioni, modellizzazione probabilistica e test di espressione differenziale. L’input è la matrice **geni × campioni** di conteggi grezzi; la normalizzazione introduce fattori di scala $s_i$ che rendono confrontabili i campioni, mentre l’inferenza è effettuata sui conteggi tramite un modello coerente con la relazione **media–varianza** osservata nei dati.

Per ciascun gene $g$ e campione $i$ i conteggi sono modellati tramite una **[[Variabili aleatorie Notevoli - Negative Binomial|Negative Binomial]] (NB)**:
$$Y_{gi}\sim \text{NB}(\mu_{gi},\theta_g)$$
dove $\mu_{gi}$ è la media attesa e $\theta_g$ la dispersione specifica del gene. La varianza è
$$\mathrm{Var}(Y_{gi})=\mu_{gi}+\theta_g\mu_{gi}^2$$
Il termine quadratico consente di modellare l’overdispersion rispetto alla [[Variabili Aleatorie Notevoli - Poisson|Poisson]], in cui varianza e media coincidono.

La dispersione $\theta_g$ misura la variabilità biologica tra replicati oltre il rumore [[Variabili Aleatorie Notevoli - Poisson|Poisson]]. Con pochi replicati, la stima gene-wise è instabile: i geni poco espressi contengono poca informazione e possono produrre stime estreme per puro rumore campionario.
**DESeq2** stima $\theta_g$ in tre fasi:
- stima gene-wise per ogni gene
- stima di un trend globale dispersione–media
- shrinkage empirical Bayes verso il trend
La dispersione finale $\hat\theta_g$ è un compromesso tra informazione del singolo gene e informazione globale (bias–variance trade-off), riducendo la varianza delle stime e migliorando il controllo dell’errore di tipo I.
![[IMG - DESeq2 stime della shrinkage dispersion.png]]

La media è collegata al disegno sperimentale tramite un [[Generalized Linear Model (GLM)|GLM]] con link [[Funzione logaritmica|log]]:
$$\log \mu_{gi} = \log s_i + x_i^T \beta_g$$
dove $x_i$ rappresenta le [[Variabili aleatorie - Covarianza e correlazione|covariante]] sperimentali e $\beta_g$ i coefficienti del modello.

## Design sperimentale
Il design passato a **DESeq2** definisce il [[Generalized Linear Model (GLM)|GLM]] che viene fittato sui conteggi. Non è un passaggio descrittivo successivo all’analisi: stabilisce quali fattori sperimentali entrano nel modello e quale effetto viene testato.

La formula usa la sintassi standard dei modelli in R. Il design più semplice è
```r
design = ~ condition
```
e modella l’espressione come dipendente dalla sola condizione sperimentale. Questo design confronta i gruppi definiti da `condition` assumendo che i campioni siano indipendenti rispetto al confronto di interesse.

Se esistono fattori tecnici o biologici che influenzano sistematicamente i conteggi, questi devono essere inclusi nel design. Per esempio
```r
design = ~ batch + condition
```
stima l’effetto della condizione dopo aver controllato per il batch. In questo caso `batch` assorbe una fonte di variazione non biologicamente interessante, mentre `condition` rappresenta l’effetto che si vuole testare.

Nei disegni **paired** o a misure ripetute, campioni diversi non sono indipendenti perché condividono lo stesso soggetto, individuo, linea cellulare o unità sperimentale. In questi casi il design deve includere un termine che rappresenta il blocco di appartenenza:
```r
design = ~ subject + condition
```
Il termine `subject` modella le differenze di baseline tra unità sperimentali, mentre `condition` stima il cambiamento associato alla condizione all’interno della stessa unità.

Ignorare la struttura paired usando solo
```r
design = ~ condition
```
su dati appaiati porta il modello a trattare campioni collegati come gruppi indipendenti. La variabilità tra soggetti finisce quindi nella variabilità residua o può confondere l’effetto della condizione, riducendo potenza statistica e aumentando il rischio di interpretazioni scorrette.

Design comuni:
- `~ condition`: confronto semplice tra gruppi indipendenti
- `~ batch + condition`: confronto tra condizioni controllando per un batch tecnico
- `~ subject + condition`: disegno paired o a misure ripetute
- `~ subject + batch + condition`: disegno paired con batch, utilizzabile solo se batch e condizione non sono confusi

L’ordine dei termini è rilevante per l’interpretazione dei coefficienti e del risultato di default: la variabile di interesse, spesso `condition`, viene normalmente posta alla fine della formula.

Una volta stimata la dispersione, viene fittato il GLM NB e si procede al [[Test Statistici|test statistico]] sui coefficienti $\beta_g$,  Il test valuta tipicamente l’ipotesi:
$$H_0: \beta_{g,\text{condizione}} = 0$$
cioè assenza di effetto della condizione sperimentale. Nel caso del **Wald test**, la statistica è: $$Z_g=\frac{\hat\beta_g}{\mathrm{SE}(\hat\beta_g)}$$dove l’errore standard dipende dalla dispersione stimata $\hat\theta_g$. 

Interpretazione:
- $\theta_g$ → livello di rumore biologico
- $\beta_g$ → effetto della condizione
- il test verifica se l’effetto stimato è grande rispetto alla variabilità osservata
L’output comprende log-fold change stimati, statistiche di test e [[Test Statistici - p-value|p-value]] per ciascun gene. Poiché vengono effettuati migliaia di test simultanei, i [[Test Statistici - p-value|p-value]] sono corretti per test multipli controllando il [[FDR|False Discovery Rate]] tramite la procedura di [[Test Statistici - Benjamini-Hochberg correction|Benjamini–Hochberg]].


Per analisi esplorative e rappresentazioni geometriche della matrice geni × campioni, DESeq2 fornisce trasformazioni opzionali come **rlog** e **VST** che stabilizzano la varianza e riducono la dipendenza dalla media. Tali trasformazioni producono una rappresentazione con varianza approssimativamente costante, rendendo più interpretabili [[Principal Component Analysis (PCA)|PCA]], [[Data analysis - Clustering|clustering]] e [[Distanza euclidea|distanze euclidee]] tra campioni.
Queste trasformazioni non sono utilizzate per il test di differential expression, che resta basato sui conteggi nel modello [[Variabili aleatorie Notevoli - Negative Binomial|NB]].
![[IMG -DESeq2 strategie di normalizzazione.png]]
