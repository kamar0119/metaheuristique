# Analyse des Algorithmes de Bin Packing

## Introduction

Le problème de bin packing consiste à placer un ensemble d'objets de différentes tailles dans un nombre minimum de conteneurs (bins) de taille fixe. Les algorithmes heuristiques et de recherche sont couramment utilisés pour résoudre ce problème. Dans cette analyse, nous évaluons trois algorithmes : l'Heuristique FBS, la Recherche Locale, et la Recherche à Voisinage Variable (VNS).

## Algorithmes

### Heuristique FBS (Finite Best Strip)

L'heuristique FBS est un algorithme qui tente de minimiser le nombre de conteneurs en deux phases :
1. **Phase 1 : Emballage des objets en bandes de hauteur infinie**
    - Les objets sont triés par hauteur décroissante.
    - Chaque objet est placé sur l'étagère (shelf) où il reste le moins de largeur, sinon une nouvelle étagère est créée.
2. **Phase 2 : Emballage des étagères dans des conteneurs de taille finie**
    - Les étagères sont placées dans des conteneurs en essayant de minimiser l'espace inutilisé.

### Recherche Locale

La recherche locale est une méthode d'optimisation itérative qui cherche à améliorer une solution initiale par des modifications locales :
- **Initialisation** : Une solution initiale est générée en plaçant les objets aléatoirement dans les conteneurs.
- **Évaluation** : La solution est évaluée en termes de fitness, qui combine le nombre de conteneurs utilisés et l'espace gaspillé.
- **Recherche** : À chaque itération, une solution voisine est générée et évaluée. Si elle est meilleure, elle remplace la solution courante.

### Recherche à Voisinage Variable (VNS)

La recherche à voisinage variable combine des techniques de diversification et d'intensification :
- **Initialisation** : Utilise une solution de la recherche locale.
- **Shaking** : Perturbe la solution en déplaçant aléatoirement des objets pour explorer de nouvelles configurations.
- **Recherche Locale** : Applique la recherche locale à la solution perturbée.
- **Diversification** : Échange aléatoirement des objets entre différentes positions pour éviter les minima locaux.

## Données Utilisées

Les données suivantes ont été utilisées pour les tests :

```plaintext
W: 10
H: 10

w: 5, h: 9
w: 4, h: 2
w: 10, h: 6
w: 5, h: 7
w: 6, h: 3
w: 10, h: 7
w: 1, h: 5
w: 3, h: 5
w: 6, h: 9
w: 2, h: 4
w: 6, h: 7
w: 7, h: 2
w: 8, h: 3
w: 4, h: 10
w: 4, h: 5
w: 10, h: 3
w: 7, h: 8
w: 8, h: 7
```

## Résultats des Algorithmes

Les résultats obtenus sont les suivants :

- **Heuristique FBS** :
  - Nombre de conteneurs utilisés = 1
  - Temps d'exécution = 0.0000s

- **Recherche Locale** :
  - Fitness = 0.0
  - Temps d'exécution = 0.0088s

- **VNS** :
  - Fitness = 10.83
  - Temps d'exécution = 0.0590s

## Analyse des Résultats

### Heuristique FBS

L'heuristique FBS a été très efficace, utilisant un seul conteneur avec un temps d'exécution extrêmement rapide (0.0000s). Cela montre que l'algorithme est capable de trouver une solution optimale de manière très efficace pour les données fournies. Son approche en deux phases permet de minimiser le nombre de conteneurs tout en restant rapide.

### Recherche Locale

La recherche locale a également donné d'excellents résultats avec une valeur de fitness de 0.0, indiquant une optimisation complète de l'espace. Cependant, elle a pris plus de temps (0.0088s) par rapport à l'heuristique FBS. Cela est dû au fait que la recherche locale itère plusieurs fois pour améliorer la solution, ce qui prend plus de temps mais permet d'atteindre une solution très optimisée.

### VNS (Variable Neighborhood Search)

La VNS a montré une valeur de fitness de 10.83, suggérant qu'il y avait encore de l'espace gaspillé. Son temps d'exécution de 0.0590s est le plus long parmi les trois algorithmes testés. La VNS est une méthode puissante dans des contextes plus variés et complexes car elle combine diversification et intensification. Cependant, pour ce cas particulier de bin packing, elle s'est révélée moins efficace en termes de temps d'exécution et d'utilisation de l'espace.

## Conclusion

En résumé, l'Heuristique FBS s'avère être la plus performante en termes d'efficacité et de rapidité pour ce problème spécifique de bin packing. La recherche locale, bien qu'un peu plus lente, offre une excellente optimisation de l'espace. La VNS, bien que polyvalente et potentiellement plus robuste dans d'autres contextes, est moins optimale pour ce cas particulier en raison de son temps d'exécution plus long et de l'optimisation de l'espace moins efficace.

### Recommandations

- **Heuristique FBS** : À utiliser lorsque la rapidité est cruciale et que les données sont similaires à celles fournies.
- **Recherche Locale** : À utiliser lorsque l'optimisation de l'espace est une priorité, même au coût d'un temps de calcul légèrement plus élevé.
- **VNS** : À considérer pour des problèmes plus complexes où la robustesse et la flexibilité sont nécessaires, malgré un compromis sur le temps d'exécution et l'efficacité.