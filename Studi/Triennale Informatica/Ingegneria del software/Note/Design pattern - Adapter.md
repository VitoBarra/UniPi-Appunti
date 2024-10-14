---
Subject: Ingegneria del software
topic: nota
tags: IS
---

Prev: [[Ingegneria Del Software (IS)]]

# Design pattern - Adapter
---
tipo di [[GoF Design Patterns]]  Strutturale



![[0769A940-C310-4A7C-9F45-0448A20D12B7.jpeg]]
### Quando usarlo
quando due sistemi implementano sistemi simili ma e devono poter comunicare 
### Vantaggi
- un adattatore converta un interfaccia di una classe i un altra interfaccia  del cliente specifico, facendo lavorare insieme classi che sarebbero altrimenti incompatibile (interfaccia diverse)

#### Struttura
![[B3559C79-45FB-4F4B-9762-4D555CDDDA3A.jpeg]]
##### Componenti
- _Target_:  Definisce l interfaccia del applicazione specifica
- _Adaptee_:  Definisce l interfaccia da adattare
- _Adapter_: adatta l interfaccia di un _Adaptee_ alla interfaccia _Target_
- _Client_: utilizza l oggetto conformandosi con l interfaccia _target_
