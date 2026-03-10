# DEFT2013 Tâche 2 
HAMONO Ewen - CHEVREUX Arthur

## Organisation du projet
    Le projet est composé de 2 dossier : data et src.
    data contient toutes les données utilisées pour ce projet.
    src contient 3 notebook. Un notebook pour l'exploration des données, un pour la baseline et un avec les différentes méthodes.

## Description de la tâche
    Le but de ce projet est d'utiliser un modèle pour prédire le type de plat correspondant à un document. Un document d'entrainement est composé d'un identifiant, un titre de recette, un type de plat, une difficulté, un ordre de prix, des ingrédients et une recette. Pour les tests on retire la colonne du type de plat. On a trois type de plat : Entrée, Plat principale et Dessert. 
    Exemple de document :


    recette_221358.xml,"Feuilleté de saumon et de poireau, sauce aux crevettes",Plat principal,Facile,Moyen,"- 1 gros pavé de saumon - 100 g de crevettes décortiquées - 2 poireaux moyens - 1 oignon  - 1 pâte feuilletée - 25 cl de crème liquide épaisse - Un peu de vin blanc - 1/2 citron jaune - 1 jaune d'oeuf - Un peu d'huile d'olive  - Une noisette de beurre - Sel, aneth","Couper finement le blanc et un peu de vert des poireaux en rondelle. Éplucher et couper l'oignon. Faire chauffer l'huile d'olive et le beurre dans une poêle. Y faire revenir à feu doux les poireaux et l'oignon environ 15 minutes. En fin de cuisson ajouter le vin blanc, un peu d'aneth et du sel. Pendant ce temps faire cuire le saumon dans une poêle huilée. En fin de cuisson le faire griller sur feu vif. Préparer la sauce : mélanger les crevettes, le 1/2 citron jaune, la crème, le sel et l'aneth. Ajouter un peu de sauce à la préparation des poireaux. Préchauffer le four à 200°C (thermostat 6-7.Étaler la pâte feuilletée et la couper en 2. Sur une moitié disposer la préparation au poireaux. Disposer le saumon sur les poireaux. Y verser un peu de sauce sur le dessus (garder le reste de sauce au frigo). Refermer le chausson à l'aide de l'autre moitié de la pâte feuilleté. Bien appuyer sur les bords. Étaler le jaune d’œuf sur le dessus à l'aide d'un pinceau. Enfourner environ 20 minutes. Avant de servir chauffer la sauce et la servir à côté du feuilleté.On peut servir ce feuilleté avec une salade verte."

    recette_71424.xml,Gâteau au yaourt au coco sans huile de laetitia,Dessert,Très facile,Bon marché,- 1 pot de yaourt - 1 pot de lait de coco - 3 oeufs - 1 pot de coco râpée - 3 pots de farine - 2 pots de sucre - 1 pincée de sel - 1 sachet de levure,"Mélanger dans l'ordre tous les ingrédients en prenant le pot de yaourt comme mesure. Mettre la préparation dans un moule et l'enfourner à 180°, thermostat 6, pendant 45 min. Ce dessert s'accompagne très bien d'une boule de glace vanille ou coco pour les gourmands."


## Statistiques corpus
	Dans le corpus on retrouve 12 473 documents d'entrainement et 1 388 documents de test.
    Dans le corpus d'entrainement on retrouve 5 802 plats principaux, 3 762 desserts et 2 909 entrées.
    Pour le corpus de test on retrouve  plats principaux,  desserts et  entrées.

## Méthodes proposées

### Run1: baseline (méthode de référence)
    Pour les deux méthodes de baseline (majoritaire et aléatoire), nous n'avons utilisé aucun descripteur ou classifieur.
    La méthode majoritaire renvoie toujours "Plat principal" qui est le type de plat le plus présent.
    La méthode aléatoire renvoie un type au hasard en suivant la seed 42.

### Run2: TF-IDF et naïve Bayes
    Pour cette méthode on utilise TF-IDF en descripteur puis naïve Bayes en classifieur.

### Run3: Modèle linéaire avec SVM
    Pour cette méthode on utilise TF-IDF en descripteur puis SVM en modèle linéaire comme classifieur.

### Run4: Modèle linéaire avec régression logistique
    Pour cette méthode on utilise TF-IDF en descripteur puis une regression logistique comme classifieur.

### Run5: Modèle enrichi
    Pour cette méthode on utilise TF-IDF avec un minMaxScaler, pour normer la taille des vecteurs, en descripteur une regression logistique comme classifieur.

## Résultats
| Run      | Micro f1 | Macro f1 |

| -------- |  -------- | --------:|

| baseline majoritaire |  46%  |  21%  |

| baseline aléatoire |  33%  |  32%  |

| METH 1   |  80%  |  74%  |

| METH 2A   |  88%  |  87%  |

| METH 2B   |  86%  |  84%  |

| METH 3   |  88%  |  87%  |


### Réflexion critique
    La difficulté dans le projet est de devoir séparer des recettes de plats principaux et d'entrées. Même manuellement il est parfois difficile de se prononcer sur le type de plat qu'est la recette. Cependant les desserts sont facilement séparables des deux autres catégories. Dans notre cas, la métrique macro-F1 est intéressante car elle prend en compte les performances de chaque classe de façon individuelle. Cependant, comme nos classes ne sont pas fortement déséquilibrées, les scores micro-F1 et macro-F1 sont très proches. Nos modèles semblent bien généraliser car nos Micro f1 sont entre 80% et 88% pour les différentes méthodes alors que nous utilisons des données de tests, qui n'ont donc jamais été vu par nos modèles.