[← Retour au portfolio](./index.md)

# InduTechData POC — Pipeline temps réel

## Le problème

Une entreprise industrielle reçoit un flux continu de tickets clients qui doivent être traités, enrichis et stockés sans latence ni perte de données — y compris en cas d'arrêt brutal du pipeline. Il fallait concevoir une architecture capable d'ingérer, transformer et router ces tickets en continu, tout en restant tolérante aux pannes.

## Ce que j'ai fait

- J'ai conçu un pipeline de streaming structuré de bout en bout : un producteur génère les tickets, Redpanda (compatible Kafka) sert de broker de messages, et PySpark Structured Streaming assure le traitement.
- J'ai écrit la logique d'enrichissement à la volée (routage automatique par type de demande, agrégations en temps réel).
- J'ai mis en place le double stockage : PostgreSQL pour les données relationnelles et des fichiers analytiques pour les usages en aval.
- J'ai implémenté le checkpointing Spark pour garantir une reprise exacte après un arrêt brutal, sans duplication de données.
- J'ai entièrement conteneurisé l'architecture (Docker / Docker Compose) et documenté une correspondance explicite POC → Cloud (Redpanda→MSK, PySpark→EMR, PostgreSQL→Redshift, fichiers→S3), pour anticiper une migration vers AWS.

## Résultat

Un pipeline reproductible localement, capable de survivre à un redémarrage sans perte ni doublon, avec une trajectoire de migration Cloud déjà pensée.

## Stack

`Redpanda` (Kafka-compatible) · `PySpark` (Structured Streaming) · `PostgreSQL` · `Docker` / `Docker Compose`

## Preuve

→ [Code source complet sur GitHub](https://github.com/TabBah1/InduTechData_POC)
