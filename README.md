# Bar Cité Gondwana — Système Pro v5
## Déploiement Netlify

### 🚀 Déploiement rapide

1. **Drag & Drop** : Glissez le dossier entier sur [app.netlify.com/drop](https://app.netlify.com/drop)
2. **Ou via GitHub** :
   - Poussez ce dossier sur un repo GitHub
   - Connectez-le sur Netlify → "New site from Git"
   - Build command : *(laisser vide)*
   - Publish directory : `.`

### ⚙️ Configuration Supabase

Dans `index.html`, localisez les lignes ~237-238 et remplacez :

```js
const SUPABASE_URL = 'https://VOTRE_PROJECT_ID.supabase.co';
const SUPABASE_KEY = 'VOTRE_ANON_KEY'; // clé anon/public (longue clé JWT)
```

> ⚠️ La `SUPABASE_KEY` doit être la **clé anon publique** (un long token JWT),
> pas l'ID du projet. Trouvez-la dans : Supabase → Project Settings → API → `anon public`

Sans Supabase configuré, l'app fonctionne en **mode localStorage** (données locales au navigateur).

### 📁 Structure du projet

```
gondwana-netlify/
├── index.html       ← Application complète (SPA)
├── netlify.toml     ← Config Netlify (headers sécurité + redirects)
├── _redirects       ← Fallback SPA routing
└── README.md        ← Ce fichier
```

### 🔐 Variables d'environnement (optionnel)

Pour ne pas exposer les clés Supabase dans le code source,
vous pouvez utiliser les **Netlify Environment Variables** et injecter
les valeurs via une Netlify Function ou un build script.
