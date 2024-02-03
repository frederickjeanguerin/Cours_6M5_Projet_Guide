
# Fonctionnalités (Calculatrice Scientifique)

> Décrivez chacune des fonctionnalités de votre application.

> Il est possible de catégoriser ces fonctionnalités.

> Il faut être aussi précis que possible (mais sans exagération).
> L'objectif est que si vous deviez confier ce document à un autre
> développeur, il pourrait arriver à coder sa propre version
> de votre application en suivant vos directives.

> Vous devez décrire le **quoi**:
>  > *Qu'est-ce que mon application va pouvoir faire?*
> 
> Pas le **comment**:
>  * L'image est stockée ~~dans une BD PostgreSQL~~.
>    * Mieux: L'image est sauvegardée par l'application.

> Pour le moment, on ne se préoccupe pas de spécifier l'interface.
> Cela viendra plus tard.
> Pour cette raison, votre description des fonctionnalités 
> devrait évacuer autant que possible tout vocabulaire qui traite
> d'interface: bouton, fenêtre, etc.
> > Parfois l'aspect interface est essentiel ou requis, donc il y a des excepetions.

## Fonctionnalités de base

### Fn: Opérations arithmétiques classiques

La calculatrice permet d'effectuer les calculs de base suivants:

* Addition
* Soustraction
* Multiplication
* Division
* Modulo
* Négation

Précisions:
 * Les calculs se font en point flottant 64 bits respectant la norme [IEEE 754](https://en.wikipedia.org/wiki/IEEE_754).
 * Les calculs se font rapidement, presque instantanément, du point de vue
de l'utilisateur.
 * Il n'y a pas d'erreurs comme telles. 
   * Une division par zéro donnera [NaN](https://en.wikipedia.org/wiki/NaN).
   * Un résultat trop grand pourrait donner l'[infini](https://en.wikipedia.org/wiki/Infinity#Computing).
 * Il est possible d'entrer des nombres avec un point décimal
 * Il est possible d'entrer des nombres en spécifiant l'exposant en base 10.
   * Cet exposant peut être négatif.
 * Il est possible d'annuler une entrée (pour possiblement recommencer). 
 * À tout moment, il est possible de voir clairement le dernier résultat d'un calcul.
 * Il est possible d'annuler un calcul en cours (le dernier résultat est préservé).
 * Il est possible de tout annuler (le dernier résultat est remis à zéro) .

> Notez que cette fonctionnalités est assez imposante.
> On aurait pu la diviser en sous-fonctionnalités: addition, soustraction, etc.
> Au moment de la réalisation du logiciel, il faudra la découper.
> Nous n'avons

### Fn: Rémanence des calculs

Lorsque l'utilisateur ferme l'application, l'état courant de la calculatrice
est préservé. Cet état est ressuscité lorsque l'application redémarre.

Précision:
* Donc il faut remettre à zéro explicitement la calculatrice pour la ramener dans son état initial.

> Contrairement à la fonctionnalité précédente, celle-ci est suffisamment simple
> pour être implémentée directement sans la découper en sous-fonctionnalités.

## Fonctionnalités intermédiaires

### Fn: Opérations mathématico-scientifiques classiques

La calculatrice permet d'effectuer les calculs scientifiques suivants:

* Logarithme (base 10, base e, base quelconque)
* Exposant (carré, cube, quelconque, base 10, base e, base 2)
* Racine (carrée, cubique, quelconque)
* Inversion (1/x)
* Pourcentage (division par 100)
* Valeur absolue
* Factorielle

La calculatrice permet de récupérer rapidement les constantes prédéfinies suivantes:
* Pi
* e ([nombre d'Euler](https://fr.wikipedia.org/wiki/E_(nombre)))

Précisions: 
 * Voir les [opérateurs arithmétiques classiques](#fn-opérations-arithmétiques-classiques)

Source:
 * Pour décrire cette fonctionnalité, nous nous sommes inspiré des opérations 
   possibles avec la [calculatrice Windows](https://apps.microsoft.com/detail/9WZDNCRFHVN5).

### Fn: Parenthèses

Un calcul peut comprendre des parenthèses pour prioriser les opérations.

Précisions:
* Il n'est pas possible de fermer une parenthèse qui n'a pas été ouverte préalablement.
* S'il manque des parenthèses finales avant d'app, elles sont ajoutées automatiquement.

### Fn: ...

---

> Il manque évidemment des fonctionnalités pour décrire complètement notre calculatrice.
> Mais nous n'avons pas à le faire ici. 
> L'intention est de vous donner un exemple de description de fonctionnalités.
> Dans votre cas cette description doit être aussi complète que possible.
> Toutefois, en ce qui concerne les fonctionnalités avancée, vous pouvez vous permettre
> d'être moins précis, ou encore juste de donner le titre, si vous avez déjà décrit plusieurs
> fonctionnalités de base.

---

Retour au [README](../README.md).
