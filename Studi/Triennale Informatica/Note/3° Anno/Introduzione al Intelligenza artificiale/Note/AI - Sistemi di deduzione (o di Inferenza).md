---
type: nota
course: Intelligenza Artificiale
topic: 
tags:
  - IA
Parent MOC: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
---

# Sistemi di deduzione (o di Inferenza)
---
un _sistema di deduzione_ è un modo per decidere se un dato $\alpha$ è [[AI - Base di conoscenza (KB)#Conseguenza logica|conseguenza logica]] di $KB \models \alpha$
-  denotiamo con $KB \vdash \alpha$ il fatto che $\alpha$ è derivabile (deducibile) da $KB$ 
- la deduzione avviene specificando delle [[Regole di inferenza|Regola di inferenza]]

l insieme delle regole formano un sistema d inferenza. dalle regole dovrebbero derivare _tutte_ e _solo_ le formule che son conseguenza logica delle regole


- _Correttezza_: 
	- Se $KB \vdash \alpha$ allora $KB \models \alpha$
	- tutto ciò che è derivabile è conseguenza logica. le regole preservano la verità
- _Completezza_: se $KB \models \alpha$ allora $KB \vdash \alpha$
	- tutto ciò che è conseguenza logica è ottenibile tramite in sistema deduttivo 

>[!example]- Prop
> si possono riscrivere tutte le leggi del calcolo proposizionale come regole di inferenza, insieme costruiscono un sistema deduttivo

