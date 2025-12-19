# Path Traversal

Captures d’écran du challenge **Path Traversal** : exploration d’un répertoire caché et lecture de fichiers système via des séquences `../`.

## Images (dans l’ordre)

1. **Exploration d’un dossier caché** : listing web d’un chemin “.hidden/…”, montrant de nombreux sous-dossiers et un `README`.
   ![Étape 1 — Listing d’un répertoire caché (.hidden/...)](Images/image_010.png)

2. **Exploitation du Path Traversal** : injection de `../../../../` pour tenter de lire `/etc/passwd` → le challenge retourne le flag (popup).
   ![Étape 2 — Path traversal vers /etc/passwd + flag](Images/image_011.png)


## Remédiation

- Ne jamais accéder à un fichier via un chemin fourni tel quel par l’utilisateur.
- Construire les chemins côté serveur avec une **allowlist** (IDs → chemins) et refuser tout ce qui sort du répertoire attendu.
- Utiliser **normalisation + `realpath`** puis vérifier que le chemin final commence bien par le répertoire autorisé.
- Stocker les fichiers **hors du webroot**, et appliquer des permissions minimales (compte applicatif dédié).
- Journaliser/alerter sur tentatives (`../`, encodages, `%2e%2e%2f`, etc.) + rate limiting.
