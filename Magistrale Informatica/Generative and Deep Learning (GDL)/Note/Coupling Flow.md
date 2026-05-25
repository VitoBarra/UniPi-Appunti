---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area: Modelli Generativi
topic: Flow-based models
SubTopic:
---
# Coupling Flow
---
Il **Coupling Flow** e una famiglia di trasformazioni invertibili usata nei [[Normalizing Flows]] per ottenere un buon compromesso tra espressivita e trattabilita del jacobiano.

L'idea centrale e dividere il vettore di input in due parti, per esempio $$x = (x_A, x_B)$$ e trasformarne solo una usando l'altra come contesto. In questo modo la trasformazione resta abbastanza ricca da modellare dipendenze non banali, ma il [[Jacobiana di una funzione|jacobiano]] assume una struttura semplice da gestire.

Una forma tipica di coupling layer e:

$$y_A = x_A$$

$$y_B = T_{\theta}(x_B; x_A)$$

dove $x_A$ resta invariata e $x_B$ viene trasformata con una funzione i cui parametri dipendono da $x_A$. La parte lasciata invariata non e quindi inutile: serve a controllare come viene aggiornata l'altra parte.
![[IMG - Coupling Flow visivamente.png]]

## Perche e utile
Il vantaggio del **Coupling Flow** e che l'invertibilita viene garantita per costruzione. Se la trasformazione applicata a $x_B$ e invertibile rispetto a $x_B$, allora anche l'intero layer e invertibile:

$$x_A = y_A$$

$$x_B = T_{\theta}^{-1}(y_B; y_A)$$

Questo evita il problema generale dei [[Normalizing Flows]], dove una trasformazione neurale arbitraria puo essere difficile da invertire o avere un determinante del jacobiano troppo costoso da calcolare.

## Jacobiano
La ragione matematica per cui i coupling layer sono cosi usati e che il loro jacobiano ha struttura triangolare a blocchi. Se $y_A=x_A$ e $y_B$ dipende da $x_A$ e $x_B$, allora:

$$
J =
\frac{\partial y}{\partial x}
=
\begin{bmatrix}
\frac{\partial y_A}{\partial x_A} & \frac{\partial y_A}{\partial x_B} \\
\frac{\partial y_B}{\partial x_A} & \frac{\partial y_B}{\partial x_B}
\end{bmatrix}
=
\begin{bmatrix}
I & 0 \\
\ast & \frac{\partial y_B}{\partial x_B}
\end{bmatrix}
$$

Essendo triangolare, il determinante si ottiene facilmente:

$$\det J = \det(I)\det\left(\frac{\partial y_B}{\partial x_B}\right) = \det\left(\frac{\partial y_B}{\partial x_B}\right)$$

Quindi non serve calcolare il determinante di una matrice piena ad alta dimensionalita: basta controllare la parte trasformata.

## Due varianti base
Le due forme piu comuni sono:
- **additive coupling**: $$y_B = x_B + m_{\theta}(x_A)$$
- **affine coupling**: $$y_B = x_B \odot \exp(s_{\theta}(x_A)) + t_{\theta}(x_A)$$

Nel caso additivo il determinante del jacobiano vale $1$, quindi il layer e molto semplice ma meno espressivo. Nel caso affine si introduce anche uno scaling locale, quindi la trasformazione diventa piu flessibile senza perdere la trattabilita del log-determinante.

## Famiglie di modelli
Il **Coupling Flow** non e un singolo modello, ma un framework architetturale da cui derivano diverse famiglie importanti:
- [[Coupling Flow - NICE]]: usa additive coupling e preserva il volume
- [[Coupling Flow - RealNVP]]: introduce affine coupling e struttura multi-scale
- [[Coupling Flow - GLOW]]: estende RealNVP con actnorm e convoluzioni invertibili $1 \times 1$

Questi modelli condividono la stessa idea di fondo: ottenere trasformazioni profonde e invertibili imponendo una struttura semplice sul jacobiano.

## Limiti
I **Coupling Flow** hanno alcuni limiti:
- un singolo layer modifica direttamente solo una parte delle variabili;
- l'espressivita dipende da come si alternano split, masking e mixing;
- la struttura trattabile del jacobiano si ottiene imponendo vincoli forti alla forma della trasformazione.

Nonostante questo, i **Coupling Flow** sono una delle idee architetturali piu importanti nei [[Normalizing Flows]], perché permettono di costruire trasformazioni invertibili profonde senza perdere la possibilita di calcolare la densita in modo efficiente.
