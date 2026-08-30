# Connexion PRONOTE

## Important
Student Toolbox ne doit jamais demander ni stocker ton mot de passe PRONOTE dans le navigateur.

Une intégration automatique dépend de ce que le CIMF autorise et expose. Index Éducation documente des services Web/API pour certaines configurations PRONOTE, mais l'accès et les données disponibles dépendent de l'établissement et de son administration.

## Architecture prévue

`PRONOTE / service autorisé → backend sécurisé → Student Toolbox`

Le backend récupère uniquement les données nécessaires :
- devoirs / échéances ;
- emploi du temps ;
- matières ;
- éventuellement notes, uniquement si tu décides de les afficher.

Le navigateur ne reçoit qu'un jeton de session ou des données filtrées. Aucun secret PRONOTE ne doit être commité dans GitHub.

## Pour activer la connexion réelle

Demander à l'administrateur PRONOTE du CIMF :

1. si l'établissement dispose d'un service Web/API PRONOTE accessible aux étudiants ;
2. si un connecteur tiers peut être autorisé ;
3. quelle méthode d'authentification est prévue ;
4. quelles données peuvent être exportées ;
5. l'URL/API et la documentation correspondant à l'instance du CIMF.

Le service officiel PRONOTE peut utiliser des services Web décrits par WSDL et communiquer en SOAP/REST. Les services et droits dépendent de la configuration de l'établissement.

## Alternative si l'API n'est pas disponible

Prévoir un import manuel contrôlé : CSV/ICS ou copier-coller des échéances. L'application conserve alors une distinction claire entre :
- `source = PRONOTE` ;
- `source = personnel` ;
- `source = import`.

## Sécurité

Ne jamais mettre dans le dépôt :
- mot de passe PRONOTE ;
- cookie de session ;
- QR code personnel ;
- token API ;
- URL privée contenant un secret.

Pour une vraie IA générative, la même règle s'applique : la clé du fournisseur doit rester côté serveur, jamais dans `app.js` ou dans le frontend GitHub Pages.
