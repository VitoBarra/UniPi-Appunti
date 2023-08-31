---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Protocollo di identificazione Fiat-Shamir
---
il Protocollo di _Fiat-Shamir_ è un protocollo di [[Protocolli di Identificazione|identificazione]] basato su  [[Protocolli Zero Knowledge|Protocolli Zero Knowledge]].

## Protocollo
_Sia_ $P$ (provider) l utente che vuole autenticarsi e $V$(verifier) il sistema che richiede l autenticazione il protocollo segue come:
$P$ sceglie $n=pq$ con $p,q$ [[Numeri primi]] e un intero positivo $s<n$. Calcola $t=s^{2} \mod  n$ e rende pubblica la coppia $\langle n,t\rangle$ e tiene segreta la terna $\langle p,q,s\rangle$, nessuno di questi valori può essere calcolato in [[Complessita|tempo polinomiale]] da $n$ e $t$. 
Da qui il protocollo precede come 
1. $V$ _chiede_ a $P$ di iniziare un iterazione
2. $P$ _genera_ un intero random $r<n$
	  _calcola_ $u =r^{2} \mod  n$
	  _comunica_ $u$ a $V$
3. $V$ _genera_ un numero binario random $e$
	 _comunica_ $e$ a $P$
4.  $P$ _calcola_ $z=rs^{e}\mod n$
	_comunica_ $z$ a $V$
5. $V$ _calcola_ $x=z^{2}\mod n$
	_if_ vai al passo 1
	_else_ blocca il protocollo senza identificare $P$

per renderci conto che questo è un [[Protocolli Zero Knowledge|protocollo zero-Knowledge]] devono essere rispettate le 3 proprietà e quindi le dimostriamo come segue
1. _Completezza_ 
	Se P è _onesto_ la condizione $x = ut^{e} \mod  n$ del passo 5 è _sempre verificata_: infatti 
	- per $e = 0$ si ha $x = r^{2} \mod n$ e $ut^{e} \mod n = r^{2} \mod n$; 
	- per $e = 1$ si ha $x = r^{2}s^{2} \mod n$ e $ut^{e} \mod n = r^{2}s^{2} \mod n$.
	 Dunque $V$ accetta l’asserzione di $P$ per qualunque valore di $k$.
2.  _Correttezza_:
	 Se $P$ è disonesto (cioè intende farsi identificare come un altro utente) e conosce il valore di $t$ che è pubblico ma non conosce il valore di $s$, può tentare di ingannare $V$ prevedendo i valori di $e$ che questi genererà al passo 3 del protocollo. 
	 Cosi, al passo 2, $P$ invierà a $V$
	-  il valore $u = r^{2} \mod n$ se prevede di ricevere $e = 0$, 
	-  il valore $u = r^{2}/t \mod n$ se prevede di ricevere $e = 1$
	In entrambi i casi invierà poi a $V$ lo stesso valore $z = r$ al passo 4.
	Se la previsione di $P$ su $e$ è corretta, al passo 5, per entrambi i valori di $e$, V scoprirà che $x = ut^{e} \mod n = r^{2} \mod n$ e accetterà l’iterazione; ma se la previsione è sbagliata la relazione non sarà verificata e sarà scoperto l’inganno. La proprieà di correttezza segue dall’osservazione che, poichè e viene generato a caso, le previsioni di $P$ su e sono corrette con _probabilità_ $1/2$. 
3.  _Conoscenza-Zero_:
	La dimostrazione che $V$ non scopre nulla su $P$ salvo la sua identità è molto complessa. Come per tutte le dimostrazioni di _conoscenza-zero_ essa si basa sull’esistenza di un simulatore (Macchina di Turing) probabilistico disponibile a qualunque _verifier onesto_ o meno, che, senza accesso al _prover_, può costruire una falsa sequenza di iterazioni tra $P$ e $V$ che con alta probabilità coincide con l’esecuzione di un protocollo corretto di accettazione. Il non accesso a $P$ garantisce che $V$ non possa acquisire alcuna informazione su di esso.

Notiamo infine un’altra caratteristica interessante dei _protocolli zero-knowledge_. Dopo che un onesto $V$ ha terminato i suoi scambi con un onesto $P$, non può ripetere a un terzo attore $T$ (per esempio a un giudice) la dimostrazione di veridicità dell’asserzione di $P$. In effetti $V$ potrebbe eseguire una registrazione di tutti i passi del protocollo e mostrarla a $T$; ma questa registrazione potrebbe essere stata costruita ad arte da un _disonesto_ $V$ senza alcuna interazione con $P$, simulando il funzionamento di un protocollo truccato ove $P$ conosce a priori le scelte (ora non) random di $V$ e si comporta in conseguenza. Nell’esempio di identificazione sopra descritto $V$ potrebbe costruire una falsa registrazione in cui $P$ conosce a priori i valori di $e$.



