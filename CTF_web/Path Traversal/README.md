# Path Traversal

Captures d’écran du challenge **Path Traversal** : exploration d’un répertoire caché et lecture de fichiers système via des séquences `../`.

## Images (dans l’ordre)

1. **Exploration d’un dossier caché** : listing web d’un chemin “.hidden/…”, montrant de nombreux sous-dossiers et un `README`.
   ![Étape 1 — Listing d’un répertoire caché (.hidden/...)](image_010.png)

2. **Exploitation du Path Traversal** : injection de `../../../../` pour tenter de lire `/etc/passwd` → le challenge retourne le flag (popup).
   ![Étape 2 — Path traversal vers /etc/passwd + flag](image_011.png)
