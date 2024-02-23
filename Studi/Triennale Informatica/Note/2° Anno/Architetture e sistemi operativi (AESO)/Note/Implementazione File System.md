---
Subject: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Implementazione File System
---


il file system è un problema di traduzione dai i dati human-readable che vuole offrire e i blocchi fisici del [[Dispositivi per Memoria permanente|device di storage]],

per risolvere il problema il file system deve avere

- [[Directories dati nominati|Directory]]: ovvero la struttura dati che mappa nomi di file ad uno specifico numero di file. di solito sono uno speciale file che con tiene questa mappatura

- index structure: la struttura dati che mappa il file number ad un blocco, questa struttura dati deve essere persistente sul disco ed è spesso implementata con una struttura ad albero per motivi di efficienza

![[Untitled 42.png]]

- **mappe dello spazio libero**: strutture dati per sapere quali blocchi sono utilizzati da file e quali no, si devono almeno sapere quali blocchi sono libero per poter espandere i file o crearne di nuovi, si possono sfruttare queste informazioni per mettere i dati almeno in una zona vicina nel disco per motivi d efficienza un esempio è una bit map salvata in modo persistente
- **euristiche di località**:  le [[Directories dati nominati |directory]] e l index structure permettono al file system di allocare sempre i dati che devono essere immagazzinati se c è dello spazio libero, mentre le mappe dello spazio libero permettono di trovarne se c è ne e di creare politiche per allocare blocchi di memoria dello stesso fai  o di file asciati vicini.