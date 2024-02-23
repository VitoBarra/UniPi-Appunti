---
Subject: Elementi di calcolabilita e complessita
topic: nota
tags: ECC
---

Prev: [[Elementi di Complessità e Calcolabilità (ECC)]]

# Nozione di Calcolabilità
---
la nazione di _calcolabilità_ esprime le funzioni intuitivamente calcolabili. se sono intuitivamente calcolabili significa che esiste un [[Algoritmi|Algoritmo]] per calcolare ed esistono molteplici formalismi che permettono di esprimere algoritmi questo sono detti modelli di calcolo: [[Macchina di Turing ]], [[Funzioni Ricorsive Primitive]],[[Funzioni Ricorsive Generali]], $\lambda-$[[Lambda calcolo|calcolo]], Random access machine, Algoritmi di markov, [[Grammatiche generali]], [[linguaggi di programmazione]].


1. ) Un algoritmo è costituito da un insieme __finito__ di istruzioni;
2. ) Le istruzioni possibili sono in numero finito e hanno un effetto limitato su dati discreti, esprimibili in maniera finita ovvero (x=y) posso cambiare y in modo infinito  ma e rappresentato finitamente (2 termini);
3. ) Una computazione è eseguita per passi discreti (singoli), ciascuno dei quali impiega un tempo finito;
4. ) Ogni passo dipende solo dai precedenti e da una porzione finita dei dati, in modo deterministico (ciò è senza essere soggetti ad alcuna distribuzione [[Definizione di Probabilita|probabilistica]] non banale);
5. ) non c’ e limite al numero di passi necessari all’esecuzione di un algoritmo, ne alla memoria richiesta per contenere i dati (finiti) iniziali, intermedi ed eventualmente finali (i numero dei passi è finito solo se prima o poi si raggiunge uno stato finale o c è uno stallo quindi quando non esiste una prossima istruzione da eseguire).


>[!note]
>Sotto queste ipotesi, tutte le formulazioni fin ad ora sviluppate sono equivalenti e si postula che lo saranno anche tutte le future

>[!info]  TEOREMA 
>non esiste nessun formalismo che esprime tutte e sole le funzioni totali e calcolabili
>Dimostrato con [[Diagonalizzazione]]
