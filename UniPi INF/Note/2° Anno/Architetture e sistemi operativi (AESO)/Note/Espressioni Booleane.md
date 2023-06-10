---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Espressioni Booleane
---

## Simbologia

- + : OR Logico
- $\cdot$  : AND Logico
- $\overline{A}$ : negazione di un letterale

## Terminologia

- **letterale**: ****è una variabile o un suo complemento
- **Implicante o** somma logica : una serie di variabili in **AND** detto anche
- **mintermine**: tutti gli ingressi di una rete in **AND**
- **implicato o** somma logica : una serie di variabili in **OR**
- **Maxtermine**: tutti gli ingressi di una rete in **OR**



### Ordine

Si esegue con l usuale ordine aritmetico, il **NOT** ha la precedenza poi l **AND** e in fine l **OR**

### Scrittura canonica

partendo da una tabella di verità la sua scrittura canonica è fatta da somme di prodotti partendo a scrivere dal primo min termine con il valore è 1

![[UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 14 1.png]]

$$
Y=\overline{A}B+AB
$$

### Postulati

![[Untitled 1 4 1.png]]
![[Untitled 2 2 1.png]]

![[Untitled 3 2 1.png]]

## Riducibilità

’espressione può essere semplificata come Y = B. In questo caso, la semplificazione poteva essere facilmente dedotta guardando la tabella delle verità.
Tuttavia, in generale sono necessari diversi passaggi per semplificare espressioni più complesse.
Il principio base per semplificare equazioni in forma somma di prodotti è
combinare i termini utilizzando la relazione PA + PA- = P, dove P rappresenta
un implicante qualsiasi. Quanto si può semplificare un’espressione? Si definisce un’espressione in somma di prodotti come minima se utilizza il minor
numero possibile di implicanti. Se si confrontano espressioni con lo stesso
numeri di implicanti, l’espressione minima è quella che usa il minor numero
possibile di letterali.
Un implicante è detto implicante primo se non può essere combinato
con nessun altro elemento all’interno dell’espressione per formare un nuovo
implicante con un numero minore di letterali. In un’espressione minima, gli
implicanti devono essere tutti implicanti primi, altrimenti è possibile combinarli ulteriormente per diminuire il numero di letterali.
