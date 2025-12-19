# XSS 1

Captures d’écran du challenge **XSS** (niveau 1) : injection d’un script dans un champ de formulaire non filtré.

## Images (dans l’ordre)

1. **Injection XSS dans le formulaire “Feedback”** (payload `<script>alert('XSS')</script>` via un champ HTML) → la page affiche ensuite le flag.
   ![Étape 1 — Injection XSS sur le formulaire Feedback](Images/image_001.png)
