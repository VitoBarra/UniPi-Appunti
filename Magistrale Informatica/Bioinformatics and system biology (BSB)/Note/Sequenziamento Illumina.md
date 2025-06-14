---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# Sequenziamento Illumina
---
l **Illumina sequencing** è una tecnologia di [[Tecnologie di sequenziamento|tecnologia di sequenziamento]] di la **seconda generazione**.  si basa su procedure che permettono l’analisi parallela di un numero molto elevato di frammenti, organizzati in matrici dense e uniformi. 
per fare ciò l l’intero genoma viene sottoposto a **sonificazione** una precudura che spezza l intero DNA in  frammenti distribuiti casualmente nell’intervallo 50–500 nt;
![[IMG - sonificazione del DNA.png]]
Collettivamente i frammenti costituiscono la **libreria**, e ciascuno di essi viene **immobilizzato** su un supporto solido a matrice![[IMG - libraria di DNA imobilizata.png]] L’immobilizzazione avviene mediante **ibridazione** degli adattatori a oligonucleotidi complementari fissati su vetro; la sequenza dell’adapter, identica in tutte le molecole della libreria, permette l’innesco della polimerizzazione ed è facilmente rimovibile nelle fasi di analisi ![[IMG - immobilizazione.png]]
La disposizione ordinata dei frammenti sul supporto consente la successiva **amplificazione della libreria**, generando insiemi di copie identiche per ciascuna molecola immobilizzata ![[IMG - aplificazione con PCR.png]]. Queste copie si legano a molecole oligonucleotidiche adiacenti a quelle inizialmente ibridate, formando cluster che separano fisicamente gli ampliconi e permettono reazioni di sintesi simultanee su un gran numero di gruppi clonali.

La sintesi si basa sull’incorporazione ciclica di nucleotidi marcati con terminatore reversibile, rilevati tramite fluorescenza e processati per ricostruire la successione delle basi. 
![[IMG - illumina sequencing.png]]
La lettura raggiunge tipicamente circa 300 bp per frammento, e la parallelizzazione di un numero molto elevato di cluster consente di ottenere quantità di dati nell’ordine di migliaia di megabasi per singola procedura.

una volta fatte le letture si deve fare la [[Problema Sequence Assembly|sequence assembly]] che dara la sequenza finale 

Il materiale video ![](https://www.youtube.com/watch?v=fCd6B5HRaZ8) illustra in modo completo la sequenza delle operazioni, comprendendo ibridazione, amplificazione clonale e sintesi con rilevazione ottica ciclica, disposte per garantire coerenza dei segnali e riduzione dell’errore di incorporazione.


