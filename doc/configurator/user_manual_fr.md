# NEXT-BIM Configurator
https://www.next-bim.com/

## Démarrage rapide
- Ajoutez des fichiers *.ifc* via *File | Add .ifc/.nbim_preprocessed*
- Une fois les fichiers chargés ils apparaissent dans la fenêtre [Hierarchy](#hierarchy)
- Exportez le .nbim pour visualisation dans NEXT-BIM Explorer via **File | Generate NBIM...**

## Sauvegarde de vos configurations
### Sauvegarde de projets
**File | Save Project** permet de sauvegarder le projet actuel.
Un projet est constitué de la liste des fichiers *.ifc* chargés, accompagnés de l'ensemble de configuration actuelle.
### Import/Export de fichiers de configuration
**File | Import/Export configuration file...** permet la réutilisation de configurations entre différents projets. L'ensemble de configuration actuelle est sauvegardée dans un fichier *.nbim_config*.
## Fenêtres
### Vue 3D
#### Contrôles de la caméra
- Rotation : clic gauche enfoncé + déplacement de la souris
- Translation du point de vue : clic droit enfoncé + déplacement de la souris
- Zoom : molette de la souris

En mode Orbit la rotation d'effectue autour du point de vue, en mode Fly la caméra tourne sur elle-même

#### Inspection
Pour inspecter un objet, cliquez dessus avec le bouton gauche de la souris. Il s'affiche en bleu et la [Hierarchy](#hierarchy) se déroule jusqu'à cet objet.
Pour accéder à son [menu contextuel](#menu-contextuel), faites un clic droit sur l'objet.
#### Preview
Dans la barre de menu, un menu déroulant permet de controler ce que l'on voit dans la vue 3D.
* Preview all : tout est affiché
* Preview [tabletop](#tabletop) : prévisualisation de l'affiche en mode Tabletop
* Preview [selection](#selection) : affiche seulement les objets dans la liste de selection
* Preview [checklist](#checklist) : affiche seulement les objets présents dans la checklist
* Preview a [visibility list](#visibility-lists) : prévisualisation d'une *visibility list*

### Hierarchy

Les différents fichiers ouverts apparaissent ici. Ils se déroulent selon la hierarchie des élements IFC.

A coté de chaque objet, l'oeil permet de masquer/réafficher l'objet et ses enfants. (cela n'affecte que la [Vue 3D](#vue-3d) de NEXT-BIM Configurator, pour retirer un objet complètement voir [ici](#retirer-des-objets-du-nbim-final))

Cliquez sur un objet pour l'inspecter, double clic pour le centrer dans la [Vue 3D](#vue-3d).
Cliquez droit sur un objet pour accéder à son [menu contextuel](#menu-contextuel)

#### Menu contextuel
Permet un accès rapide aux différentes configurations applicables sur un objet ou son type.
##### Retirer des objets du nbim final
Dans le [menu contextuel](#menu-contextuel) d'un objet l'option "Remove object from output" permet de completement retirer l'objet (et ses enfants) de .nbim final.
> Les objets retirés apparaissent barrés.

### Properties

Dans la fenêtre Properties, on peut visualiser les propriétés de l'objet acutellement [inspecté](#inspection) (affiché en bleu dans la [Vue 3D](#vue-3d)).

### Search
La recherche (via **Edit/Find...**) permet de contruire une liste de [selection](#selection) en effectuant des recherches d'objets basées sur un ou plusieurs critères tels que leur nom, leur type, le fichier .ifc ou bien leurs propriètes.

### Selection
La liste de selection permet d'effectuer des actions sur plusieurs objets en même temps.
Pour ajouter ou retirer des objets de la liste de selection, plusieurs options : 
1. Via le menu contextuel d'un objet dans la fenêtre [Hierarchy](#hierarchy) ou dans la [Vue 3D](#vue-3d)
2. En faisant un clic gauche sur un objet dans la [Vue 3D](#vue-3d) en maintenant enfoncé la touche CTRL
3. En faisant une [Recherche](#search)

Une fois que la liste de selection contient des objets, les différentes actions disponibles s'affichent dans la fenêtre Selection.

### Settings
#### Default Configuration
Permet de definir la configuration actuelle comme configuration par défaut lors de l'ouverture de NEXT-BIM Configurator
#### Cache
Lors qu'un fichier *.ifc* est chargé pour la première fois, il est converti en fichier *.nbim_preprocessed* et placé dans un dossier de cache. La prochaine fois que le même *.ifc* est ouvert, le fichier *.nbim_preprocessed* est réutilisé au lieu d'avoir à refaire la conversion.

L'emplacement du cache et sa taille maximale est configurable dans ce menu.
> Nous vous conseillons de ne pas descendre en dessous de la taille maximale par défaut de 8 Go pour une utilisation confortable.

## Configuration

> Chacune des fenêtres de cette liste possède son propre menu **File** avec la possibilité d'importer/exporter juste la configuration qui correspond à cette fenêtre.

### Annotations
La configuration **Annotations** permet de définir la liste d'utilisateurs, les annotations prédéfinies et les différents états disponibles pour les annotations.

### Tabletop
La configuration **Tabletop** permet de controler quels types d'élements ifc apparaissent dans mode Tabletop de NEXT-BIM Explorer.

- Panneau de gauche : la liste des types autorisés
- Panneau de droite : la liste des types présents dans les fichiers actuellement chargés

Cliquez sur un type pour le passer d'un panneau à l'autre.
La liste de types autorisés peut être réordonnée par glisser-déposer des types ou par les flêches haut/bas.
#### Limite de triangles
Pour des raisons de performances, nous avons une limite de 1 million de triangles dans la visualisation en mode tabletop. 
Si cette limite est dépassée, un message apparaîtra sous le dernier type qui passe sous la limite. Les types suivants seront ignorés.

### Materials

La configuration **Materials** permet de modifier l'appararence de la maquette.
Trois onglets sont disponibles qui permettent d'appliquer *material* à un objet spécifique, à tous les objets d'un type ifc ou à tous les objets d'un fichier.

> Si plusieurs configurations sont applicables pour un même objet, la priorité est la suivante : par objet > par type > par fichier

Chaque *material* a les options suivantes :
- *Preserve color* ou bien appliquer une nouvelle couleur
- *Preserve transparency* ou bien appliquer une nouvelle transparence
- *Texture* permet d'ajouter une texture 


### Property filtering

La configuration **Property filtering** permet de masquer des *property sets* dans l'Info Tool de NEXT-BIM Explorer.

### Visibility Lists

La configuration **Visibility Lists** permet de créer des listes de masquage qui peuvent être ensuite rapidement activées dans NEXT-BIM Explorer dans le **Visibility Tool**, dans l'**Annotate Tool** lors de la prise de photo et le **Snap Tool** lors d'un snap.

* IFC type whitelist : seulement les types présents dans la liste seront visibles, tous les autres seront masqués
* IFC type blacklist : les types présents dans la liste seront masqués, tous les autres resteront visibles
* Object whitelist : seulement les objets présents dans la liste seront visibles, tous les autres seront masqués
* File whitelist : seulement les fichiers cochés seront visibles, les autres seront masqués

### Checklist

La configuration **Checklist** permet de choisir quels objets doivent être contrôlés, ainsi que les différents états dans lesquels ils peuvent être.

Les objets peuvent ête ajoutés individuellement (un par un manuellement, ou par la [selection](#selection) par exemple), ou bien par type IFC.

L'onglet *Property Set* permet d'ajouter automatiquement des objets à la checklist s'ils possèdent la propriété définie ici.

Les checklists peuvent être importées depuis des fichiers .xlsx (dans le configurator via *File | Load XLSX Checklists*, ou directement dans NEXT-BIM Explorer)

Les fichiers .xlsx doivent suivre ce format :
- une colonne avec les GUIDs IFC ou les RevitIDs
- une colonne avec les états de départ des objets (la liste des états doit être personnalisée dans NEXT-BIM Configurator)
    Cette colonne DOIT avoir comme en-tête : "checklist" ou "next-bim checklist" (sans guillemets, majuscules sans importances)
Vous pouvez avoir plusieurs checklists dans un seul fichier .xlsx : une checklist par feuille de calcul

