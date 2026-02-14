---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Formato file - System biology markup Language (SBML)
---
Il **System Biology Markup Language (SBML)** è uno standard aperto basato su XML per la rappresentazione e lo scambio di modelli computazionali di sistemi biologici, in particolare [[Chemical Reaction Network (CRN)|CRNs]], pathway metabolici e modelli dinamici basati su [[Ordinary Differential Equation (ODE)|ODE]].

Obiettivo principale:
- garantire interoperabilità tra software di modellazione;
- consentire condivisione e riproducibilità dei modelli;
- separare la descrizione del modello dalla simulazione.

Struttura generale di un modello SBML Un file SBML è un documento XML strutturato in componenti principali:
- **model**: contenitore principale.
- **listOfCompartments**: compartimenti (es. citoplasma).
- **listOfSpecies**: specie molecolari con concentrazione iniziale.
- **listOfParameters**: parametri cinetici ($k$, costanti globali).
- **listOfReactions**: reazioni con stechiometria e legge cinetica.
- **listOfRules / Events**: vincoli dinamici o eventi discreti.
- **listOfFunctions**: funzioni riutilizzabili.

Rappresentazione di una reazione

Per una reazione del tipo:

$$\ell_1 S_1 + \dots + \ell_\rho S_\rho \xrightarrow{k} \ell'_1 P_1 + \dots + \ell'_\gamma P_\gamma$$

in SBML vengono specificati:
- **Reactants** con coefficienti $\ell_i$
- **Products** con coefficienti $\ell'_i$
- **KineticLaw** con espressione matematica, ad esempio (massa-azione):
$$r = k[S_1]^{\ell_1}\cdots[S_\rho]^{\ell_\rho}$$

La legge cinetica è scritta in MathML (standard XML per espressioni matematiche).


Un modello SBML non contiene direttamente le ODE esplicite, ma:
- definisce le reazioni;
- definisce le leggi cinetiche;
- la dinamica viene derivata automaticamente applicando la [[CRN - Modello mass-action|Legge di Azione di Massa]] o altre cinetiche.
Per ogni specie $S$:$$\frac{d[S]}{dt} = \sum_{\text{prod}} \ell r - \sum_{\text{react}} \ell r$$La generazione del sistema di ODE è quindi automatica a partire dalla struttura del CRN.



SBML è organizzato in:
- **Level**: evoluzione concettuale dello standard (Level 1, 2, 3).
- **Version**: revisioni incrementali.
- **Packages (Level 3)**: estensioni modulari (es. per vincoli, layout, modelli qualitativi).

Level 3 introduce modularità e maggiore flessibilità per:
- modelli qualitativi (es. [[GRN - Boolean Networks]]);
- annotazioni semantiche;
- vincoli strutturali.

Vantaggi
- Standard de facto nella systems biology.
- Supportato da numerosi software (COPASI, CellDesigner, SBMLsimulator, ecc.).
- Consente simulazione deterministica (ODE) e stocastica.
- Favorisce riproducibilità scientifica.