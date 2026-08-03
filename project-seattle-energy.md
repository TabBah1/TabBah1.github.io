[← Retour au portfolio](./index.md)

# Prédiction de consommation énergétique — Ville de Seattle

## Le problème

La ville de Seattle vise la neutralité carbone et souhaite prédire la consommation énergétique de ses bâtiments non résidentiels à partir de leurs seules caractéristiques structurelles (surface, âge, usage), sans avoir besoin de relever leur consommation réelle — un préalable coûteux et lent à obtenir à grande échelle.

## Ce que j'ai fait

- J'ai comparé plusieurs modèles de Machine Learning (Régression Linéaire, Random Forest, SVR) et diagnostiqué leur tendance au sur-apprentissage.
- J'ai optimisé les hyperparamètres du modèle retenu (SVR) via GridSearchCV.
- J'ai validé le modèle final sur un jeu de test indépendant, atteignant un R² de 0,69.
- J'ai déployé ce modèle sous forme d'API avec BentoML, avec validation des données d'entrée via Pydantic pour garantir la robustesse du service en production.

## Résultat

Une API de prédiction fonctionnelle capable d'estimer la consommation énergétique d'un bâtiment à partir de ses caractéristiques déclaratives, sans données de consommation historiques.

## Stack

`Scikit-Learn` (SVR, GridSearchCV) · `Pandas` · `BentoML` · `Pydantic`

## Preuve

→ [Code source complet sur GitHub](https://github.com/TabBah1/Seattle-Energy-Prediction)
