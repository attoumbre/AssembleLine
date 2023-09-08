
# tableau de tâches

## Tâche

Souvent, les processus peuvent être représentés comme une série d'étapes. Le concept d'une ligne d'assemblage peut être un moyen utile d'organiser la logique de production, les listes de tâches à différents stades d'achèvement ou de suivre les individus progressant à travers une série d'étapes importantes.

Voici un schéma simple des principales étapes qui pourraient être présentes dans une ligne d'assemblage logicielle :

Brainstorming => dev => Testing => Deployment

diagramme de la ligne d'assemblage représentant 4 étapes en ligne avec des flèches pointant de l'une à l'autre : étape de brainstorming, étape de développement, étape de test, étape de déploiement

Pour ce défi, vous écrirez un composant Vue qui est un prototype initial d'un outil organisationnel à utiliser à des fins personnelles et professionnelles, basé sur le concept de ligne d'assemblage.

Après avoir terminé la programmation, vous devrez rédiger une réponse écrite (les détails sont fournis en bas des instructions).

Exigences fonctionnelles
Cette section contient les spécifications pour le composant. N'hésitez pas à passer brièvement à la capture d'écran de démonstration en bas de ces instructions, qui offre une représentation concrète du comportement que vous allez créer et qui pourrait aider à éclairer les descriptions écrites.

Props et saisie de noms d'éléments
Le composant AssemblyLine acceptera un tableau d'étapes dans ses props, qui correspondent aux noms de listes ordonnées séquentiellement par lesquelles les éléments passeront à mesure qu'ils progressent dans la ligne d'assemblage virtuelle. Chaque étape est une liste car elle peut contenir plus d'un élément à la fois. Les éléments peuvent être ajoutés à la première étape de la ligne d'assemblage au moyen d'une boîte de saisie qui peut être soumise avec la touche Entrée.

Déplacement des éléments entre les étapes
Une fois ajoutés, les éléments peuvent être cliqués par l'utilisateur pour être déplacés vers l'étape suivante. Si un élément se trouve dans la dernière étape et qu'il est cliqué, il est complètement supprimé. Conceptuellement, vous pourriez considérer qu'un élément qui progresse au-delà de la dernière étape correspond à une tâche terminée ou à un produit déployé.

Les éléments peuvent également être cliqués avec le bouton droit de la souris, ce qui les fait reculer vers l'étape précédente, et ils sont supprimés s'ils sont déplacés en arrière au-delà de la première étape. Conceptuellement, le fait de déplacer un élément en arrière jusqu'à sa suppression pourrait représenter une idée rejetée ou un produit défectueux qui n'a jamais franchi le processus d'assemblage.

Les éléments ne peuvent pas sauter d'étapes ou être supprimés en cours de route, ils doivent être déplacés complètement d'un bord ou de l'autre pour être retirés de la ligne d'assemblage.

De plus, lorsqu'un élément est déplacé en arrière vers l'étape précédente, il doit être ajouté à la liste des éléments actuellement présents à cette étape. Lorsqu'un élément est déplacé vers l'étape suivante, il doit être ajouté au début de la liste de sa nouvelle étape.

Rendu et comportement
Le composant doit rendre un certain nombre d'éléments que la suite de tests pourra utiliser, tous accessibles par data-testid et index (en particulier, le code de test récupérera la n-ième étape ou le n-ième élément dans une étape par data-testid). Voici la liste complète des éléments qui doivent être rendus, ainsi que leurs spécifications comportementales :

- Un élément HTML <input data-testid="assembly-add-item" /> doit être fourni pour la saisie. La suite de tests déclenchera un changement pour ajouter du texte et un événement keydown avec la touche Entrée pour soumettre la valeur. La valeur du champ de saisie, une fois la touche Entrée enfoncée, sera ajoutée au début de la liste des éléments de la première étape, et l'élément assembly-add-item sera effacé. Les éléments peuvent être ajoutés à tout moment.
- Une série d'enfants <div data-testid="assembly-stage"></div> doit être fournie, chacun représentant la n-ième étape correspondant à la ligne d'assemblage telle que définie par les étapes. Le nombre d'étapes sera égal à la longueur des étapes fournies au composant et restera fixe pendant un cycle de montage. stages[0] est le nom de la première étape et est le point d'entrée pour tous les éléments nouvellement créés par assembly-add-item, tandis que stages[props.stages.length-1] est le nom de la dernière étape. Vous pouvez supposer que les étapes ne seront jamais données sous forme de tableau vide (mais si vous avez le temps d'écrire une validation pour cela, c'est un bonus !). La suite de tests ne vérifiera pas que ces chaînes de caractères de nom d'étape ont été rendues, mais il est recommandé de le faire pour aider à identifier les étapes pendant votre travail.
- Une série d'éléments <button data-testid="assembly-item"></button>, qui représentent les éléments résidant dans une étape particulière. Le contenu textuel d'un assembly-item sera une chaîne provenant d'une soumission précédente de assembly-add-item. Comme décrit ci-dessus, ce bouton accepte les événements de clic gauche et de clic droit (menu contextuel), qui le font avancer ou reculer, respectivement, à travers les étapes de la ligne d'assemblage. Comme pour les étapes, le n-ième enfant assembly-item d'une liste devrait correspondre conceptuellement au n-ième élément de cette liste.
Pour une clarification supplémentaire, consultez le code de test dans le fichier tests/unit/AssemblyLine.test.jsx. Ce fichier contient tous les tests pour ce défi et peut être utilisé pour soutenir la spécification comportementale. Vous êtes invité à apporter des modifications à ce fichier pour vérifier que votre composant fonctionne, bien que le code de test original soit restauré lors de la soumission.




## Demo

Voici une capture d'écran illustrant la fonctionnalité du composant. Notez la différence entre un clic gauche (déplacer un élément vers la liste suivante) et un clic droit sur un élément (déplacer un élément vers la liste précédente), ainsi que l'emplacement où les éléments sont déplacés (les déplacements précédents ajoutent, tandis que les déplacements suivants insèrent au début).

Cette instance particulière du composant a été créée avec :

```
<AssemblyLine 
  stages={[
    "Idea", 
    "Development", 
    "Testing", 
    "Deployment"
  ]} 
/>

```


## Authors

- [@attoumbre](https://www.github.com/attoumbre)

