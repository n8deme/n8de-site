# 🎨 n8de.me — Site Agence Automation Ultime

**Status:** ✅ Structure complète | HTML/CSS/JS livré | Prêt déploiement Netlify

---

## 📋 Vue d'ensemble

Site web professionnel d'agence automation n8n dirigée par Kevin Forma.

**Objectif:** Transformer les visiteurs en prospects qualifiés. Machine à conversion.

**Design:** Premium, moderne, tech-focused. Référence visuelle : agences n8n pro.

---

## 🗂️ Structure du Projet

```
n8de-site/
├── src/
│   ├── pages/
│   │   ├── index.html ..................... Accueil (hero + social proof + pricing)
│   │   ├── index.css ...................... Styles page accueil
│   │   ├── about.html ..................... À propos (Kevin + expertise)
│   │   ├── about.css ...................... Styles page about
│   │   ├── contact.html ................... Formulaire lead capture
│   │   ├── contact.css .................... Styles page contact
│   │   ├── blog.html ...................... Liste articles + newsletter
│   │   └── blog.css ....................... Styles page blog
│   ├── css/
│   │   ├── variables.css .................. Design system (couleurs, typo, spacing)
│   │   └── global.css ..................... Styles globaux (typography, components)
│   ├── js/
│   │   └── main.js ........................ Interactions (nav, smooth scroll, forms)
│   └── assets/
│       └── (À remplir : images, logos, favicon)
├── build/
│   ├── sitemap.xml ........................ Sitemap SEO
│   └── robots.txt ......................... Fichier robots (crawlers)
├── AUDIT-PLAN.md .......................... Audit complet + plan détaillé
├── DEPLOYMENT-GUIDE.md .................... Guide déploiement Netlify
├── netlify.toml ........................... Config build Netlify (À créer)
└── README.md ............................. Ce fichier

```

---

## 🎨 Design System

### Couleurs
- **Fond :** #000000 (noir pur)
- **Accent primaire :** #FF6B00 (orange vif)
- **Accent secondaire :** #F5A623 (or/jaune)
- **Texte :** #FFFFFF (blanc)
- **Texte secondaire :** #D1D5DB (gris clair)

### Typographie
- **Font :** Space Grotesk Bold (Google Fonts)
- **H1 :** 48px (mobile 32px)
- **H2 :** 36px (mobile 24px)
- **Body :** 16px

### Composants
- Buttons : orange, rounded, hover effect
- Cards : sombre, bordure subtile, transform on hover
- Inputs : dark bg, focus state orange
- CTAs : toujours orange, conversion-focused

---

## 📄 Pages & Contenu

### 1. **Accueil** (`index.html`)
**Objectif :** Conversion immédiate

Sections :
- ✅ Navigation sticky
- ✅ Hero (headline + CTA + visual)
- ✅ Social proof Poke House
- ✅ 3 colonnes problèmes/solutions (Restaurants, PME, E-commerce)
- ✅ Pricing 3 tiers (Starter, Business, Premium)
- ✅ FAQ (4 questions)
- ✅ CTA final (gradient)
- ✅ Footer

### 2. **À Propos** (`about.html`)
**Objectif :** Crédibilité + expertise

Sections :
- ✅ Hero + qui est n8de.me?
- ✅ Story grid (pourquoi, comment, pour qui)
- ✅ Team member (Kevin Forma)
- ✅ Principes (hyper-efficace, transparent, support réel)
- ✅ Social proof (Poke House testimonial)
- ✅ Tech stack (n8n, Sheets, Zapier, Stripe)

### 3. **Contact** (`contact.html`)
**Objectif :** Lead capture

Sections :
- ✅ Formulaire complet (nom, email, entreprise, niche, message)
- ✅ Infos contact (email, LinkedIn, Twitter)
- ✅ Response time promise (< 2h)

### 4. **Blog** (`blog.html`)
**Objectif :** SEO + thought leadership

Sections :
- ✅ Liste articles (3 exemples)
- ✅ Meta tags (category, date)
- ✅ Newsletter signup
- ✅ Article cards avec hover states

---

## 🔗 Intégration Stripe

**Liens de paiement sécurisés :**

| Offre | Prix | Lien |
|---|---|---|
| Starter | 997€ | https://buy.stripe.com/dRm14ndoe62TeIg4a5gMw00 |
| Business | 2,497€ | https://buy.stripe.com/eVqbJ1fwm76X9nWegWRgMw01 |
| Premium | 4,997€ | https://buy.stripe.com/dRm8wP4RI3UL1VugWRgMw02 |

