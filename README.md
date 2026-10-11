# cve-lens

Explorer, filtrer et analyser les vulnérabilités connues (CVE) à partir de plusieurs bases de données publiques.

**Statut :** MVP en cours de développement.

## Contexte

- Chaque vulnérabilité connue reçoit un identifiant : un CVE.
- Chaque CVE est accompagné d'une courte description et de références.
- Plusieurs bases publiques publient et complètent ces données : le programme CVE, le NVD (NIST), la liste KEV de la CISA, OSV, les avis de sécurité GitHub, etc.
- Chaque source ajoute ses propres informations : produits affectés, versions, type de faiblesse, score de sévérité, exploitation active.

## Problématique

- Les données sur un même CVE sont dispersées entre plusieurs sources, dans des formats différents.
- Les sources ne sont pas toujours d'accord, et certaines sont incomplètes : par exemple, le NVD n'analyse plus qu'une partie des CVE.
- Il est difficile de répondre à des questions simples : combien de CVE critiques ce mois-ci? Quelle part est exploitée activement? Quelle part n'a jamais été analysée?

## Objectif

Rassembler les CVE de plusieurs sources publiques dans un modèle unique, permettre de les filtrer et de les explorer, et produire des statistiques fiables sur l'état actuel des données.

## Approche

- Importer les CVE de plusieurs sources publiques et les garder à jour automatiquement.
- Conserver les données brutes de chaque source à côté d'un modèle consolidé.
- Rendre visible la provenance de chaque donnée et les désaccords entre sources.
- Filtrer et rechercher les CVE (date, sévérité, produit, type de faiblesse, source, exploitation).
- Calculer des statistiques : volumes, tendances, couverture et délai d'analyse par source.
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
