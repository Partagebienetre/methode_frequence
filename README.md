# La Méthode Fréquence — Agnès & Vous
## Lead Magnet · Déploiement GitHub Pages

---

### Structure des fichiers

```
/
├── index.html        → Page de capture email (porte d'entrée publique)
├── protocole.html    → Le protocole complet (protégé par localStorage)
└── README.md         → Ce fichier
```

---

### Déploiement sur GitHub Pages (5 minutes)

1. **Crée un dépôt GitHub** nommé par exemple `methode-frequence` (peut être public ou privé)
2. **Upload les 2 fichiers** : `index.html` et `protocole.html`
3. **Active GitHub Pages** : Settings → Pages → Source : `main` → `/root`
4. Ton URL sera : `https://[ton-pseudo].github.io/methode-frequence/`

---

### Connecter ta liste email (optionnel mais recommandé)

Dans `index.html`, trouve la ligne :
```js
const WEBHOOK_URL = "REMPLACE_PAR_TON_WEBHOOK_OU_LISTE_URL";
```

**Option A — Brevo (anciennement Sendinblue) :**
- Crée un formulaire dans Brevo → copie l'URL de l'API POST → colle-la ici

**Option B — Systeme.io :**
- Dans ton tunnel → formulaire optin → copie le lien webhook → colle-le ici

**Option C — Aucune connexion (le plus simple) :**
- Laisse le placeholder tel quel
- Les emails ne sont pas capturés côté serveur, mais la page fonctionne quand même
- L'accès localStorage est accordé après validation de l'email
- ⚠ Dans ce cas, l'email n'est pas enregistré — uniquement le passage de la porte

---

### Comment fonctionne la protection

- `index.html` : capture l'email + stocke `mf_access=true` dans localStorage + redirige vers `protocole.html`
- `protocole.html` : vérifie si `mf_access=true` dans localStorage. Si non → affiche un écran de blocage avec lien retour vers `index.html`
- ⚠ Cette protection est suffisante pour un lead magnet simple (elle bloque 99% des visiteurs non inscrits). Ce n'est pas une sécurité serveur — quelqu'un de technique pourrait contourner en modifiant localStorage. Pour une vraie sécurité, il faudrait un backend (Systeme.io, etc.)

---

### Personnalisation rapide

| Élément | Fichier | Cherche |
|---|---|---|
| Lien CTA "Prendre RDV" | protocole.html | `href="mailto:contact@agnesetvous.com"` |
| URL de redirection | index.html | `const REDIRECT_URL` |
| Webhook liste email | index.html | `const WEBHOOK_URL` |
| Texte du bouton CTA | protocole.html | `PRENDRE RENDEZ-VOUS →` |

---

### Partage du lead magnet

Une fois déployé, partage uniquement l'URL de `index.html` (la racine) :
`https://[ton-pseudo].github.io/methode-frequence/`

Ne partage jamais directement le lien `protocole.html` — cela contournerait la capture email.

---

*Agnès & Vous · contact@agnesetvous.com · agnesetvous.com*
