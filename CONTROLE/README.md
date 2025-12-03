# ERROUYAS AYA
<img src="AYA.jpeg" style="height:150px;margin-right:100px"/>

# CONTROLE

# Analyse et Modélisation des Données Financières



## 📋 Table des Matières

- [Description du Projet](#-description-du-projet)
- [Problématique](#-problématique)
- [Dictionnaire des Données](#-dictionnaire-des-données)
- [Architecture du Projet](#-architecture-du-projet)
- [Installation](#-installation)
- [Utilisation](#-utilisation)
- [Résultats Principaux](#-résultats-principaux)
- [Méthodologie](#-méthodologie)
- [Technologies Utilisées](#-technologies-utilisées)
- [Auteur](#-auteur)

---

##  Description du Projet

Ce projet implémente un **pipeline end-to-end** d'analyse de données financières, incluant :

-  **Prétraitement automatisé** : gestion des valeurs manquantes, doublons, encodage
-  **Analyse exploratoire approfondie** : statistiques descriptives, visualisations, corrélations
-  **Feature Engineering avancé** : création de variables dérivées (ratios, interactions, agrégations)
-  **Modélisation prédictive** : régression linéaire et classification logistique
-  **Évaluation rigoureuse** : métriques de performance et validation croisée

Le code est **modulaire, documenté et reproductible**, conçu pour faciliter l'adaptation à d'autres datasets financiers.

---

##  Problématique

### Type de Tâche
Ce projet traite à la fois :
- **Régression** : prédiction de variables continues (ex: prix, rendements)
- **Classification binaire** : prédiction de catégories (ex: hausse/baisse, défaut/non-défaut)

### Objectifs
1. Identifier les **facteurs clés** influençant les variables financières
2. Développer des **modèles prédictifs performants** pour aider à la décision
3. Fournir des **insights exploitables** via l'analyse exploratoire

---

##  Dictionnaire des Données

### Dataset Source
- **Nom** : Finance Data
- **Source** : [Kaggle - nitindatta/finance-data](https://www.kaggle.com/datasets/nitindatta/finance-data)
- **Taille initiale** : Variable selon le dataset (affichée lors de l'exécution)

### Types de Variables
| Catégorie | Description | Traitement |
|-----------|-------------|------------|
| **Numériques** | Variables continues (prix, volumes, ratios) | Imputation KNN + Standardisation |
| **Catégorielles** | Variables qualitatives (secteur, type) | Label/One-Hot Encoding |
| **Target** | Variable cible (dernière colonne par défaut) | Selon la tâche (régression/classification) |

### Métadonnées
- **Features** : Toutes les colonnes sauf la dernière
- **Target** : Dernière colonne du dataset (personnalisable)
- **Valeurs manquantes** : Gérées automatiquement par imputation intelligente

---

##  Architecture du Projet

```
finance-analysis/
│
├── README.md                          # Ce fichier
├── requirements.txt                   # Dépendances Python
├── finance_analysis.py                # Script principal
│
├── outputs/                           # Dossier des résultats
│   ├── finance_data_preprocessed.csv  # Données nettoyées
│   ├── missing_values_analysis.png    # Visualisation valeurs manquantes
│   ├── distributions_histograms.png   # Histogrammes
│   ├── distributions_boxplots.png     # Boxplots
│   ├── correlation_heatmap.png        # Matrice de corrélation
│   ├── model_regression.pkl           # Modèle de régression sauvegardé
│   └── model_classification.pkl       # Modèle de classification sauvegardé
│
└── report/
    └── compte_rendu.md                # Rapport scientifique
```

---

##  Installation

### Prérequis
- Python 3.8 ou supérieur
- pip (gestionnaire de paquets Python)

### Étapes d'Installation

```bash
# 1. Cloner le dépôt (ou télécharger les fichiers)
git clone https://github.com/votre-username/finance-analysis.git
cd finance-analysis

# 2. Créer un environnement virtuel (recommandé)
python -m venv venv

# Activer l'environnement
# Sur Windows :
venv\Scripts\activate
# Sur macOS/Linux :
source venv/bin/activate

# 3. Installer les dépendances
pip install -r requirements.txt

# 4. Configuration Kaggle (pour télécharger le dataset)
# Placez votre fichier kaggle.json dans ~/.kaggle/
# Téléchargez-le depuis : https://www.kaggle.com/settings/account
```

---

##  Utilisation

### Exécution Complète

```bash
python finance_analysis.py
```

### Résultats Générés
Après exécution, vous obtiendrez :
-  **Console** : Statistiques détaillées et métriques
-  **Visualisations** : 4 graphiques PNG sauvegardés
-  **Données prétraitées** : `finance_data_preprocessed.csv`
-  **Modèles entraînés** : `model_regression.pkl` et `model_classification.pkl`

### Personnalisation

Pour utiliser votre propre variable cible :

```python
# Modifier dans le script (ligne ~350)
target_column = 'votre_colonne_cible'  # Au lieu de df_features.columns[-1]
```

---

##  Résultats Principaux

### Prétraitement
- **Doublons supprimés** : Variable (affiché lors de l'exécution)
- **Valeurs manquantes** : Imputation complète via KNN et mode
- **Variables encodées** : Label Encoding et One-Hot Encoding
- **Features finales** : Augmentées via feature engineering (+ratios, +interactions)

### Analyse Exploratoire
| Insight | Résultat |
|---------|----------|
| **Corrélations fortes** | Identifiées dans la heatmap (valeurs > 0.7) |
| **Outliers détectés** | Visibles dans les boxplots |
| **Distributions** | Asymétries et normalités analysées |

### Performance des Modèles

#### Régression Linéaire
```
Métriques (exemple) :
- MSE (Mean Squared Error) : [affiché lors de l'exécution]
- R² (Coefficient de détermination) : [affiché lors de l'exécution]
- CV Score moyen : [validation croisée 5-folds]
```

#### Classification Logistique
```
Métriques (exemple) :
- Accuracy : [affiché lors de l'exécution]
- Precision / Recall / F1-Score : [voir classification report]
- Matrice de confusion : [visualisation des erreurs]
```

### Visualisations Clés

1. **Missing Values Analysis** : Identification des colonnes problématiques
2. **Distributions** : Histogrammes révélant la forme des données
3. **Boxplots** : Détection des valeurs aberrantes
4. **Heatmap de Corrélation** : Relations entre variables (rouge = positive, bleu = négative)

---

##  Méthodologie

### 1. Prétraitement
- **Doublons** : Suppression automatique
- **Valeurs manquantes** :
  - Numériques → KNN Imputer (k=5, weighted by distance)
  - Catégorielles → Mode (valeur la plus fréquente)
- **Encodage** :
  - Binaire → Label Encoding
  - Faible cardinalité (≤10) → One-Hot Encoding
  - Haute cardinalité → Label Encoding

### 2. Feature Engineering
- **Ratios** : Captures des relations proportionnelles
- **Interactions** : Produits entre variables (effets combinés)
- **Agrégations** : Sommes, moyennes, écarts-types par ligne

### 3. Normalisation
- **StandardScaler** : Moyenne = 0, Écart-type = 1
- Justification : Évite la dominance des variables à grande échelle dans les modèles

### 4. Modélisation
- **Split 80/20** : Train/Test pour évaluation honnête
- **Validation croisée** : 5-folds pour robustesse
- **Choix des algorithmes** :
  - Linear Regression : Baseline pour la régression
  - Logistic Regression : Baseline pour la classification

---

##  Technologies Utilisées

| Technologie | Usage |
|-------------|-------|
| **Python 3.8+** | Langage principal |
| **pandas** | Manipulation de données |
| **NumPy** | Calculs numériques |
| **Matplotlib / Seaborn** | Visualisations |
| **scikit-learn** | Machine Learning |
| **KaggleHub** | Téléchargement de datasets |
| **joblib** | Sérialisation des modèles |

---

##  Rapport Scientifique

Un compte rendu détaillé au format Markdown est disponible dans `report/compte_rendu.md`, incluant :
- Introduction et contexte
- Méthodologie justifiée
- Résultats et discussion approfondie
- Conclusion et pistes d'amélioration

---

##  Contribution

Les contributions sont les bienvenues ! Pour contribuer :
1. Forkez le projet
2. Créez une branche (`git checkout -b feature/amelioration`)
3. Committez vos changements (`git commit -m 'Ajout d'une fonctionnalité'`)
4. Pushez vers la branche (`git push origin feature/amelioration`)
5. Ouvrez une Pull Request


