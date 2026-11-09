# Agent instructions

## Directive transversale — livraison continue

Lire [docs/DELIVERY_POLICY.md](docs/DELIVERY_POLICY.md) : Trunk-Based Development, trunk stable, branches courtes, lots cohérents et préversions vérifiées. Les obligations de sécurité et de revue du dépôt priment.

**Fusion autonome impérative :** dès qu'une PR a sa CI, ses revues et ses protections obligatoires validées sur le HEAD exact, activer l'auto-merge GitHub ou la fusionner immédiatement. Ne pas attendre un « vert » ou un « go » de l'utilisateur. La CI absente, rouge, pending ou une revue exigée manquante restent bloquantes.

