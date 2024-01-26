l idea e di fa giocare più intelligenze artificiali [[Machine Learning (ML)|allenate con modelli]] diversi a giochi di carte come 
1. 3 sette
2. briscola 
3. scopa
4. scopone
5. burraco
6. scala quaranta
7. rubamazzo

1. cactus tedesco

va implementato prima il mondo di gioco per ogni gioco

i modelli andranno fatto in ottica di classificazione delle carte da giocare. 
va fatto un approfondimento su [[Reti Neurali (NN)|neural network]]


voglio studiare anche il transfer delle abilita tra giochi simili e completamente diversi 

implementazione delle azioni come ipotetico range di azioni codificate in $\mathbb{N}$ 
per azioni doppie con dati si usano Tuple (n,Dato)
problema della codifica di input e output, va capito come codificare le azioni anzi il set di azioni per turno

una idea sarebbe discretizzare le mosse in 100 possibili interi codificando poi output come liste di mosse di dimensione arbitraria.
- Problema di regolarizzazione, vanno penalizzate mosse troppo lunghe? va penalizzato il fare una sola mossa?, dipende dal gioco, l intelligenza puoi imparare da se questa cosa (da capire come)


### input
gli input della rete saranno
1. lo stato del tavolo
	1. esistenza di pile
		1. pesca
		2. scarti
	2. carte a terra se presenti
	3. numero di player
	4. numero di carte in mano ad ogni player
2. numero di turni giocati
3. 


risorse per [catastrophic forgetting](https://ai.stackexchange.com/questions/14117/how-is-transfer-learning-used-to-mitigate-catastrophic-forgetting-in-neural-netw) ovvero cosa succede se cerco di sfruttare il transfer.


[reinforment learning](https://www.youtube.com/watch?v=NFo9v_yKQXA&list=PLzvYlJMoZ02Dxtwe-MmH4nOB5jYlMGBjr)




https://openai.com/research/openai-five-defeats-dota-2-world-champions