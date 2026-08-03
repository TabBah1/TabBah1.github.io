[← Retour au portfolio](./index.md)

# Migration de données médicales vers MongoDB

## Le problème

Un jeu de données médicales de près de 55 000 dossiers patients existait sous forme de CSV plat — difficile à interroger efficacement, sans structure hiérarchique naturelle, et sans contrôle d'accès différencié selon le rôle de la personne qui consulte les données (un enjeu critique en contexte médical).

## Ce que j'ai fait

- J'ai conçu un pipeline ETL en Python (Pandas, PyMongo) migrant 54 966 documents patients d'un CSV vers une base NoSQL documentaire.
- J'ai identifié et supprimé 534 doublons durant la phase de nettoyage.
- J'ai modélisé un schéma en documents imbriqués (patient / medical / admission / billing / staff) plutôt qu'une structure plate, pour refléter les relations réelles entre les données.
- J'ai conteneurisé toute la base avec Docker / Docker Compose pour un déploiement reproductible.
- J'ai mis en place une politique de sécurité RBAC à 4 niveaux d'accès (Admin, Medical Editor, Medical Viewer, Doctor Restricted), avec gestion des secrets via `.env`.
- J'ai audité les performances des requêtes après indexation : une recherche typique s'exécute en moins de 3 ms sur l'ensemble des 55 000 documents.

## Résultat

Une base NoSQL sécurisée, performante et prête pour un usage en production, avec une séparation claire des droits d'accès selon le profil de l'utilisateur.

## Stack

`Python` · `MongoDB` · `PyMongo` · `Docker` / `Docker Compose`

## Preuve

→ [Code source complet sur GitHub](https://github.com/TabBah1/Migrez-des-donnees-medicales-a-l-aide-du-NoSQL)
