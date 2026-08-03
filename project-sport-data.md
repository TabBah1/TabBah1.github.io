[← Retour au portfolio](./index.md)

# POC Avantages Sportifs — Sport Data Solution

## Le problème

Une entreprise souhaite récompenser ses salariés actifs physiquement (primes, jours bien-être), mais le calcul de ces avantages à partir de données d'activité brutes était manuel, non supervisé et sans alerte en cas d'anomalie.

## Ce que j'ai fait

- J'ai conçu un pipeline automatisé de bout en bout calculant les avantages salariés à partir des données d'activité physique.
- J'ai mis en place une architecture streaming temps réel avec Redpanda (compatible Kafka), incluant un producteur et un consommateur avec notifications automatiques.
- J'ai orchestré l'exécution du pipeline avec Kestra, en planifiant un run hebdomadaire automatique et en journalisant chaque exécution.
- J'ai intégré un contrôle qualité des données automatisé avec Great Expectations.
- J'ai connecté des notifications Slack pour alerter l'équipe en cas d'anomalie détectée.
- J'ai construit un tableau de bord Power BI dédié au monitoring du pipeline.

## Résultat

Un pipeline qui tourne de façon autonome chaque semaine, avec une supervision automatisée qui évite d'avoir à vérifier manuellement chaque exécution.

## Stack

`PostgreSQL` · `Redpanda` (Kafka-compatible) · `Kestra` · `Great Expectations` · `Slack API` · `Power BI`

## Preuve

→ [Code source complet sur GitHub](https://github.com/TabBah1/Sport_data_poc)
