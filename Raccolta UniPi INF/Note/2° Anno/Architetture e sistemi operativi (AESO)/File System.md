---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# File System
---


il file system è un astrazione del sistema operativo su i device di storage fisici che offre dei dati che sono

- **Persistenti**: ovvero vengono mantenuti finche non viene richiesta la cancellazione
- **Nominati**: ovvero posso essere accessi  e ricercato in un formato Human-readable.

e deve provvedere a più aspetti che sono

- **Performance**: ovvero deve dare delle performance ragionevoli gestendo le limitazioni imposte dai [[Storage device|device di storage fisici]] . questo è fatto garantendo una buona località spaziale
- **Flessibilità**: la possibilità di essere usati in contesti variegati, quindi deve gestire sia file piccoli che grandi che temporanei ecc.
- **Persistenza**: il file system deve mantenere sia i dati del utente che quelle delle strutture dati del file system stesso sul device fisco in modo che questi persistano anche in caso di crash o banale spegnimento
- **Affidabilità**: deve mantenere i dati anche in casi di crash o di malfunzionamento hardware, un sistema per questo sono le tecnologia [[RAID]]

Il file system comporta da due parti fondamentali

- file: ovvero un astrazione sul mezzo di storage dei dati questo ha un nome con cui si può fare riferimento ad una collezione di dati di lunghezza arbitraria sul device. Il file in se è composto da due parti
    - Metadati: ovvero informazioni sul file stesso come ultima modifica data di creazione dimensione su disco e così via
    - dati: i dati sono una qualsiasi informazione ci venga scritta fuori infatti sono un lungo array di byte senza tipo. Questo permette di scrivere sia file con formati molto semplici che file moto complessi come database e file con dentro immagine
- Directory: sono file contenendo system-defined metadati e dati arbitrari.
    - Una FIle Directory invece è una lista di nomi human-readable che mappano un nome a un file o ad una directory.

    Un modello per rappresentarle sono delle cartelle che contengono altre cartelle o documenti. Questo ci permette di organizzare i file in modo gerarchico


![[654E36E0-2AAA-44DA-8E0B-F77F459190D3.jpeg]]

La stringa che definisce il nome di un file è composta da una lista di directory e dal nome del set di dati. questa viene chiama path nella stringa il simbolo “/”  separa i componenti del nome.

I path possono essere di due tipi

- relativi: non iniziano per / e sono del tipo “home/user/foo.txt”
- Assoluti: sono relativi alla directory root e inizia quindi per /

L‘organizzazione gerarchica della directory può essere vista come un albero se ogni file è rappresentato da un unico path altrimenti diventa un DAG la radice del albero viene chiama root directory

![[BD0C6154-5A52-43C0-9CBD-643DFBEAEE0C.jpeg]]

Molti sistemi operativi permettono di riferirsi ad un file utilizzando più nomi ma li limitano in moda da evitare cicli questo perché permette non semplificare alcuni operazioni come [[Reference Counting]] dei file e la permette alla ricerca ricorsiva di fermarsi

