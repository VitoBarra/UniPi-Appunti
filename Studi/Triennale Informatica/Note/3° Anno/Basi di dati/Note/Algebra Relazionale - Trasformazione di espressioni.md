---
type: nota
course: Data Base
topic: 
tags:
  - FDI
Parent MOC: "[[Data Base (DB)]]"
---
# Algebra Relazionale - Trasformazione di espressioni

---
#### Proprietà delle operazioni 
Un’espressione dell’algebra relazionale puo essere trasformata in un’altra equiva- `
lente sfruttando alcune proprieta degli operatori. Queste trasformazioni sono utili `
perche possono ridurre di ordini di grandezza il costo di esecuzione delle espressioni ´
(riscrittura algebrica).
Si consideri la rappresentazione di un’espressione algebrica come un albero le cui fo￾glie siano le relazioni e i nodi interni sono gli operatori dell’algebra; i figli di un nodo
interno N sono gli operandi dell’operatore associato al nodo N (si veda la Figura 4.12).
![[IMG_1059.jpeg]]

L’idea alla base della riscrittura algebrica e di anticipare l’applicazione degli operatori `
di proiezione e restrizione rispetto al prodotto e alla giunzione (spostamento verso le
foglie della proiezione e restrizione), in modo da ridurre la dimensione dei risultati
intermedi. Poiche la restrizione ´ e l’operatore che in generale produce una relazione `
con un numero di ennuple inferiore rispetto a quello della relazione a cui viene ap￾plicato, le proprieta pi ` u utili dell’algebra relazionale sono quelle che consentono di `
anticipare l’operatore di restrizione. E anche utile anticipare l’operazione di proiezio- `
ne rispetto al prodotto e alla giunzione, perche una proiezione riduce la dimensione ´
delle ennuple dell’operando ed elimina eventuali ennuple uguali dal risultato.
Indicando con E un’espressione dell’algebra relazionale, esempi di regole su cui si
basa la riscrittura sono:
1. Raggruppamento di restrizioni
σφX
(σφY
(E)) = σφX ∧ φY
(E),
dove σφX
e l’operatore di restrizione con condizione sull’insieme di attributi ` X.

2. Commutativit`a della restrizione e della proiezione
πY(σφX
(E)) = σφX
(πY(E)), se X ⊆ Y.
Se la condizione interessa attributi X 6⊆ Y, allora vale:
πY(σφX
(E)) = πY(σφX
(πXY(E))).
3. Anticipazione della restrizione rispetto al prodotto e alla giunzione
σφX
(E1 × E2) = σφX
(E1) × E2,
σφX
(E1 ./ E2) = σφX
(E1) ./ E2,
se X sono attributi di E1.
σφX ∧ φY
(E1 × E2) = σφX
(E1) × σφY
(E2),
σφX ∧ φY
(E1 ./ E2) = σφX
(E1) ./ σφY
(E2),
se X sono attributi di E1 ed Y sono attributi di E2.
σφX ∧ φY ∧ φJ
(E1 × E2) = σφX
(E1)
./
φJ
σφY
(E2),
se X sono attributi di E1, Y sono attributi di E2 e φJ e una condizione di giunzione. `
4. Raggruppamento di proiezioni
πZ(πY(E)) = πZ(E),
dove πZ e l’operatore di proiezione sull’insieme di attributi ` Z, e Z ⊆ Y in espres￾sioni ben formate.

5. Eliminazioni di proiezioni superflue
πZ(E) = E,
se Z sono gli attributi di E.
6. Anticipazione della proiezione rispetto al prodotto e alla giunzione
πXY(E1 × E2) = πX(E1) × πY(E2),
πXY(E1
./
φJ
E2) = πX(E1)
./
φJ
πY(E2),
dove X sono attributi di E1, Y sono attributi di E2 e φJ
la condizione di giunzione
con attributi J ⊆ XY.
πXY(E1
./
φJ
E2) = πXY((πXXE1
(E1)) ./
φJ
(πYXE2
(E2))),
dove X sono attributi di E1, Y sono attributi di E2, XE1
sono gli attributi di giunzione
di E1 che non sono in XY e XE2
sono gli attributi di giunzione di E2 che non sono
in XY.

7. Commutativit`a del prodotto e della giunzione
E1 × E2 = E2 × E1
E1
./
φJ
E2 = E2
./
φJ
E1

8. Associativit`a del prodotto e della giunzione
(E1 ./ E2) ./ E3 = E1 ./ (E2 ./ E3),
(E1
./
φJ1
E2)
./
φJ2 ∧φJ3
E3 = E1
./
φJ1 ∧φJ3
(E2
./
φJ2
E3),
dove φJ2
contiene attributi solo di E2 e E3. Se mancano le condizioni di giunzione,
ne segue che anche il prodotto × e associativo. `
9. Commutativit`a degli operatori insiemistici
E1 ∪ E2 = E2 ∪ E1
E1 ∩ E2 = E2 ∩ E1
E1 − E2 6= E2 − E1
10. Associativit`a degli operatori insiemistici
(E1 ∪ E2) ∪ E3 = E1 ∪ (E2 ∪ E3)
(E1 ∩ E2) ∩ E3 = E1 ∩ (E2 ∩ E3)


11. Anticipazione della restrizione rispetto agli operatori insiemistici
σφX
(E1 − E2) = σφX
(E1) − σφX
(E2)
l’equivalenza vale anche sostituendo − con ∪ o ∩. Mentre
σφX
(E1 − E2) = σφX
(E1) − E2
vale anche sostituendo − con ∩, ma non con ∪.
12. Anticipazione della proiezione rispetto agli operatori insiemistici
πX(E1 ∪ E2) = (πX(E1)) ∪ (πX(E2))


Esistono altre regole di riscrittura algebrica di espressioni che usano il _raggruppamento_, 
1. _l’anticipazione della proiezione rispetto al raggruppamento_:$\sigma_{\phi}(_A\gamma_F(E)) = _A\gamma_F(\sigma_\phi(E))$, se $\phi$ usa solo attributi in $A$.

#### Algoritmo
Un possibile algoritmo di riscrittura algebrica procede quindi secondo i seguenti
passi:
1. Si anticipa l’esecuzione delle restrizioni sulle proiezioni usando la regola 2 da de￾stra verso sinistra (in tutti gli altri casi le regole verranno usate nell’altra direzione);
dato che la regola e usata in questa direzione, vale sempre la condizione ` X ⊆ Y.
2. Si raggruppano le restrizioni usando la regola 1.
3. Si anticipa l’esecuzione delle restrizioni sul prodotto e sulla giunzione usando la
regola 3.
4. Si ripetono i tre passi precedenti fino a che e possibile. `
5. Si eliminano le proiezioni superflue usando la regola 5.
6. Si raggruppano le proiezioni usando la regola 4.
7. Si anticipa l’esecuzione delle proiezioni rispetto al prodotto e alla giunzione usando
ripetutamente la regola 2, ma solo nel caso in cui E e un prodotto o una giunzione, `
e la regola 6.

In generale, quindi, il risultato di questo algoritmo e un’espressione in cui la restri- `
zione e la proiezione sono eseguite il piu presto possibile, e la restrizione ` e anticipata `
rispetto alla proiezione. In particolare, nel caso di espressioni con una sola giunzione,
l’espressione ottimizzata ha la forma:
πX1
(πX2
(σφY2
(R)) ./ πX3
(σφY3
(S))).

![[IMG_1060.jpeg]]

