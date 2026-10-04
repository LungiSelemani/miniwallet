# MiniWallet — Glossaire et règles d'or

> Statut : brouillon v0.1 — Dernière mise à jour : 2026-10-04
>
> Convention : la documentation est en français, le code est en anglais.
> Le nom entre parenthèses est celui à utiliser dans le code.

## 1. Termes métier

### Utilisateur (`User`)
Personne physique inscrite au service, identifiée de manière unique par son
numéro de téléphone.

### Portefeuille (`Wallet`)
Compte électronique appartenant à un utilisateur, qui détient de l'argent dans
une seule devise.

### Solde (`Balance`)
Montant disponible dans un portefeuille à un instant donné. Il ne peut jamais
être négatif. En Phase 1, il est stocké directement ; à partir de la Phase 3,
il est calculé à partir des écritures du grand livre.

### Devise (`Currency`)
Monnaie dans laquelle un montant est exprimé, identifiée par son code
ISO 4217 à trois lettres (exemples : `USD`, `EUR`).

### Montant (`Money`)
Valeur monétaire composée d'une quantité ET d'une devise. Une quantité seule,
sans devise, n'est pas un montant.

### Transaction (`Transaction`)
Tout mouvement d'argent enregistré par le système : dépôt, retrait ou
transfert. Une transaction enregistrée est définitive.

### Dépôt (`Deposit`)
Transaction qui ajoute de l'argent à un portefeuille depuis l'extérieur du
système.

### Retrait (`Withdrawal`)
Transaction qui sort de l'argent d'un portefeuille vers l'extérieur du
système. Elle est refusée si le solde est insuffisant.

### Transfert (`Transfer`)
Transaction qui déplace de l'argent d'un portefeuille vers un autre
portefeuille du système. Elle réussit entièrement ou échoue entièrement.

### Frais (`Fee`)
Montant prélevé par le service sur une transaction. Les frais sont enregistrés
comme un mouvement séparé et traçable.

### Plafond (`Limit`)
Montant maximal autorisé, par transaction ou par période (jour, mois).

### Écriture comptable (`LedgerEntry`)
Ligne qui enregistre un débit ou un crédit sur un compte. En comptabilité en
partie double, chaque transaction produit au moins deux écritures, et le total
des débits est toujours égal au total des crédits.

### Grand livre (`Ledger`)
Ensemble de toutes les écritures comptables. C'est la source de vérité
financière du système.

### Clé d'idempotence (`IdempotencyKey`)
Identifiant unique envoyé par le client avec une requête. Si la même clé est
reçue deux fois, le système renvoie le résultat de la première requête sans
l'exécuter une seconde fois.

### Réconciliation (`Reconciliation`)
Vérification que deux sources d'information concordent : par exemple, que la
somme des écritures du grand livre correspond aux soldes des portefeuilles.

## 2. Règles d'or (non négociables)

### Règle 1 — Jamais de `double` ni de `float` pour l'argent
- Utiliser `BigDecimal` en Java et `NUMERIC` en PostgreSQL.
- Créer un `BigDecimal` à partir d'un texte : `new BigDecimal("10.50")`,
  jamais `new BigDecimal(10.50)`.
- Comparer avec `compareTo()`, jamais avec `equals()`.
- Arrondir toujours explicitement, avec un mode d'arrondi documenté.

### Règle 2 — Un montant voyage toujours avec sa devise
- Ne jamais stocker ni transmettre une quantité sans sa devise.
- Ne jamais additionner ou comparer deux montants de devises différentes.

### Règle 3 — Une transaction n'est jamais modifiée ni supprimée
- Une erreur se corrige par une nouvelle transaction inverse
  (contre-passation), qui fait référence à la transaction d'origine.

### Règle 4 — Toutes les dates sont en UTC
- Utiliser `Instant` en Java et `TIMESTAMPTZ` en PostgreSQL.
- La conversion vers le fuseau horaire de l'utilisateur se fait uniquement
  à l'affichage.

### Règle 5 — Aucune donnée sensible dans les journaux (logs)
- Interdit : mots de passe, jetons d'accès, codes PIN, numéros de carte.
- Les numéros de téléphone sont masqués : `******1234`.