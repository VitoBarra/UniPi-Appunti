---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Condition Variable
---
Strumenti per la sincronizzazione dei thread, è fatta in modo per aspettare che una condizione sia valida e rilasciare il lock che ha il thread che aspetta. questo severve per fare una separazione dei doveri tra attesa e condizione dove il lock provede a fare l attesa e la codition variable gestisce dei controlli su condizioni.

# Semantica Mesa

la condition variable con una signal  fa passare un thread da uno stato wait a uno Ready questo quando verrà schedulato tenterà di prendere il lock e perseguirà con la sua esecuzione

### Pattern di utilizzo

### Wait

```c
lock.acquire()
while(condizione)
	wait(CV,lock);
lock.relese()
```

si usa un while per aspettare sulla condizione perche a seconda del interliving dei thread quella condizione potrebbe non essere piu vera quindi bisogna  rimmettersi in attesa. in piu ogni tanto la semantica mesa riattiva un thread senza signal quindi bisogna ricontrollare per assicurarsi che tutto vada a buon fine

### Signal

```c
condizione = true
signal(CV);
```

### BrodCast

```c
condizione = true
Brodcast(CV);
```

risveglia tutti i thread che aspettano su quella condizione

# Semantica Hoare

sveglia un thread ma viene svegliato passandogli il lock quindi facendo

```c
Signal(cv,lock)
```

 è il duale dela wait, è piu complessa della semantica Mesa siccome c è un passaggio di lock.

con il passaggio significa che tra i thread che devono operare con quel lock il thread che deve andare in esecuzione è necessariamente quello a cui è stato passato il lock con la signal. questo siccome tutti gli altri thrad che cercono di fare lock acquire verranno messi in stato di wait.

una volche il il thread che ha ottenuto il lock lo rilascia viene restituito al thread che ho fatto la signal cosi che possa finire la sua esecuzione e ralascaire il lock

### Pattern di utilizzo

### Wait

```c
lock.acquire()
if(condizione)
	wait(CV,lock);
lock.relese()
```

### Signal

```c
lock.acquire()
condizione = true
signal(CV,lock);

lock.relese()
```
