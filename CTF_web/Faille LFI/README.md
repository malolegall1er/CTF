# Faille LFI

Captures d’écran autour d’un challenge “LFI / upload” : tentative d’upload d’un fichier PHP, contournement des filtres (type MIME / extension), puis validation avec obtention du flag.

## Images (dans l’ordre)

1. **Tentative initiale** : upload direct d’un `shell.php` (interception Burp).
   ![Étape 1 — Upload de shell.php (intercept Burp)](Images/image_017.png)

2. **Blocage** : le site refuse l’upload (message “Your image was not uploaded”).
   ![Étape 2 — Upload refusé](Images/image_018.png)

3. **Contournement (double extension)** : envoi d’un fichier ressemblant à une image mais nommé avec une extension double (ex. `bash.php.jpg`), en observant la requête dans Burp.
   ![Étape 3 — Bypass via double extension (.php.jpg)](Images/image_019.png)

4. **Upload accepté** : confirmation que `/tmp/bash.php.jpg` est bien envoyé.
   ![Étape 4 — Confirmation: /tmp/bash.php.jpg uploadé](Images/image_020.png)

5. **Contournement (type MIME / contenu)** : modification de la requête pour faire accepter un fichier `.php` en le présentant comme une image (`Content-Type: image/jpeg`) tout en gardant du code PHP dans le corps.
   ![Étape 5 — Bypass via Content-Type image/jpeg + contenu PHP](Images/image_021.png)

6. **Résultat** : upload de `/tmp/shell.php` validé, et flag affiché par le challenge.
   ![Étape 6 — Flag obtenu + /tmp/shell.php uploadé](Images/image_022.png)
