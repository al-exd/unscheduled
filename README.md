# cve-lens

Explorer, filtrer et analyser les vulnérabilités connues (CVE) à partir de la base de données publique du NVD (NIST).

**Statut :** MVP en cours de développement.

## Contexte

- Chaque vulnérabilité connue reçoit un identifiant : un CVE.
- Chaque CVE est accompagné d'une courte description et de références.
- Le NVD (National Vulnerability Database, NIST) republie ces CVE et y ajoute des données structurées : produits affectés, versions, type de faiblesse, score de sévérité, exploitation connue.
- Le NVD est la seule source de données du projet.

## Problématique

- Le NVD publie ses données sous forme brute, difficile à parcourir et à interroger directement.
- Le NVD n'analyse plus qu'une partie des CVE : une part importante reste sans données structurées.
- Il est difficile de répondre à des questions simples : combien de CVE critiques ce mois-ci? Quelle part est exploitée activement? Quelle part n'a jamais été analysée? Quel est le délai d'analyse?

## Objectif

Importer les CVE du NVD, permettre de les filtrer et de les explorer de façon interactive, et produire des statistiques fiables sur l'état actuel des données.

## Approche

- Importer les CVE du NVD et les garder à jour automatiquement.
- Conserver les données brutes du NVD à côté d'un modèle propre.
- Filtrer et rechercher les CVE (date, sévérité, produit, type de faiblesse, statut d'analyse, exploitation).
- Explorer les données de façon interactive : liste, recherche, fiche détaillée d'un CVE.
- Calculer des statistiques sur n'importe quel sous-ensemble filtré : volumes, tendances, sévérité, faiblesses, produits, délai d'analyse.
- Plus tard : proposer des suggestions générées par IA pour les CVE incomplets, avec une exactitude mesurée.
- Développement guidé par le domaine (DDD) et par les tests (TDD).

## Résultats

À venir.

## Documentation

- [Plan de développement](docs/PLAN.md) : étapes de construction du MVP
- [Glossaire](docs/GLOSSARY.md) : vocabulaire du domaine
- [Décisions d'architecture](docs/adr/) : choix de conception et leurs raisons

## Démarrer le projet

À venir.

## Utilisation de l'IA

Ce projet est développé avec l'aide d'un assistant IA. La conception, le modèle du domaine et les décisions de sécurité sont les miens; chaque contribution est révisée et couverte par des tests.

## Auteur

Alexandre Duchesne, 2026-10-04
