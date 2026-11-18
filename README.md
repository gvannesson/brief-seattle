# Brief Seattle — Prédiction de la consommation d'énergie et des émissions de CO2

Projet de formation Data Engineer — **Groupe 1** : BALESTRA Antonio, SRIRANJAN Vinuisaa, VANNESSON Gauthier.

## Contexte

La ville de Seattle vise la neutralité carbone en 2050. À partir des relevés de 2016 sur les bâtiments **non destinés à l'habitation**, l'objectif est de :

1. prédire les **émissions de CO2** (`TotalGHGEmissions`) et la **consommation totale d'énergie** (`SiteEnergyUse(kBtu)`) des bâtiments pas encore mesurés ;
2. évaluer l'intérêt de l'**ENERGY STAR Score** pour la prédiction des émissions.

## Structure du dépôt

```
.
├── data/
│   └── raw/                       # Données brutes (2016 Building Energy Benchmarking)
├── notebooks/
│   └── 00_description_variables.ipynb   # Résumé des variables (fourni)
├── slides/                        # Support de la présentation orale
├── pyproject.toml                 # Dépendances (gérées avec uv)
├── uv.lock                        # Versions exactes verrouillées
└── README.md
```

## Démarche

- Analyse exploratoire et nettoyage (erreurs, valeurs manquantes, outliers, filtrage des bâtiments non résidentiels)
- Encodage des variables catégorielles
- Réduction de dimensionnalité
- Comparaison d'au moins 3 modèles de régression
- Vérification du sur/sous-apprentissage
- Optimisation des hyperparamètres du modèle retenu (gain mesuré vs modèle par défaut)
- Évaluation de l'apport de l'ENERGY STAR Score

## Installation et exécution

Le projet utilise [uv](https://docs.astral.sh/uv/) pour gérer Python et les dépendances.

```bash
# Installer uv si besoin
curl -LsSf https://astral.sh/uv/install.sh | sh     # Windows : powershell -c "irm https://astral.sh/uv/install.ps1 | iex"

git clone https://github.com/gvannesson/brief-seattle.git
cd brief-seattle
uv sync                      # crée .venv et installe les versions exactes de uv.lock
uv run jupyter notebook
```

Avec VS Code, sélectionner le kernel `.venv` du projet après `uv sync`.

Ajouter une dépendance : `uv add <paquet>` (puis committer `pyproject.toml` et `uv.lock`).

Les notebooks utilisent un `random_state` fixé pour garantir la reproductibilité.

## Source des données

[Seattle Open Data — 2016 Building Energy Benchmarking](https://data.seattle.gov/)
