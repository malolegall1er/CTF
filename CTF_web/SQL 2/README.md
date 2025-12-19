# SQL 2

Captures d’écran du challenge **SQL Injection** (niveau 2) : découverte de table/colonnes, extraction d’un hash MD5, puis conversion en SHA-256 pour obtenir le flag.

## Images (dans l’ordre)

1. **Énumération des colonnes** : `UNION SELECT ... FROM information_schema.columns` révèle la table `list_images` et ses champs.
   ![Étape 1 — Colonnes trouvées pour list_images](Images/image_003.png)

2. **Extraction du hash** : `UNION SELECT` + `CONCAT(...)` récupère un MD5 et une consigne (“md5 decode → lowercase → sha256”).
   ![Étape 2 — Dump + récupération du MD5 et des instructions](Images/image_004.png)

3. **Décryptage du MD5** : récupération du texte en clair (`albatroz`).
   ![Étape 3 — MD5 décrypté en “albatroz”](Images/image_005.png)

4. **Calcul du SHA-256** : hash SHA-256 du mot en clair (après mise en minuscules) → résultat utilisé comme flag.
   ![Étape 4 — SHA-256(albatroz)](Images/image_006.png)
