## Quoi

<!-- Décrire le changement en une ou deux phrases. -->

## Pourquoi

<!-- Le besoin ou la user story concernée. -->

## Comment tester

<!-- Les étapes pour vérifier le changement, avec les commandes ou requêtes. -->

## Type de changement

- [ ] Nouvelle fonctionnalité (`feat`)
- [ ] Correction de bug (`fix`)
- [ ] Documentation (`docs`)
- [ ] Refactorisation (`refactor`)
- [ ] Maintenance ou CI (`chore`, `ci`)

## Checklist

- [ ] `./mvnw verify` passe en local
- [ ] Des tests couvrent le changement, y compris les cas d'erreur
- [ ] La documentation est à jour (README, docs, OpenAPI)
- [ ] Une migration Flyway est incluse si le schéma de base change
- [ ] Aucun secret ni donnée sensible dans le code ou les logs
- [ ] Les règles d'or sont respectées (pas de `double` pour l'argent,
      devise avec chaque montant, dates en UTC, aucune transaction
      modifiée ou supprimée)