# Guide de contribution

Ce document décrit le processus à suivre pour toute modification du projet.

## 1. Règle principale

La branche `main` contient toujours du code fonctionnel. On n'y fait **jamais**
de commit directement : toute modification passe par une branche et une
pull request.

## 2. Les branches

Créer une branche à partir de `main` à jour, avec un préfixe qui indique
le type de travail :

| Préfixe     | Usage                                   | Exemple                       |
|-------------|-----------------------------------------|-------------------------------|
| `feature/`  | Nouvelle fonctionnalité                 | `feature/depot-portefeuille`  |
| `fix/`      | Correction d'un bug                     | `fix/solde-negatif-retrait`   |
| `docs/`     | Documentation uniquement                | `docs/mise-a-jour-glossaire`  |
| `chore/`    | Maintenance, configuration, outillage   | `chore/mise-a-jour-spring`    |

Règles :
- noms en minuscules, mots séparés par des tirets, sans accents ;
- une branche = une seule tâche ou user story ;
- une branche vit peu de temps : quelques jours au maximum.

## 3. Les messages de commit

Format [Conventional Commits](https://www.conventionalcommits.org/fr/) :

```
<type>(<portée optionnelle>): <description>
```

| Type       | Usage                                                    |
|------------|----------------------------------------------------------|
| `feat`     | Nouvelle fonctionnalité                                  |
| `fix`      | Correction d'un bug                                      |
| `docs`     | Documentation uniquement                                 |
| `test`     | Ajout ou modification de tests uniquement                |
| `refactor` | Restructuration du code sans changement de comportement  |
| `chore`    | Maintenance et configuration                             |
| `ci`       | Intégration continue                                     |

Règles :
- description au présent, en minuscules, sans point final ;
- 72 caractères maximum sur la première ligne ;
- un commit = un seul changement logique.

Exemples :
```
feat(wallet): ajoute le dépôt sur un portefeuille
fix(wallet): refuse un retrait supérieur au solde
test(wallet): couvre le cas d'un montant négatif
```

## 4. Le processus de pull request

1. Mettre à jour `main` et créer sa branche :
```bash
   git switch main
   git pull
   git switch -c feature/ma-fonctionnalite
```
2. Développer en faisant des commits réguliers.
3. Vérifier en local que tout passe : `./mvnw verify`.
4. Publier la branche : `git push -u origin feature/ma-fonctionnalite`.
5. Ouvrir une pull request sur GitHub et remplir le modèle.
6. Attendre que l'intégration continue soit verte.
7. Relire soi-même le diff complet, puis faire relire.
8. Fusionner avec **« Squash and merge »**, puis supprimer la branche.

Le titre de la pull request doit respecter le format Conventional Commits :
il devient le message du commit unique ajouté à `main`.

## 5. Définition de « terminé »

Une modification est terminée seulement si elle respecte la
[Definition of Done](docs/definition-of-done.md) (à venir).