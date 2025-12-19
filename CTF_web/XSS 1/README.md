# XSS 1

Captures d’écran du challenge **XSS** (niveau 1) : injection d’un script dans un champ de formulaire non filtré.

## Images (dans l’ordre)

1. **Injection XSS dans le formulaire “Feedback”** (payload `<script>alert('XSS')</script>` via un champ HTML) → la page affiche ensuite le flag.
   ![Étape 1 — Injection XSS sur le formulaire Feedback](Images/image_001.png)


## Remédiation

- **Échapper/encoder en sortie** (HTML, attributs, URL, JS) plutôt que “filtrer” en entrée.
- **Éviter les sinks dangereux** (`innerHTML`, `document.write`, `eval`, templates non échappés) et préférer `textContent` / APIs DOM sûres.
- Mettre une **Content Security Policy (CSP)** restrictive (au minimum bloquer l’inline/script non approuvé).
- Cookies de session en **HttpOnly + Secure + SameSite**, et limiter l’exposition de données sensibles côté client.
- Ajouter des contrôles côté serveur : **validation/allowlist**, logs, et tests (OWASP XSS / linters SAST/DAST).
