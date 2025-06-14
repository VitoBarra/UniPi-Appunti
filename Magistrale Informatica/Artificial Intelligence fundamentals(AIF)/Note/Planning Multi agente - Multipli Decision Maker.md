---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Planning Multi agente - Multipli Decision Maker
---
un caso del [[Planning Multi agente|Planning Multi agente]] è quando ci sono **più decisori autonomi**, ciascuno con proprie preferenze, obiettivi e capacità di pianificazione, si parla di **counterparts**. In questo scenario, ogni agente elabora ed esegue il proprio piano, tenendo conto delle decisioni e delle strategie degli altri. Le interazioni tra decisori possono essere classificate in due casi:
- **Obiettivo comune**: tutti i decisori perseguono un medesimo fine collettivo. È la situazione tipica di un’organizzazione cooperativa, come un’azienda in cui diversi responsabili agiscono in direzioni diverse ma per uno scopo condiviso. Il principale problema da risolvere è quello della **coordination problem**, ovvero assicurare che le azioni dei diversi agenti siano allineate e non interferiscano tra loro. La coordinazione può essere ottenuta mediante comunicazione esplicita, convenzioni operative o protocolli di sincronizzazione.
- **Obiettivi distinti o conflittuali**: ogni decisore persegue interessi propri, eventualmente in contrasto con quelli altrui. In tal caso, la pianificazione entra nel dominio della ***[[Teoria dei giochi (Game theory)|Teoria dei giochi (Game theory)]]***, la teoria della decisione strategica, che si distingue dalla **[[Teoria delle decisioni (Decision theory)|decision theory]]** per il carattere interattivo delle scelte. Ogni agente deve infatti valutare non solo le proprie azioni, ma anche le possibili risposte degli altri, sapendo che questi a loro volta stanno compiendo analisi simmetriche. 