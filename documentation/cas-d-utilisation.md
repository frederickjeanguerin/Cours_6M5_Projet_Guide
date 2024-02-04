
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
    user(["<span style='font-size:200%'>웃</span><br> Utilisateur"])
    %% user(["<span style='font-size:200%'>👤</span><br> Utilisateur"])
    stockage[(stockage)]
    
    %% Définir ensuite les cas ou fonctionnalités du "système"
    subgraph système ["&nbsp;"]
        %% identifier les cas faisant partie du PMV
        subgraph PMV
            arithmétique-classique
        end
        arithmétique-scientifique
        parenthèses
        rémanence
    end
    
    %% Définir les liens entre les acteurs et les cas
    user --- arithmétique-classique
    user --- parenthèses & arithmétique-scientifique
    rémanence --- stockage
    
    %% Définir au besoin des styles particulier
    style PMV fill:#00F
```

---

Retour au [README](../README.md).
