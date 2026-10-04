# MiniWallet — Vision du produit

> Statut : brouillon v0.1 — Dernière mise à jour : 2026-10-04

## 1. Le problème

Beaucoup de personnes ont besoin d'envoyer, recevoir et conserver de l'argent
de manière simple, depuis un téléphone, sans compte bancaire classique.
Pour qu'elles fassent confiance à un tel service, il doit être exact au centime
près, disponible et traçable.

## 2. La solution

MiniWallet est un portefeuille électronique de type mobile money. Chaque
utilisateur possède un portefeuille dans lequel il peut déposer, retirer et,
plus tard, transférer de l'argent vers d'autres utilisateurs.

## 3. Les utilisateurs cibles

- **Utilisateur final** : particulier qui gère son argent depuis son téléphone.
- **Agent de support** (phases ultérieures) : consulte l'historique d'un client
  pour répondre à une réclamation.

## 4. Périmètre de la Phase 1 (ce que nous faisons)

- Créer un utilisateur (nom complet, numéro de téléphone unique).
- Créer un portefeuille pour un utilisateur, dans une devise donnée.
- Déposer de l'argent sur un portefeuille.
- Retirer de l'argent d'un portefeuille, si le solde est suffisant.
- Consulter le solde d'un portefeuille.

## 5. Hors périmètre de la Phase 1 (ce que nous ne faisons pas encore)

- Transferts entre utilisateurs (Phase 2).
- Authentification et sécurité des accès (Phase 2).
- Frais, plafonds et niveaux de vérification d'identité (Phase 3).
- Conversion entre devises.
- Intégration avec de vrais opérateurs ou banques.
- Notifications (SMS, e-mail).
- Interface graphique : seule l'API REST est livrée.

## 6. Principes directeurs (non négociables)

1. **Exactitude** : aucun argent n'est jamais créé ni perdu par erreur.
2. **Traçabilité** : chaque mouvement d'argent laisse une trace permanente.
3. **Sécurité** : aucune donnée sensible n'est exposée ni journalisée.
4. **Simplicité** : la solution la plus simple qui respecte les trois
   principes précédents est la bonne.

Les règles techniques qui découlent de ces principes sont détaillées dans
[le glossaire](glossaire.md).

## 7. Critères de réussite de la Phase 1

- Toutes les fonctionnalités du périmètre sont disponibles via l'API REST.
- Un retrait supérieur au solde est toujours refusé, sans modifier le solde.
- Chaque fonctionnalité est couverte par des tests automatisés.
- Un nouveau développeur peut lancer le projet en suivant uniquement le README.