---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Operazione di convoluzione
---
La __convoluzione__ è un'[[Operazioni algebriche|operazione matematica]] solitamente denotata con $*$.

L'idea generale di questa operazione è quella di calcolare una media pesata di una funzione $f$ utilizzando i pesi definiti da un'altra funzione $g$. Formalmente, la **convoluzione discreta** tra due funzioni $f$ e $g$ è definita come: $$(f * g)(n) = \sum_{i=-\infty}^{\infty} f(i) g(n-i)$$ Mentre, nella forma continua si sostituisce la somma con un [[Integrali|integrale]] ed è quindi data da: $$
(f * g)(t) = \int_{-\infty}^{\infty} f(\tau) g(t - \tau) d\tau
$$

La convoluzione possiede anche alcune proprietà fondamentali, tra cui:
- [[Proprietà del operazioni - Commutativita|Commutatività]]: $f * g = g * f$
- [[Proprietà del operazioni - Associativa|Associatività]]: $f * (g * h) = (f * g) * h$
- [[Proprietà del operazioni - Distributività|Distributività]]: $f * (g + h) = (f * g) + (f * h)$
- __[[Operazioni - Elemento Neutro o identita|Elemento neutro]]__: la convoluzione con la delta di Dirac o con l'impulso unitario lascia invariata la funzione originale.

Questa **operazione** può essere generalizzata prendendo in considerazione più dimensioni. Ad esempio, nel caso discreto 2D si ottiene una doppia somma: $$(f * g)(i,j) = \sum_m \sum_n f(m,n) g(i-m, j-n)$$ mentre nel caso continuo si sostituiscono le somme con [[Integrali|integrali]]: $$(f * g)(x,y) = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f(\xi,\eta) g(x-\xi, y-\eta) d\xi d\eta$$ Il significato però resta lo stesso: in ogni posizione si misura la sovrapposizione locale tra il segnale e una versione traslata del kernel.

#### Convoluzione continua
Se si vuole visualizzare la **convoluzione continua**, si può immaginare di far scorrere una delle due funzioni sull'altra. In ogni posizione si moltiplicano punto per punto le due curve e si calcola l'area totale del prodotto:
$$
(f * g)(t) = \int_{-\infty}^{\infty} f(\tau) g(t-\tau) d\tau
$$
Al variare di $t$, cambia la sovrapposizione tra $f(\tau)$ e la versione traslata di $g(t-\tau)$; il valore della convoluzione in quel punto è proprio l'area ottenuta da questa sovrapposizione pesata.

Se il nucleo $g$ è una [[funzioni|funzione pari]], cioè soddisfa $g(-\tau)=g(\tau)$, allora la convoluzione coincide con la correlazione. In questo caso la visualizzazione è ancora più intuitiva, perché il "ribaltamento" del kernel non cambia la sua forma.
![[GIF - Convolution_of_box_signal_with_itself2.gif]]

Un'altra intuizione utile è vedere la convoluzione come un'operazione di "spalmatura" o diffusione. Se $g(\tau)=\delta(\tau)$, cioè è un impulso ideale, allora la convoluzione restituisce semplicemente $f(t)$. Se invece $g$ è un impulso più largo, l'uscita diventa una versione più liscia e distribuita di $f$: l'informazione locale viene mediata sul supporto di $g$.
![[GIF - Convolution_of_spiky_function_with_box2.gif]]

### Approfondimento caso discreto 2D
Nel caso discreto bidimensionale le funzioni non dipendono più da un solo indice, ma da una coppia di indici. Si può quindi pensare a $f(i,j)$ come a una tabella o a una matrice di valori definita su una griglia, mentre $g(i,j)$ rappresenta un secondo segnale bidimensionale, spesso più piccolo, che agisce come kernel.

La definizione è: $$(f * g)(i,j) = \sum_m \sum_n f(m,n) g(i-m, j-n)$$ Fissata la posizione $(i,j)$, il valore $(f * g)(i,j)$ si ottiene quindi moltiplicando i valori del segnale per i corrispondenti valori del kernel traslato e ribaltato, e sommando tutti i contributi locali.

L'immagine seguente rende bene questa idea: si prende una piccola finestra dell'input, la si combina con il kernel e si ottiene un singolo valore nell'output. Ripetendo lo stesso procedimento su tutte le posizioni ammissibili si costruisce l'intera matrice di uscita.
![[IMG - visualizzazione del operazione di convoluzione su pixel.png]]

Un modo equivalente di leggerla è questo: il valore $(f * g)(i,j)$ misura quanto il segnale $f$ e una copia traslata e ribaltata di $g$ si sovrappongono in quella zona della griglia. Se il kernel è concentrato su un intorno piccolo, la convoluzione in ogni punto dipende solo dai valori vicini, e per questo l'operazione preserva la località.

Dal punto di vista strutturale, il passaggio da 1D a 2D non cambia la natura dell'operazione, ma solo il dominio su cui viene effettuata. La convoluzione resta una somma pesata locale; cambia il fatto che ora la località è definita rispetto a un intorno bidimensionale anziché lungo una sola direzione.

Due concetti importanti nella convoluzione discreta 2D sono inoltre il __padding__ e lo __stride__. Il padding consiste nell'aggiungere valori artificiali, tipicamente zeri, attorno alla griglia originale prima di applicare il kernel. Questo serve a controllare il comportamento ai bordi e a evitare che l'output si restringa applicando la convoluzione. Senza padding, infatti, il kernel può essere centrato solo sulle posizioni per cui resta interamente dentro il segnale.

Lo stride, invece, indica di quanto il kernel viene spostato a ogni passo lungo ciascuna dimensione. Con stride $1$ il filtro visita tutte le posizioni adiacenti; con stride maggiore di $1$ salta alcune posizioni, producendo un'uscita più piccola e realizzando quindi una forma di sottocampionamento. Dal punto di vista matematico, **stride e padding** non cambiano la natura dell'operazione di convoluzione, ma modificano il modo in cui il kernel viene applicato sulla griglia. La visualizzazione seguente mostra i casi più comuni, evidenziando in particolare come cambiano dimensioni e posizione delle finestre applicate all'input.

![[GIF - convoluzione padding stride.gif]]

Un'osservazione utile è che la stessa logica si può applicare anche nel verso opposto, quando si vuole passare da una griglia più piccola a una più grande. In questo caso non si introduce una nuova operazione di natura diversa: si sta ancora sfruttando la struttura della convoluzione, ma su un input opportunamente trasformato. In particolare, nel caso con stride maggiore di $1$, si può interpretare il procedimento come una riespansione della griglia in cui vengono inseriti zeri tra gli elementi, seguita poi da una normale convoluzione. Per questo, in ambito di calcolo numerico e deep learning, si parla di __transpose convolution__ o convoluzione trasposta; matematicamente, però, non è corretto intenderla come la vera inversa della convoluzione, perché l'informazione eventualmente persa nel passaggio in avanti non è in generale ricostruibile in modo esatto.

Anche in questo caso il principio locale non cambia: un valore in ingresso viene distribuito nelle posizioni vicine secondo i pesi del kernel, producendo una griglia più grande. La visualizzazione seguente mostra i casi più comuni di questa applicazione della stessa idea convolutiva.

![[GIF - convoluzione trasposta padding stride.gif]]