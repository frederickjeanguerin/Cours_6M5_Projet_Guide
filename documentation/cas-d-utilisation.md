
# Cas d'utilisation (Calculatrice Scientifique)

> Le meilleur logiciel pour les cas d'utilisation est [PlantUML](https://plantuml.com/fr/use-case-diagram).
> Toutefois, dans le but de simplifier les choses, nous allons
> nous rabattre sur une alternative moins puissante, mais plus simple appelée 
> [Mermaid](https://mermaid.js.org/syntax/flowchart.html).

> Les aventages de Mermaid sur PlanUML sont:
> * Simplicité
> * Affichage natif dans GitHub et PyCharm
>> Pour afficher dans PyCharm, il faut installer le plugin.
>> Une icone apparaît dans la gouttière quand on crée un diagramme.
>> Il suffit de cliquer dessus.

> Puisque Mermaid ne définit pas de diagrammes de cas d'utilisation natif,
> on va utiliser un diagramme de type [FlowChart](https://mermaid.js.org/syntax/flowchart.html) à la place.

> Le diagramme doit définir les acteurs du système et les différentes
> fonctionnalités accessibles à ces acteurs.

> Les fonctionnalités définies dans le document "fonctionnalités" devraient se retrouver 
> dans ce diagramme. Il peut y avoir plus de trucs.

> De plus, vous devez définir la portée du PMV (produit minimalement viable).

```mermaid
---
title: Cas d'utilisations - Calculatrice Scientifiques
---
%% Type de diagramme: flowchart
%% Orientation du diagramme: LR (Left to right)
flowchart LR
    
    %% Définir d'abord les acteurs
    %% Il n'y a pas de stickman en mermaid. 
    %% Mais on peut le simuler avec un caractère coréen
    user(["<span style='font-size:200%'>웃</span><br> Utilisateur"])
    %% Ou encore utiliser un émoji (décommenter la ligne ci-dessous)
    %% user(["<span style='font-size:200%'>👤</span><br> Utilisateur"])
    stockage[(stockage)]
    
    %% Définir ensuite les cas ou fonctionnalités du "système"
    subgraph système ["&nbsp;"]
        %% Identifier les cas faisant partie du PMV
        subgraph PMV
            arithmétique-de-base(Effectuer des calculs simples)
        end
        
        %% Ajouter ensuite les cas qui ne font pas partie du PMV
        arithmétique-scientifique(Effectuer des calculs scientifiques)
        parenthèses(Ajouter des parenthèses)
        
        poursuivre("Poursuivre un calcul<br>au démarrage")
        rémanence(Sauvegarder & Restaurer)

        %% Un cas peut utiliser un autre cas
        poursuivre -->|utilise| rémanence
    end
    
    %% Définir les liens entre les acteurs et les cas
    %% L'ordre est important et décidera si l'acteur sera positionné
    %%      à gauche ou à droite du système.
    %% Par convention on positionne l'acteur principal à gauche
    %%      et les acteurs secondaires à droite.
    user --- arithmétique-de-base
    user --- parenthèses & arithmétique-scientifique
    rémanence --- stockage
    user --- poursuivre

    %% Définir au besoin des styles particulier
    %% La couleur doit être une couleur CSS valide 
    %% -> https://www.w3schools.com/cssref/css_colors.php.
    style PMV fill:blue
    %% Ou alors hexadécimale à 3 ou 6 chiffres
    style stockage fill:#060
```

> Supposons qu'une IA peut elle-même effectuer des calculs...
> bien que ce soit un peu exagérer ici.

```mermaid
---
title: Cas d'utilisations - Calculatrice Scientifiques avec IA
---
flowchart LR
    user(["<span style='font-size:200%'>웃</span><br> Utilisateur"])
    stockage[(stockage)]
    IA(["<span style='font-size:200%'>🤖</span><br> IA"])
    UouIA(["<span style='font-size:200%'>웃🤖</span><br>Utilisateur ou IA"])

    %% liens entre les acteurs
    IA --> UouIA
    user --> UouIA
    
    subgraph système ["&nbsp;"]
        subgraph PMV
            arithmétique-de-base(Effectuer des calculs simples)
        end
        
        invoquer-ia(Invoquer IA)
        arithmétique-scientifique(Effectuer des calculs scientifiques)
        parenthèses(Ajouter des parenthèses)
        
        poursuivre("Poursuivre un calcul<br>au démarrage")
        rémanence(Sauvegarder & Restaurer)
        poursuivre -->|utilise| rémanence
    end
    
    UouIA --- arithmétique-de-base
    UouIA --- parenthèses & arithmétique-scientifique
    rémanence --- stockage
    
    %% liens plus longs pour équilibrer le diagramme
    user ---- invoquer-ia
    user ---- poursuivre

    style PMV fill:blue
    style stockage fill:#060
```

> Explorer un sous-cas d'utilisation:
>> Utile prioritairement pour les cas complexes qui font partie du PMV.

```mermaid
---
title: Sous-cas d'utilisations - Effectuer des calculs simples
---
flowchart LR
    user(["<span style='font-size:200%'>웃</span><br> Utilisateur"])
    
    subgraph système ["&nbsp;"]
        additionner
        soustraire
        multiplier
        diviser
        modulo("diviser (modulo)")
        inverser("inverser additivement (négation)")
        combiner(Enchaîner des opérations)
        entrer(Entrer des nombres)
        annuler(Annuler une opération)
        reset(Remettre à zéro)
    end

    user --- additionner & soustraire & multiplier & diviser
    user --- inverser & modulo & combiner & annuler & entrer & reset
```

---

Retour au [README](../README.md).
