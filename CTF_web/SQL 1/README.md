# SQL 1

Captures d’écran du challenge **SQL Injection** (niveau 1) : énumération des colonnes, extraction d’un secret, puis transformation (décryptage/normalisation + SHA-256) pour obtenir le flag.

## Images (dans l’ordre)

1. **Énumération des colonnes** : `UNION SELECT ... FROM information_schema.columns` pour identifier les champs de la table `users`.
   ![Étape 1 — Énumération des colonnes (information_schema)](Images/image_033.png)

2. **Dump des données** : `UNION SELECT` + `CONCAT(...)` pour récupérer le contenu pertinent (dont un hash et des instructions).
   ![Étape 2 — Extraction via UNION SELECT (dump users)](Images/image_034.png)

3. **Décryptage du hash** : résolution du MD5 pour retrouver la valeur en clair (`FortyTwo`).
   ![Étape 3 — MD5 décrypté en “FortyTwo”](Images/image_035.png)

4. **Résultat final** : la valeur “FortyTwo” (mise en minuscules selon l’indication) est hashée en SHA-256 → flag affiché.
   ![Étape 4 — Flag final (SHA-256)](Images/image_002.png)
