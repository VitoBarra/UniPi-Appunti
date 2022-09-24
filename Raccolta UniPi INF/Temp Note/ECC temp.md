2022-09-23:
[[Funzioni]]: può avere 


F(x) è
T-Calcolabile
Whille-Calcolabile. $F(n) = m \iff (c,\sigma) \rightarrow^*$


## calcolare funzioni in 2 variabili:
Per calcolare una funzione in 2  variabili basta immaginarti un quadrante di un paiano e tirarlo con dei quadrati. Oggi quadrato puo essere associato un valore calcolato con una formula dove prendi gli indici si ha 
$$ (x,y)\rightarrow $$
Per la best e di noumero non naturai quindi rendere robusto la nazione di calcolabilita sui dat

1. Codifica $A$ in $N$
2. Calcolo $N \rightarrow N$
3. Decodifico il risultato $N \rightarrow A$

Quidni ho bisogno di una funzione di codifica di A che si a [[Funzioni#Biunivocita|Biunivoca]] Quindi invertibile in modo da poterne fare la Decodifica 



T-calcolabilita = While-calcolabilita 


### difetti della nozione di calcolabilita
Funzioni come quella che dico se la  [[Congettura Goldbach]] è vera o falsa 
$$f(n)= sistema 1 se verra 0 se falsa$$ sono calcolabili dalla macchina che da sempre uno e quella che d sempre zero ma per ora non si puo sapere come è fatta questa macchinina. Infatti una definizione proposta e altenativa e quella dove la calcolabilita implica la costruzionabilita delle soluzioni. In questo modo questa funzione non rientrerebbe nelle funzioni calcolabili perché non la posso costruire.

>[!info] ExtraNote
Le $\lambda-$[[Lambda calcolo||espressione]]  è del tipo $\lambda x.\lambda y.yx$ 
### Funzioni Ricorsive primitive
 E’ la classe di funzioni $C$ conn
1. (zero) $\lambda x_1,\dots,x_n.0$
2. (succ) $\lambda x.x+1$
3. (identità o proiezione ) $\lambda x_1,\dots,x_n.x_i$
E sono [[Insieme Chiuso |chiuse]] riaspettò a 
 4. (composizione )
 5. (Ritorsione Primitiva)
	 1.  Se $h \in C$ È una funzione $k+1$ variabili $g \in C$ é una funzione in $k-1$ variabili m allora appartiene a $C$ anche la funzione $f$ in $k$ variabili definita da 
	 
	  $$
	  \begin{cases}
		    f(0,x_2,\dots,x_k) =  g(x_2,\dots,x_k) \\
		    f(x_1+1,x_2,\dots,x_k) =h(x_1,f(x_1,x_2,\dots,x_k)x_2,\dots,x_k) 
    \end{cases}
	 $$
	 