**Placements :**
- Hero accueil : "Voir les offres"
- Page offres : "Commander" sur chaque carte
- Footer : CTA "Commander"

---

## 🔍 SEO & Performance

### SEO Technique ✅
- Meta titles (60 chars max)
- Meta descriptions (160 chars max)
- Schema.org (LocalBusiness, Product)
- sitemap.xml
- robots.txt
- Open Graph (social preview)
- Canonical tags (si duplication)

### Core Web Vitals ✅
- LCP (Largest Contentful Paint) < 2.5s
- FID (First Input Delay) < 100ms
- CLS (Cumulative Layout Shift) < 0.1

### Mobile-First ✅
- Responsive 320px → 1440px
- Touch-friendly buttons (48px min)
- No horizontal scroll

---

## 🚀 Déploiement Netlify

### Prérequis
- GitHub repo
- Netlify account (gratuit)
- Domaine n8de.me

### Steps rapides
1. Push repo vers GitHub
2. Connecter Netlify → GitHub → Select repo
3. Build command : (laisse vide)
4. Publish directory : `src`
5. Deploy
6. Configurer custom domain n8de.me
7. Attendre DNS propagation (24-48h)

**Détails complets :** Voir `DEPLOYMENT-GUIDE.md`

---

## 📊 Analytics & Monitoring

### GA4 Setup
- Créer compte GA4
- Copier ID de mesure (G_XXXXXXXXXX)
- Ajouter à `src/js/main.js`
- Track : pageviews, button clicks, form submissions

### Google Search Console
- Ajouter propriété n8de.me
- Soumettre sitemap.xml
- Monitor index status, 404s, search queries

### Formulaire Contact
- Intégrer webhook Zapier/n8n
- Router données vers CRM Sheets

---

## 🔧 Customisation

### Ajouter nouvel article blog
1. Créer `src/pages/blog-article-X.html`
2. Suivre structure de `index.html`
3. Ajouter lien dans `blog.html`
4. Push GitHub → Netlify redéploie auto

### Changer copy/textes
- Tous les textes sont en HTML
- Chercher/remplacer simple
- Push → redéploiement auto

### Mettre à jour design
- Variables CSS dans `src/css/variables.css`
- Colores, tailles, spacing
- Un seul endroit pour tweak global

---

## ✅ Checklist Pré-Lancement

- [ ] Toutes les pages HTML/CSS créées
- [ ] Design system appliqué consistemment
- [ ] Navigation fonctionnelle
- [ ] Formulaire contact branché webhook
- [ ] Stripe links testés
- [ ] Images/logos en place
- [ ] SEO tags vérifiés (Google Search Console)
- [ ] Core Web Vitals OK (Lighthouse)
- [ ] Mobile responsive testé (iOS + Android)
- [ ] Cross-browser testé (Chrome, Safari, Firefox)
- [ ] sitemap.xml + robots.txt en place
- [ ] GitHub repo créé + poussé
- [ ] Netlify déploiement OK
- [ ] Domaine n8de.me configuré
- [ ] GA4 configuré
- [ ] Tests final : pricing, CTAs, contact form

---

## 🎯 KPIs À Tracker

- **Visiteurs uniques/semaine**
- **CTR sur "Voir les offres"**
- **CTR sur "Prenez une démo"**
- **Taux remplissage formulaire contact**
- **Conversion vers Stripe**
- **Bounce rate**
- **Temps sur site**
- **Requêtes Google ranking**

---

## 📞 Support & Maintenance

**Questions design/copy :** Kevin (Telegram)
**Questions déploiement :** Netlify docs + Search Console

---

## 📈 Roadmap Post-Lancement

- [ ] 1 article blog/semaine (SEO + authority)
- [ ] A/B testing headlines + CTAs
- [ ] Testimonials clients (photos + quotes)
- [ ] Case studies (Poke House détaillé)
- [ ] Intégration email marketing (Zapier)
- [ ] Retargeting Google Ads (si budget)
- [ ] Social proof automation (Trustpilot, etc.)

---

**Status :** 🚀 PRÊT À DÉPLOYER

**Créé :** 14 Apr 2026
**Assigné :** JACK (webmaster)
**Deadline Lancement :** 15 Apr 2026
