
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
title: Cas d'utilisations (Calculatrice Scientifiques)
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
            arithmétique-classique
            %% En principe, un use case devrait être un groupe verbal
            %% Donc le cas ci-dessus aurait du être libellé ainsi:
            %% arithmétique-classique("Effectuer une opération<br>arithmétique classique")
        end
        
        %% Ajouter ensuite les cas qui ne font pas partie du PMV
        arithmétique-scientifique
        parenthèses
        rémanence
        
        %% Acteurs internes au système
        %% Par exemple une intelligence artificielle pour remplacer un utilisateur.
        %% Plus ou moins pertinent pour une calculatrice mais pourrait vous être utile.
        IA(["<span style='font-size:200%'>🤖</span><br> IA"])
    end
    
    %% Définir les liens entre les acteurs et les cas
    %% L'ordre est important et décidera si l'acteur sera positionné
    %%      à gauche ou à droite du système.
    %% Par convention on positionne l'acteur principal à gauche
    %%      et les acteurs secondaires à droite.
    user --- arithmétique-classique
    user --- parenthèses & arithmétique-scientifique
    rémanence --- stockage

    %% Il n'y a pas de lien d'héritage en mermaid
    %% On peut le remplacer pour un lien pointillé avec texte explicatif.
    %% Le triangle (◀ ou ▶) indique la direction de lecture
    user -.-|◀ simule| IA 

    %% Définir au besoin des styles particulier
    %% La couleur doit être une couleur CSS valide 
    %% -> https://www.w3schools.com/cssref/css_colors.php.
    style PMV fill:blue
    %% Ou alors hexadécimale à 3 ou 6 chiffres
    style stockage fill:#060
```

---

Retour au [README](../README.md).
