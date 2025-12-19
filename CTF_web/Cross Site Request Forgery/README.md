# Cross Site Request Forgery (CSRF)

Captures d’écran du challenge **CSRF** : la ressource n’est accessible que si certaines conditions “navigateur” sont remplies (référent + user-agent). L’idée est de forger la requête (ex. via Burp) pour passer les contrôles.

## Images (dans l’ordre)

1. **Indice dans le code source** : commentaire indiquant que la requête doit provenir de `https://www.nsa.gov/` (contrôle du header `Referer`).
   ![Étape 1 — Indice: Referer attendu (nsa.gov)](Images/image_013.png)

2. **Deuxième indice** : commentaire suggérant un navigateur / user-agent spécifique (`ft_bornToSec`).
   ![Étape 2 — Indice: User-Agent ft_bornToSec](Images/image_014.png)

3. **Requête forgée** : dans Burp, ajout/modification des en-têtes `Referer` et `User-Agent` pour satisfaire les conditions côté serveur.
   ![Étape 3 — Requête modifiée dans Burp (Referer + UA)](Images/image_015.png)

4. **Résultat** : accès autorisé et flag affiché.
   ![Étape 4 — Flag obtenu (CSRF)](Images/image_016.png)
