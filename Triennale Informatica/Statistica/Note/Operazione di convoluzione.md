---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Operazione di convoluzione
---
La __convoluzione__ è un'[[Operazioni algebriche|operazione matematica]] solitamente denotata con  $*$ 

L'idea generale di questa operazione è quella di calcolare una media pesata di una funzione $f$ utilizzando i pesi definiti da un'altra funzione $g$. 
Formalmente, la convoluzione discreta tra due funzioni $f$ e $g$  è definita come:  $$
(f * g)(n) = \sum_{i=-\infty}^{\infty} f(i) g(n-i)
$$Mentre, nella forma continua è data da:  $$
(f * g)(t) = \int_{-\infty}^{\infty} f(\tau) g(t - \tau) d\tau
$$
Questa operazione ha molteplici applicazioni:  
- **Elaborazione delle immagini**: applicazione di filtri convoluzionali per il miglioramento e l'estrazione di caratteristiche nelle immagini.  
- **Elaborazione del segnale**: utilizzata nei sistemi di filtraggio per migliorare la qualità del segnale o rimuovere rumori indesiderati.  
- **Riconoscimento dei pattern**: fondamentale nelle reti neurali convoluzionali (CNN), dove viene utilizzata per l'estrazione di caratteristiche significative dalle immagini.  
- **Equazioni differenziali**: la convoluzione aiuta a risolvere equazioni differenziali lineari e sistemi dinamici.  

La convoluzione possiede anche alcune proprietà fondamentali, tra cui:  
- [[Proprietà del operazioni - Commutativita|Commutatività]]:   $f * g = g * f$ 
- [[Proprietà del operazioni - Associativa|Associatività]]:   $f * (g * h) = (f * g) * h$
- [[Proprietà del operazioni - Distributività|Distributività]]: $f * (g + h) = (f * g) + (f * h)$
- __[[Operazioni - Elemento Neutro o identita|Elemento neutro]]__: la convoluzione con la delta di Dirac o con l'impulso unitario lascia invariata la funzione originale.  


>[!tip] intuizione visiva
>questo da un [idea visuale](https://youtu.be/IaSGqQa5O-M?si=H2xv8S8jRUAUTuHl) di cosa rappresentano le convoluzioni



In this example, the red-colored "pulse",   g ( τ ) , ![{\displaystyle \ g(\tau ),}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8682ec88f51b5ebb0dda735983ec3165d825382c) is an [even function](https://en.wikipedia.org/wiki/Even_function "Even function") (   g ( − τ ) = g ( τ )   ) , ![{\displaystyle (\ g(-\tau )=g(\tau )\ ),}](https://wikimedia.org/api/rest_v1/media/math/render/svg/652e3c0430a4931e2265d6947e582e557882021e) so convolution is equivalent to correlation. A snapshot of this "movie" shows functions g ( t − τ ) ![{\displaystyle g(t-\tau )}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3cb1c1c6de1ad02f14ce3217246b956b66f1c5a2) and f ( τ ) ![{\displaystyle f(\tau )}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bcba00f11285b589b0ff57beeaf118defab2cfe8) (in blue) for some value of parameter t , ![{\displaystyle t,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4ea3ad87830a1055c7b85c04cf940cfd3b847ae6) which is arbitrarily defined as the distance along the τ ![{\displaystyle \tau }](https://wikimedia.org/api/rest_v1/media/math/render/svg/38a7dcde9730ef0853809fefc18d88771f95206c) axis from the point τ = 0 ![{\displaystyle \tau =0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4422051052da869dc5b1f0e1cfb06a045ee0c36a) to the center of the red pulse. The amount of yellow is the area of the product f ( τ ) ⋅ g ( t − τ ) , ![{\displaystyle f(\tau )\cdot g(t-\tau ),}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b778e710d0b6bed2b0b5beed59be539e9dfdde41) computed by the convolution/correlation integral. The movie is created by continuously changing t ![{\displaystyle t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/65658b7b223af9e1acc877d848888ecdb4466560) and recomputing the integral. The result (shown in black) is a function of t , ![{\displaystyle t,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4ea3ad87830a1055c7b85c04cf940cfd3b847ae6) but is plotted on the same axis as τ , ![{\displaystyle \tau ,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/26d6cc28c28ff4ff88402f47f2a99e583e9e045f) for convenience and comparison.

![[Convolution_of_box_signal_with_itself2.gif]]
n this depiction, f ( τ ) ![{\displaystyle f(\tau )}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bcba00f11285b589b0ff57beeaf118defab2cfe8) could represent the response of a [resistor-capacitor circuit](https://en.wikipedia.org/wiki/Resistor-capacitor_circuit "Resistor-capacitor circuit") to a narrow pulse that occurs at τ = 0. ![{\displaystyle \tau =0.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/536a344c98711768c9d2055a50e50c62e69b5fac) In other words, if g ( τ ) = δ ( τ ) , ![{\displaystyle g(\tau )=\delta (\tau ),}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ecb1ed1bb9b4152e2dda12a3ab518e94a5d5a35e) the result of convolution is just f ( t ) . ![{\displaystyle f(t).}](https://wikimedia.org/api/rest_v1/media/math/render/svg/db88c28d6c644c905a4e12de7971c3d1eed37540) But when g ( τ ) ![{\displaystyle g(\tau )}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f3ca3806d8f1456510d15896379772656cd465da) is the wider pulse (in red), the response is a "smeared" version of f ( t ) . ![{\displaystyle f(t).}](https://wikimedia.org/api/rest_v1/media/math/render/svg/db88c28d6c644c905a4e12de7971c3d1eed37540) It begins at t = − 0.5 , ![{\displaystyle t=-0.5,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/122a1d7a1cc954c319923b4e430df85a9a1edd36) because we defined t ![{\displaystyle t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/65658b7b223af9e1acc877d848888ecdb4466560) as the distance from the τ = 0 ![{\displaystyle \tau =0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4422051052da869dc5b1f0e1cfb06a045ee0c36a) axis to the _center_ of the wide pulse (instead of the leading edge).

![[Convolution_of_spiky_function_with_box2.gif]]



e viene utilizzata in diversi ambiti, come nelle [[Convolutional Neural Network  (CNN)|Convolutional Neural Network  (CNN)]] che prendono il nome proprio da questa operazione e nell'_[[Immage Processing|image processing]]_, dove viene impiegata per il [[Filtering|filtraggio]] delle immagini.  
