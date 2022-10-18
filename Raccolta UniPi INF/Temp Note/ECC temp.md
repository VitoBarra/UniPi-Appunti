### difetti della nozione di calcolabilita
Funzioni come quella che dico se la  [[Congettura Goldbach]] è vera o falsa 
$$f(n)= sistema 1 se verra 0 se falsa$$ sono calcolabili dalla macchina che da sempre uno e quella che d sempre zero ma per ora non si può sapere come è fatta questa macchinina. Infatti una definizione proposta e alternativa e quella dove la calcolabilità implica la costruzionabilita delle soluzioni. In questo modo questa funzione non rientrerebbe nelle funzioni calcolabili perché non la posso costruire.

>[!info] ExtraNote
Le $\lambda-$[[Lambda calcolo|espressione]]  è del tipo $\lambda x.\lambda y.yx$ 

2022-09-30:
$$\mathcal{F}=formalismo \begin{cases} MdT \\ for/while \\ Ricorsive Primitive/RicorsiveGenerali\end{cases}$$
$$\mathcal{F}\iff\mathbb{N} $$

Se $\mathcal{F}$ rappresenta solo funzioni totali allora _NON_ le può rappresentare tutte

## Dimostrazione

$$\mathcal{B}(x)= A_x(x)+1 \\ Godel(B) $$
$$A_i(i)=B(i)=A_i(i)+1$$


$\phi_n$ è la funzione calcolabile da $M_n$ una volta fondata un esecuzione 
$$\phi_i(i)=\phi_i(i) + 1$$

Enumerazione effettiva parte dalla numerazione canonica di [[godel]] 

Per numerare gli algoritmi devo considerare quello che sono non quello che fanno


---

## Classe delle funzioni ricorsive
La classe delle unzioni $u$-ricorsive è la minima classe che rispetta le regole della [[ECC temp#Funzioni Ricorsive primitive|ricorsione]] primitiva 
- lo 0 
- il successore 
- la proiezione
Ed è chiusa per
- composizione
- Ricorsione primitava


## Tedi di calcolabilita
Le funzioni intuitivamente calcolabili ovvero hanno una procedura per calcolarli.
Sono tutte e sole le t-calcolabili.



  Linguaggio di programmazione non sono Turing complete perche sono limitati dalla memoria e dal tempo. A d’esempio il computer in cui gira il linguaggio non ha abbastanza memoria per memorizzare i dati intermedi.




# teoremi
## Teorema 1
Le funzioni calcolabili sono tante quanto i numeri naturali perche per ogni funzione da calcolare esiste una macchina di Turing, e le macchine di turing sono infinite e tante quanto i numeri naturali.
Esistono funzioni non calcolabili.
FIssiamo un enumerazione effettiva
### padding lemma
Ogni $\Phi_n$ ha $\# \mathbb{N}$ indici

### Teorema 3




2022-10-06:

Tesi di Church-Turing :
Tutte l e funzioni si dicono calcolabili se si possono calcolare con una macchina di Turing. 


L $n-$sima a$M_n$ calcola $\phi$ 


## Teorema Forma Normale

$$\large\exists T,U |  \forall i,x \phi_i(z) = U(\eta y.T(i,x,y)) $$
 >[!note] 
 >- il linguaggio While è espressivo quantoi$\phi$
 >- il formalismo delle ricorsi e generali è espressivo quanto  $\phi$
 >
### Dimostrazione
BHO


## Teorema di enumerazione (macchia di turing universale)

$$\exists x.\forall i,x \phi_i(x)=\phi(i,x)$$



### Dimostrazione
$$\phi_i(x) = U(\upsilon y.T(i,x,y)) \overset{C-T}{=}  \phi_z(i,z) $$




## Teorema Del paragrafo o $\large S^m_n$
$$\exists s \text{ una finzione inniettiva} | \forall i,x,y.\lambda y.\phi_i(x,y)= \phi_{S(i,x)}(y)$$





## Macchina di turing universale
Si parte dal [[Teorema di enumerazione]]
p