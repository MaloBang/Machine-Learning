# Machine-Learning

Un premier travail de Machine Learning sur une régression linéaire multiple pour la prévision d'un prix selon plusieurs variables exogènes.  
Une base de données nous est fournie, et nous devons réaliser la prévision de 4 variables manquantes.

## I- Exploration des données :

Le dataset contient plusieurs colonnes. Voici leur signification métier :

- **id** : Identifiant unique pour chaque maison vendue  
- **date** : Date de la vente de la maison  
- **price** : Prix de chaque maison vendue  
- **bedrooms** : Nombre de chambres  
- **bathrooms** : Nombre de salles de bains, où 0.5 correspond à une pièce avec des toilettes mais sans douche  
- **sqft_living** : Surface habitable intérieure de l’appartement (en pieds carrés)  
- **sqft_lot** : Surface du terrain (en pieds carrés)  
- **floors** : Nombre d’étages  
- **waterfront** : Variable binaire indiquant si l’appartement a une vue sur l’eau ou non  
- **view** : Indice de 0 à 4 indiquant la qualité de la vue de la propriété  
- **condition** : Indice de 1 à 5 indiquant l’état général de l’appartement  
- **grade** : Indice de 1 à 13 où :
  - 1-3 désigne une construction et un design de qualité insuffisante  
  - 7 correspond à une construction et un design de qualité moyenne  
  - 11-13 désignent une construction et un design de haute qualité  
- **sqft_above** : Surface habitable intérieure au-dessus du niveau du sol (en pieds carrés)  
- **sqft_basement** : Surface habitable intérieure située au sous-sol (en pieds carrés)  
- **yr_built** : Année de construction initiale de la maison  
- **yr_renovated** : Année de la dernière rénovation de la maison  
- **zipcode** : Code postal de la zone où se trouve la maison  
- **lat** : Latitude  
- **long** : Longitude  
- **sqft_living15** : Surface habitable intérieure des 15 voisins les plus proches (en pieds carrés)  
- **sqft_lot15** : Surface des terrains des 15 voisins les plus proches (en pieds carrés)  

La base fournie est déjà nettoyée : il n'y a pas de valeurs aberrantes ni de cellules vides, à part les 4 à prévoir.  
Seule la colonne `date` a été traitée pour pouvoir être incluse dans le modèle de régression.  
Une nouvelle base de données sans les lignes contenant des cellules vides a été créée afin de pouvoir entraîner notre modèle.

---

## II- Manipulation des données :

### 1. Test statistique 

- Visualisation de la matrice de corrélation.  
- Test de Student (non abouti).  

Ces deux étapes ont pour but de créer un modèle logique.

### 2. Modèle initial 

- **Premier modèle de régression avec toutes les variables du dataset**  
- Score pour le dataset d'entraînement : **70,28%**  
- Score pour le dataset de test : **69,61%**  

Le R² est de **70,28%**, ce qui signifie que dans ce modèle, nous expliquons **70,28% de la dispersion**.  
Autrement dit, nos variables exogènes expliquent la variable endogène à **70,28%**.  
Ce modèle est donc déjà rigoureux.

### 3. Modèle 2

- **Modèle de régression avec les variables dont les tests statistiques démontrent des corrélations et une implication logique.**  
- Score pour le dataset d'entraînement : **64,14%**  
- Score pour le dataset de test : **63,87%**  

Le R² est de **64,14%**, ce qui signifie que dans ce modèle, nous expliquons **64,14% de la dispersion**.  
Ce modèle semble moins performant que le modèle initial, mais la pertinence des variables exogènes est à considérer.

### 4. Modèle logarithmique initial

- **Premier modèle de régression avec le dataset transformé par la fonction logarithme népérien.**  
- Certaines variables ont été écartées (valeurs négatives ou égales à 0), bien qu’un retravail de ces variables aurait pu être effectué.  
- Score pour le dataset d'entraînement : **76,61%**  
- Score pour le dataset de test : **77,21%**  

Le R² est de **76,61%**, ce qui signifie que dans ce modèle, nous expliquons **76,61% de la dispersion**.  
Ce modèle semble plus pertinent que le modèle initial.

### 5. Modèle logarithmique 2

- **Modèle de régression basé sur le modèle logarithmique initial, avec retrait des variables identifiées comme non pertinentes.**  
- Score pour le dataset d'entraînement : **72,03%**  
- Score pour le dataset de test : **72,28%**  

Le R² est de **72,03%**, ce qui signifie que dans ce modèle, nous expliquons **72,03% de la dispersion**.  
Ce modèle est encore plus pertinent que le modèle initial.

---

## III- Prévision :

Le **modèle logarithmique initial** a été choisi pour la prévision des valeurs manquantes, car il obtient la meilleure dispersion expliquée.  
(L’écart-type et le critère AIC auraient pu être comparés entre les modèles, et un test de White aurait pu être réalisé sur les modèles.)  

La pertinence des prévisions est observée sur 4 graphiques différents et semble bonne.
