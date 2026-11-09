# Politique de livraison — Trunk-Based Development et préversions successives

> Directive transversale validée par le propriétaire le 9 novembre 2026. Applicable à ce projet et à tous les agents, sous réserve des protections et procédures de sécurité plus strictes du dépôt.

## Objectif

**Livrer régulièrement des versions réellement utilisables, plutôt que prolonger indéfiniment des branches et attendre une V1 parfaite.** Préserver la stabilité de la branche de référence.

## Règles de travail

1. La branche de référence (`main`) est le **trunk** : elle doit rester vérifiable, intégrable et publiable pour le périmètre activé. Ne pas renommer une branche existante pour appliquer la méthode.
2. Ne pas développer durablement directement sur le trunk : utiliser des **branches courtes**, avec une PR par **lot fonctionnel cohérent** et non une multitude de micro-PR. Éviter les branches d'intégration qui vivent plusieurs semaines.
3. Avant chaque PR : regarder les PR déjà ouvertes, leurs modifications et les dépendances ; réutiliser/réconcilier les travaux existants, éviter les doublons et les conflits de propriété de fichiers. Ne pas écraser le travail d'un autre agent.
4. Fusionner **rapidement une fois le HEAD exact validé** par les contrôles requis : tests pertinents, typecheck/build, sécurité, migrations et revue selon les règles du dépôt. Un statut pending, absent, skipped ou un job différent n'est **pas** vert. Ne jamais contourner les protections, approbations ou permissions.
5. Une fonctionnalité incomplète peut rejoindre le trunk **uniquement si elle reste désactivée ou inaccessible**, avec des frontières et tests empêchant les effets de bord. Les flags désactivés par défaut ne remplacent pas une vraie validation. Pas de migrations non réversibles, fuite de secrets, mutation de données/budgets, ou baisse de sécurité dissimulée par flag.
6. Après chaque fusion : vérifier la CI du **nouveau trunk**, identifier le premier échec réel, corriger à la racine, puis reprendre le prochain lot. Ne pas ignorer un `main` rouge.
7. Produire des **préversions successives** (`v0.1`, `v0.2`, `v0.3`, etc. si le dépôt livre une application), chacune avec un **parcours vertical testable**, des critères d'acceptation, un changelog, une preuve de validation et une procédure de retour arrière. Ne pas déclarer « livré » si aucun artefact/staging/test utilisateur n'est prouvé.
8. Une préversion privée/interne n'est pas une bêta publique. Avant accès utilisateurs : confirmer tests bout en bout, isolation des comptes, observabilité, sauvegarde/rollback et barrières de sécurité adaptées au projet.
9. Priorité à la **stabilité, à la complétude du parcours et aux bibliothèques maintenues/officielles** lorsqu'elles remplacent proprement du code maison. Pas de refactorings purement cosmétiques qui retardent une préversion. Le formatage n'est pas un substitut aux tests techniques.
10. Pour les dépôts de bibliothèque, infrastructure ou documentation : appliquer le même **trunk stable et petites intégrations**, mais choisir des versions/tags et des critères compatibles avec leur nature, sans inventer de V0 applicative.

## Application à ce dépôt

Writer Sandbox : chaque changement est testé dans un environnement isolé à droits minimaux. Ce dépôt sert de bac à sable, pas de voie de déploiement automatique ; ne pas exposer secrets ou ressources de production.

## À fournir avec chaque lot

- Fonction ou parcours désormais utilisable ; éléments explicitement hors périmètre et flags désactivés.
- SHA exact, liens des vérifications, tests effectués, limites de preuve et risques résiduels.
- Étape de livraison suivante (préversion/tag, déploiement ou test) et retour arrière possible.

**Arbitrage :** la cadence de livraison ne justifie jamais une fusion rouge, un déploiement non sûr ni le contournement des règles locales de ce dépôt.
