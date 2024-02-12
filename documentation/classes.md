
# Classes (Calculatrice Scientifique)

> Nous allons utiliser [Mermaid](https://mermaid.js.org/syntax/classDiagram.html) pour réaliser notre diagramme de classes.

> L'objectif est prinicipalement de modéliser les données traitées par votre application.
> > Les données du PMV ou plus.

> Dans un premier temps, nous allons modéliser un diagramme présent dans les notes de cours

```mermaid
---
title: Diagramme de classes - Cégep St-Jean
---
classDiagram
    %% D'abord spécifier les relations
    %% Voir: https://mermaid.js.org/syntax/classDiagram.html#defining-relationship

    %% Héritage
    Personne <|-- Étudiant
    
    %% Composition (possession forte)
    Étudiant *-- Statut
    CégepStJean *-- "*" Étudiant
    CégepStJean *-- "*" VignetteStationnement
    
    %% Composition + champ associé au type
    %% Le cégep possède un Directeur qui est une Personne
    CégepStJean *-- Personne : Directeur

    %% Agrégation (possession faible)
    Étudiant o-- "?" VignetteStationnement
    
    %% Relation non spécifique
    %% Il faut ajouter un texte et préciser le sens de lecture
    Étudiant "*" --> "*" Cours : est inscrit à

    %% Liens d'utilisation (dépendance)
    VignetteStationnement ..> Session
    Session ..> Saison
    
    %% Ensuite définir les champs ou attributs ou variables membre de chaque classe
    class CégepStJean {
        Adresse
        AnnéeFondation
    }
    
    class Étudiant {
        %% Au besoin vous pouvez préciser le type de chaque champ
        entier NoDa
        string CodePermanent
    }
    
    class Cours {
        Titre
        Numéro
    }
    
    class VignetteStationnement {
        Numéro
        Session
    }
    
    class Session {
        Année
        Saison
    }
    
    class Personne {
        Nom
        DateDeNaissance
        %% champ/propriété calculable, précédé d'un /
        /Âge
    }
    
    %% Il est possible d'annoter une "classe"
    %% Voir: https://mermaid.js.org/syntax/classDiagram.html#annotations-on-classes
    <<enumeration>> Statut
    class Statut {
        TempsPlein
        TempsPartiel
        Ancien
    }
    
    <<enumeration>> Saison
    class Saison {
        Hiver
        Été
        Automne
    }
    
```

---

> Voyons maintenant pour la calculatrice, mode PMV

```mermaid
---
title: Diagramme de classes - Calculatrice Scientifique
---
classDiagram
    %% En général, il est bon d'ajouter les acteurs dans le diagramme d'analyse
    %% Même si l'acteur n'aura aucune donnée associée
    Utilisateur --> Calculatrice : Effectue un calcul
    Calculatrice *-- ÉtatCalcul
    Calculatrice --> "*" Opération : Calcule
    Opération *-- TypeOpération
    Calculatrice *-- "*" Touche
    Utilisateur --> Touche : Appuie sur des
    Opération ..> Touche


    class Calculatrice {
        Opérande1
        Opération [?]
        Opérande2 [?]
    }
    
    <<enumeration>> ÉtatCalcul 
    class ÉtatCalcul {
        Opérande1
        Opérande2
    }
    
    class Opération {
        Touche ToucheAssociée
        string Nom
    }
    
    <<enumeration>> TypeOpération     
    class TypeOpération {
        Unaire
        Binaire
    }
    
    <<enumeration>> Touche
    class Touche {
        0 à 9
        .
        plus, moins, fois, div, mod
        =
        reset
        négation
    }
    
```

---

> Si vous voulez aller plus loin, vous pouvez ajouter des méthodes dans vos classes
> Conventionnellement, on quitte alors le domaine de l'analyse pour entrer dans la conception.

> En mode conception, on supprime en générale les classes qui
> n'auront pas d'implémentation, comme Utilisateur dans notre cas.

> En mode conception, on élimine aussi les liens flous nommés pour les
> remplacer par des liens programmatiquement plus clairs.


```mermaid
---
title: Diagramme de classes (conception) - Calculatrice Scientifique
---
classDiagram
    Calculatrice *-- ÉtatCalcul
    Calculatrice ..> "*" Opération
    Opération *-- TypeOpération
    Calculatrice ..> "*" Touche 
    Opération ..> Touche


    %% On ajoute les méthodes
    %% On peut distinguer entre les méhodes publiques + et privées -
    class Calculatrice {
        Opérande1
        Opération [?]
        Opérande2 [?]
        +AppuyerSurUneTouche(touche)
        -Reset()
        -EffectuerUneOpération(opération)
    }
    
    <<enumeration>> ÉtatCalcul 
    class ÉtatCalcul {
        Opérande1
        Opérande2
    }
    
    %% Si une méthode retourne un résultat, on peut l'indiquer
    class Opération {
        Touche ToucheAssociée
        string Nom
        +Calculer(opérande1, opérande2?) résultat
    }
    
    <<enumeration>> TypeOpération     
    class TypeOpération {
        Unaire
        Binaire
    }
    
    <<enumeration>> Touche
    class Touche {
        0 à 9
        .
        plus, moins, fois, div, mod
        =
        reset
        négation
    }
    
```

---

Retour au [README](../README.md).
