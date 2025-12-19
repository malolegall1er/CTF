# Brute Force de répertoire

Captures d’écran du challenge **bruteforce / discovery de répertoires** : découverte d’un dossier caché, récupération d’un fichier `.htpasswd`, crack du hash, puis obtention du flag.

## Images (dans l’ordre)

1. **Énumération de contenu web** : scan avec `gobuster dir` pour lister les répertoires accessibles (dont un dossier “whatever”).
   ![Étape 1 — Gobuster (directory enumeration)](Images/image_012.png)

2. **Accès au dossier découvert** : listing HTTP du répertoire `/whatever/` avec un fichier intéressant (`htpasswd`).
   ![Étape 2 — Index of /whatever/ + htpasswd](Images/image_031.png)

3. **Récupération du hash** : contenu du fichier `htpasswd` (login + hash).
   ![Étape 3 — Contenu du fichier htpasswd (hash)](Images/image_023.png)

4. **Crack du hash** : `john` retrouve le mot de passe en clair pour l’utilisateur `root`.
   ![Étape 4 — Hash cracké avec John (root:qwerty123@)](Images/image_030.png)

5. **Résultat** : page “Congratulations” affichant le flag.
   ![Étape 5 — Flag obtenu](Images/image_032.png)
