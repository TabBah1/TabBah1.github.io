[← Retour au portfolio](./index.md)

# Puls-Events — Assistant RAG culturel

## Le problème

Puls-Events est une plateforme qui recense des événements culturels en temps réel. Une recherche par mots-clés classique ne comprend pas qu'une requête sur le "jazz" pourrait aussi correspondre à de la "musique improvisée". Un LLM seul, lui, connaît mal les événements récents et peut inventer des événements qui n'existent pas. Je voulais un système qui comprenne des requêtes en langage naturel tout en restant ancré dans des données réelles, sans halluciner.

## Ce que j'ai fait

- J'ai collecté environ 500 événements culturels parisiens via l'API publique Open Agenda (OpenDataSoft), en filtrant sur la ville et une fenêtre de 12 mois.
- J'ai nettoyé et structuré ces données avec Pandas, puis construit des textes d'indexation enrichis par événement (titre, catégorie, description, lieu, dates).
- J'ai découpé ces textes en chunks (500 caractères, overlap 50) avec LangChain, puis généré les embeddings via l'API Mistral.
- J'ai indexé ces vecteurs dans FAISS et construit une chaîne RAG complète (retriever top-k=5 → prompt anti-hallucination → génération Mistral, temperature 0.3).
- J'ai écrit une suite de 8 tests unitaires (pytest) validant l'intégrité des données et la cohérence de l'index vectoriel, ainsi qu'un script d'évaluation sur un jeu de questions annotées.

## Résultat

Le chatbot répond en français, sans halluciner, en citant des événements réels avec leurs dates, lieux et descriptions — y compris sur des requêtes combinant plusieurs critères ("poétique, insolite et intimiste").

## Stack

`LangChain` · `FAISS` (CPU) · `Mistral AI` (LLM + embeddings) · `Python 3.11` · `pytest`

## Preuve

→ [Code source complet sur GitHub](https://github.com/TabBah1/Puls-events)
