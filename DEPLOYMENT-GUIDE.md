# 🚀 GUIDE DÉPLOIEMENT — n8de.me sur Netlify

## Prérequis
- Compte GitHub (ou GitLab)
- Compte Netlify (gratuit)
- Domaine n8de.me (ou DNS configuré)

---

## ÉTAPE 1 : Préparer le Repo GitHub

### 1.1 Initialiser le repo
```bash
cd /data/.openclaw/workspace/projects/n8de-site
git init
git add .
git commit -m "init: n8de.me site structure"
```

### 1.2 Pousser vers GitHub
```bash
git remote add origin https://github.com/YOUR_USERNAME/n8de-site.git
git branch -M main
git push -u origin main
```

### 1.3 Structure du repo à vérifier
```
n8de-site/
├── src/
│   ├── pages/
│   │   ├── index.html
│   │   ├── about.html
│   │   ├── contact.html
│   │   ├── blog.html
│   │   └── *.css (stylesheets)
│   ├── css/
│   │   ├── variables.css
│   │   └── global.css
│   ├── js/
│   │   └── main.js
│   └── assets/
│       └── (images, logos, etc.)
├── build/
│   ├── sitemap.xml
│   └── robots.txt
├── README.md
└── netlify.toml (à créer)
```

---

## ÉTAPE 2 : Créer netlify.toml

```toml
[build]
  publish = "src"
  command = ""

[build.environment]
  NODE_VERSION = "18"

[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200

[[headers]]
  for = "/*"
  [headers.values]
    X-Content-Type-Options = "nosniff"
    X-Frame-Options = "DENY"
    X-XSS-Protection = "1; mode=block"
    Referrer-Policy = "strict-origin-when-cross-origin"
    Strict-Transport-Security = "max-age=31536000; includeSubDomains"

[[headers]]
  for = "/css/*"
  [headers.values]
    Cache-Control = "public, max-age=31536000"

[[headers]]
  for = "/js/*"
  [headers.values]
    Cache-Control = "public, max-age=31536000"

[[headers]]
  for = "/*.html"
  [headers.values]
    Cache-Control = "public, max-age=3600"
```

---

## ÉTAPE 3 : Déployer sur Netlify

### 3.1 Via Interface Netlify
1. Aller à **netlify.com**
2. **Sign Up** (si nécessaire)
3. **New site from Git**
4. Sélectionner **GitHub**
5. Authoriser Netlify à accéder tes repos
6. Choisir **n8de-site**
7. Build settings :
   - Build command : (laisser vide)
   - Publish directory : `src`
8. **Deploy site**

### 3.2 Vérifier le déploiement
- Netlify génère une URL temporaire : `https://xxxxxxxx.netlify.app`
- Vérifier que les pages chargent

---

## ÉTAPE 4 : Configurer le Domaine

### 4.1 Pointer n8de.me vers Netlify
1. Dans Netlify, aller à **Site settings → Domain management**
2. Ajouter un custom domain : `n8de.me`
3. Netlify affiche des **nameservers** à configurer
4. Aller à registrar DNS (GoDaddy, Namecheap, etc.)
5. Remplacer les nameservers par ceux de Netlify
6. Attendre 24-48h pour propagation DNS

### 4.2 SSL/HTTPS (Auto via Netlify)
- Netlify configure automatiquement SSL Let's Encrypt
- Certifikat renouvelé auto tous les 90 jours

---

## ÉTAPE 5 : Configuration Post-Déploiement

### 5.1 Google Analytics (GA4)
1. Créer un compte GA4 : **analytics.google.com**
2. Copier l'ID de mesure (format : G_XXXXXXXXXX)
3. Dans `src/js/main.js`, remplacer :
   ```javascript
   gtag('config', 'G_YOUR_GA4_ID'); // → G_123456789
   ```
4. Redéployer

### 5.2 Webhook Formulaire Contact
1. Créer un compte Zapier ou n8n
2. Générer un webhook public
3. Remplacer dans `src/js/main.js` :
   ```javascript
   const webhookUrl = 'https://hooks.zapier.com/hooks/catch/YOUR_KEY';
   ```
4. Redéployer

### 5.3 Open Graph Image (Social Preview)
1. Créer une image 1200x630px (logo + headline)
2. Upload à `src/assets/og-image.png`
3. Vérifier que la meta tag pointe correctly

---

## ÉTAPE 6 : Tests Pré-Lancement

### 6.1 Performance (Core Web Vitals)
```bash
# Utiliser Lighthouse (intégré dans Chrome DevTools)
1. Ouvrir https://n8de.me
2. Ctrl+Shift+I → Lighthouse
3. Vérifier scores :
   - LCP < 2.5s ✓
   - FID < 100ms ✓
   - CLS < 0.1 ✓
```

### 6.2 Mobile Responsiveness
```bash
1. Ouvrir https://n8de.me
2. Toggle device toolbar (Ctrl+Shift+M)
3. Tester sur iPhone 12, iPad, Galaxy S10
4. Vérifier :
   - Pas de horizontal scroll
   - Buttons touchables (48px min)
   - Texte lisible
```

### 6.3 SEO Basique
```bash
1. Google Search Console
   - Ajouter propriété https://n8de.me
   - Soumettre sitemap.xml
   - Vérifier index status
2. Meta tags
   - Vérifier title (60 chars)
   - Vérifier description (160 chars)
3. Schema.org
   - Tester : schema.org/validator
   - Coller HTML de la page
   - Vérifier LocalBusiness structuré
```

### 6.4 Links Stripe
```bash
Tester les 3 liens de paiement :
- https://buy.stripe.com/dRm14ndoe62TeIg4a5gMw00 (Starter)
- https://buy.stripe.com/eVqbJ1fwm76X9nWegWRgMw01 (Business)
- https://buy.stripe.com/dRm8wP4RI3UL1VugWRgMw02 (Premium)

Vérifier que chaque lien :
✓ Ouvre un page checkout Stripe
✓ Montre le bon prix
✓ Redirige vers le bon ordre
```

---

## ÉTAPE 7 : Maintenance Quotidienne

### 7.1 Updater le contenu
1. Ajouter nouvel article blog :
   - Créer `src/pages/blog-article-X.html`
   - Ajouter à `blog.html` (liste articles)
   - Push vers GitHub
2. Netlify redéploie auto

### 7.2 Monitoring
- Vérifier GA4 régulièrement
- Google Search Console : check index + erreurs
- Netlify logs : check 404, 500

### 7.3 Optimisations continues
- A/B testing des CTAs (headline, color, text)
- Monitor conversion rate
- Update copy basé sur feedback clients

---

## 🎯 CHECKLIST FINAL

- [ ] Repo GitHub créé et poussé
- [ ] `netlify.toml` configuré
- [ ] Site déployé sur Netlify
- [ ] Domaine n8de.me pointé vers Netlify
- [ ] SSL/HTTPS en place
- [ ] GA4 configuré
- [ ] Webhook formulaire en place
- [ ] Tests Lighthouse OK (Core Web Vitals)
- [ ] Responsive mobile OK
- [ ] SEO tags vérifié
- [ ] Stripe links testés
- [ ] sitemap.xml + robots.txt en place
- [ ] Google Search Console configuré
- [ ] Lancement annoncé 🚀

---

## Support

- **Netlify Docs :** https://docs.netlify.com/
- **Google Analytics :** https://support.google.com/analytics
- **Stripe :** https://stripe.com/docs

**Status :** ✅ PRÊT À DÉPLOYER
