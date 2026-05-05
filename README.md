# 💰 Optimisation Prix E-commerce

> Analyse de l'élasticité prix sur 100k commandes pour maximiser le CA d'une marketplace brésilienne.

## 📊 Résultats

| Métrique | Valeur |
|---|---|
| CA actuel | 12 947 451 R$ |
| CA optimisé | 15 371 613 R$ |
| **Gain estimé** | **+2 424 162 R$ (+18.7%)** |
| Gain garanti à 95% | +2 026 576 R$ (+15.7%) |
| Objectif initial | +15% ✅ |
| Catégories analysées | 53 |
| Catégories opportunités | 42 (79%) |

## 🗂️ Dataset

- **Source** : [Brazilian E-Commerce - Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
- **Volume** : 108 660 commandes nettoyées, 73 catégories
- **Période** : 2016-2018

## 🛠️ Stack technique

- **Python** : pandas, numpy, scikit-learn, scipy, matplotlib, seaborn
- **Modèles** : Régression linéaire, Random Forest
- **Imputation** : MICE (Multiple Imputation by Chained Equations)
- **Optimisation** : scipy.optimize
- **Dashboard** : Power BI

## 📓 Structure du projet

    ecommerce-pricing/
    ├── notebooks/
    │   ├── 01_exploration.ipynb       # Exploration des données
    │   ├── 02_nettoyage.ipynb         # Nettoyage et préparation
    │   ├── 03_elasticite.ipynb        # Calcul élasticité prix
    │   ├── 04_optimisation.ipynb      # Optimisation des prix
    │   ├── 05_simulation_ab.ipynb     # Simulation A/B tests
    │   └── 06_modele_ameliore.ipynb   # Random Forest + score confiance
    ├── outputs/                       # Graphiques et dashboard
    ├── requirements.txt               # Dépendances Python
    └── README.md

## 🎯 Méthodologie

### 1. Exploration & Nettoyage
- 99 441 commandes → 108 660 lignes après fusion des tables
- Suppression des commandes non livrées (2 963)
- Imputation MICE pour les 815 notes clients manquantes
- Traduction des 73 catégories du portugais vers le français

### 2. Calcul de l'élasticité prix
- Régression linéaire log-log par catégorie
- Segmentation en 10 tranches de prix par catégorie
- Résultat : élasticités entre 0 et -0.17 → marché peu sensible aux prix

### 3. Optimisation des prix
- Maximisation du CA via scipy.optimize
- Contrainte : hausse maximale de +20%
- Résultat : +18.7% de CA potentiel

### 4. Validation par simulation A/B
- 10 000 simulations Monte Carlo par catégorie
- Probabilité de gain : 100% pour toutes les catégories
- Gain minimum garanti à 95% : +2 026 576 R$

### 5. Modèle amélioré (Random Forest)
- Intégration de 3 variables : prix, note client, ratio livraison
- Imputation MICE pour les valeurs manquantes
- R² moyen : 0.300 → 0.761 (+153%)
- Découverte clé : la note client (46.8%) est plus importante que le prix (28.2%)

## 💡 Insights business

1. **79% des catégories** sont peu sensibles aux prix → fort potentiel d'augmentation
2. **La note client est le levier principal** (46.8% d'importance) — plus que le prix
3. **Les frais de livraison** influencent autant les ventes que le prix (25% vs 28%)
4. **Top 3 priorités** : Beauté & Santé (+243k R$), Montres & Cadeaux (+230k R$), Literie (+199k R$)

## ⚠️ Catégories à ne pas toucher

| Catégorie | Élasticité | Raison |
|---|---|---|
| Outils & Bricolage | -0.172 | Trop sensible au prix |
| Chaussures | -0.159 | Trop sensible au prix |
| Outils & Jardin | -0.122 | Trop sensible au prix |
| Lingerie & Maillots | -0.122 | Trop sensible au prix |
| Confort Maison | -0.109 | Trop sensible au prix |

## 🚀 Installation

```bash
# Cloner le repo
git clone https://github.com/Dboy003/Ecommerce-pricing.git
cd Ecommerce-pricing

# Créer l'environnement virtuel
python -m venv venv
venv\Scripts\activate  # Windows

# Installer les dépendances
pip install -r requirements.txt

# Télécharger le dataset
# https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce
# Placer les CSV dans le dossier data/
```

## 📈 Dashboard Power BI

Le dashboard interactif contient 4 pages :
- **Vue Globale** : KPIs et CA actuel vs optimisé
- **Recommandations** : Prix optimaux et scores de confiance
- **Élasticité** : Analyse de sensibilité par catégorie
- **Simulation A/B** : Validation statistique des recommandations

## 🔮 Améliorations futures

- Intégrer la saisonnalité dans le modèle
- Ajouter les données de la concurrence
- Analyse géographique par région brésilienne
- Déploiement d'une API de recommandation de prix en temps réel

---

*Projet réalisé avec le dataset Brazilian E-Commerce Public Dataset by Olist*