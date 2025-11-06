---
Course 1: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
  - IIA
Area:
topic:
SubTopic:
---

# Agenti Knowledge based con FOL
---
Un **[[Agenti Razionali|agente basato sulla conoscenza]]** con [[Logica del primo ordine (FOL)|FOL]] è un espansione degli agenti [[Agenti Knowledge Based|basati su conoscenza]] dove le interrogazioni possono includere quantificatori, come $\forall$ e $\exists$, e la loro valutazione implica la verifica delle condizioni di **verità** per tutti o per alcuni elementi del dominio.

assumendo una **knowled base** di solo [[Forma a Clausola definita e Clausola di Horn|clausole horn]] si puo usare l'interfaccia 
- **ASKVARS**($KB$, $P(x)$): che coinvolge variabili libere è restituisce **sostituzioni** o **liste di associazione** tra variabili e termini, dette **binding list**, che specificano le istanze per cui la formula risulta vera.  

### Agenti Knowledge base in un nuovo dominio
Per definire un dominio in cui è possibile usare un agente **knowled bease con FOL** va creato un KB con al interno gli **assiomi** che costituiscono le verità fondamentali del dominio, fornendo la base inferenziale da cui possono essere dedotti nuovi enunciati. Gli **enunciati derivati**, o **teoremi**, sono proposizioni [[Conseguenza Logica (Deduzione)|logicamente conseguenti]] dagli assiomi già presenti nella KB. Da un punto di vista operativo, la loro esplicitazione riduce il costo computazionale dell’inferenza, evitando di ricostruire ogni deduzione dai principi di base.  

Alcuni predicati possono essere definiti solo parzialmente, attraverso specificazioni delle loro proprietà necessarie o sufficienti, nella forma  $$
\forall x \; P(x) \Rightarrow \Psi(x)
$$oppure  $$
\forall x \; \Phi(x) \Rightarrow P(x)
$$che delineano rispettivamente le condizioni che un elemento deve soddisfare per possedere una certa proprietà o per essere riconosciuto come appartenente a una categoria logica. Accanto a questi, la **KB** può contenere **fatti atomici** del tipo $P(a, b)$, che rappresentano istanze particolari del dominio e costituiscono la base da cui il sistema inferenziale deduce nuove conoscenze.

