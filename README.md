# TABLEAU DE SYNTHÈSE E5 - BTS SIO SLAM
**Session 2026 | Réalisation professionnelle**

---

## 📌 IDENTIFICATION DU PROJET

| Élément | Valeur |
|---------|--------|
| **Nom du projet** | Métiers du Numérique - Plateforme d'Orientation BTS |
| **Période** | Hackathon janvier 2026 (5-8 janvier, 15h effectives) |
| **Type** | Réalisation en cours de formation (TP Laravel, 2ème année) |
| **Format** | Projet solo |
| **Contexte pédagogique** | Hackathon thématique sur les APIs publiques (Open-Data) |

---

## 🎯 DESCRIPTION DE LA RÉALISATION

### Objectif
Créer une **plateforme web d'orientation** permettant aux élèves de terminale et étudiants de découvrir les formations BTS du numérique en France, en exploitant les données publiques (data.gouv.fr) et en leur proposant une vision des carrières et rémunérations associées.

### Problématique résolue
- **Besoin identifié**: Les orientations scolaires manquent souvent de données actualisées sur l'offre BTS
- **Solution apportée**: Centraliser les données publiques BTS + salaires + localisation dans une interface ergonomique et interactive
- **Utilisateurs cibles**: Élèves, parents, conseillères d'orientation

---

## 🏗️ ARCHITECTURE TECHNIQUE

### Stack Technologique
- **Backend**: Laravel 12 (PHP 8.2+)
- **Frontend**: Blade + Tailwind CSS + Alpine.js
- **Build**: Vite.js
- **Cartographie**: Leaflet.js
- **BDD**: MySQL (migrations Laravel)
- **Cache**: Redis (Laravel Cache)

### Métriques du projet
```
📊 Code généré:
  - Services: 688 lignes (DataGouvService, RemunerationService)
  - Controllers: 397 lignes (5 contrôleurs)
  - Models: 129 lignes (SearchStat, User)
  - Vues Blade: 40+ fichiers
  ─────────────────────────
  TOTAL: ~1200+ lignes de code significatif
```

---

## 💾 FONCTIONNALITÉS DÉVELOPPÉES

### 1️⃣ Consommation d'APIs publiques
**Fichier**: `app/Services/DataGouvService.php` (428 lignes)

**Implémentation**:
- ✅ Connexion API data.gouv.fr pour les effectifs BTS
- ✅ Récupération paginée (100 enregistrements/requête)
- ✅ Système de cache 24h pour optimisation
- ✅ Filtrage côté serveur/client pour BTS du numérique
- ✅ Gestion des erreurs avec logs détaillés
- ✅ Fallback en cas d'indisponibilité API

**Points techniques**:
```php
// Pagination intelligente
while ($hasMore) {
    $response = Http::timeout(60)->retry(3, 100)->get(API_URL, [...])
}

// Cache & mémorisation
Cache::remember("bts_numerique_{$annee}", 86400, function() {...})

// Filtrage avancé
- Années scolaires (2024, 2023...)
- Académies (France métropolitaine + DOM-TOM)
- Villes d'implantation
- Établissements publics/privés
```

---

### 2️⃣ Recherche avancée avec filtres multiples
**Fichier**: `app/Http/Controllers/FormationSearchController.php` (134 lignes)

**Fonctionnalités**:
- ✅ Recherche par nom de formation
- ✅ Filtrage par académie (liste exhaustive)
- ✅ Filtrage par ville
- ✅ Filtrage par statut (public/privé)
- ✅ Sélection par année scolaire
- ✅ Recherche par plage salariale (métiers)
- ✅ Validation des données en entrée
- ✅ Enregistrement automatique des statistiques

**Validation mise en place**:
```php
$validated = $request->validate([
    'formation' => 'nullable|string|max:255',
    'academie' => 'nullable|string|max:100',
    'ville' => 'nullable|string|max:100',
    'statut' => 'nullable|in:public,privé,prive',
    'year' => 'nullable|string|in:2024,2023,2022,2021,2020,2019',
    'salaire_min' => 'nullable|integer|min:0',
    'salaire_max' => 'nullable|integer|min:0',
]);
```

---

### 3️⃣ Authentification et gestion utilisateurs
**Fichiers**: 
- `app/Http/Middleware/Authenticate.php`
- `routes/auth.php`
- `resources/views/auth/` (6 vues)

**Implémentation**:
- ✅ Inscription avec validation email
- ✅ Connexion sécurisée (hash password)
- ✅ Récupération mot de passe
- ✅ Profil utilisateur modifiable
- ✅ Accès réservé aux recherches avancées
- ✅ Sessions gérées automatiquement

**Sécurité appliquée**:
- CSRF protection (Laravel middleware)
- Password hashing (bcrypt)
- Email verification
- Session timeout

---

### 4️⃣ Dashboard avec statistiques et analytics
**Fichier**: `app/Http/Controllers/DashboardController.php` (59 lignes)

**Données affichées**:
- ✅ Statistiques globales des formations (nombre total, répartition)
- ✅ Mes recherches récentes (historique utilisateur)
- ✅ Formations les plus recherchées (TOP 5)
- ✅ Académies les plus recherchées (TOP 5)
- ✅ Métiers avec meilleurs salaires (TOP 5)
- ✅ Graphiques et cartes de synthèse

**Modèle de données**:
```php
SearchStat::topFormations(10)        // Groupement & count
SearchStat::topAcademies(10)         // Statistiques
$remunerationService->getRemunerations() // Données salaires
```

---

### 5️⃣ Cartographie interactive
**Fichier**: `resources/views/home.blade.php`

**Technologie**: Leaflet.js + OpenStreetMap

**Fonctionnalités**:
- ✅ Carte de France interactive
- ✅ Marqueurs pour chaque formation
- ✅ Clustering par ville (pour lisibilité)
- ✅ Popup avec infos établissement
- ✅ Responsive design (mobile/desktop)
- ✅ Zoom & navigation intuitifs

**Données affichées par marqueur**:
- Nom de la formation
- Établissement
- Ville & académie
- Nombre d'élèves
- Statut (public/privé)

---

### 6️⃣ Gestion des données avec modèles et migrations
**Fichiers**: 
- `database/migrations/2026_01_08_205440_create_search_stats_table.php`
- `app/Models/SearchStat.php`

**Tables créées**:

**`search_stats`**: Enregistre chaque recherche effectuée
```sql
- id, user_id (FK), formation, academie, ville, statut, year
- sexe_rechercheur (démographie)
- nombre_resultats, ip_address, user_agent
- timestamps (created_at, updated_at)
- Index sur formation, academie, created_at
```

**`remunerations`**: Référentiel des salaires métiers
```sql
- metier, niveau, salaire_min, salaire_max, salaire_median
- Données par défaut en fallback
```

**Requêtes optimisées**:
```php
// Scopes réutilisables
SearchStat::recent()        // 7 derniers jours
SearchStat::forYear(2024)   // Année spécifique
SearchStat::topFormations() // Agrégation + tri
```

---

### 7️⃣ Page d'accueil publique
**Fichier**: `app/Http/Controllers/HomeController.php` (77 lignes)

**Contenu**:
- ✅ Vue globale sans authentification
- ✅ Statistiques générales des BTS
- ✅ Carte interactive des formations
- ✅ Appels à action (inscription, recherche)
- ✅ Info données actualisées

**API endpoint**:
- `GET /api/formations-map` → JSON des formations pour Leaflet

---

### 8️⃣ Système de cache et optimisation
**Implémentation**:
- ✅ Cache des données API 24h
- ✅ Limite de pagination (1000 enregistrements max)
- ✅ Timeouts sur requêtes API (60s)
- ✅ Retry automatique (3 tentatives)
- ✅ Logs détaillés pour debug

**Performance**:
- Temps chargement carte: < 2s
- Temps recherche avancée: < 1s (données cachées)
- Appels API minimisés via cache

---

## 🛠️ COMPÉTENCES COUVERTE DES MÉTIERS DU NUMÉRIQUE

### 📍 Compétence 1: **Gérer le patrimoine informatique**
**Vérification**: ✅ OUI

**Preuves**:
1. **Gestion des données**:
   - Création 2 tables MySQL (SearchStat, Remunerations)
   - Migrations Laravel pour versioning BD
   - Index optimisés pour requêtes fréquentes

2. **Sécurité**:
   - Authentification utilisateurs (bcrypt, CSRF)
   - Validation des données (Request validation)
   - Gestion des erreurs & logs (Monolog)

3. **Maintenance**:
   - Cache management (Redis/File)
   - Logs détaillés (app.log)
   - Fallback en cas d'erreur API

**Illustration**: 
- Migration: `database/migrations/2026_01_08_205440_create_search_stats_table.php`
- Modèle: `app/Models/SearchStat.php` (Eloquent ORM)
- Sécurité: Authentification Laravel + validation Request

---

### 🚨 Compétence 2: **Répondre aux incidents et demandes d'assistance**
**Vérification**: ✅ PARTIELLEMENT

**Preuves**:
1. **Gestion des erreurs**:
   - Try-catch sur appels API
   - Logs détaillés (INFO, WARNING, ERROR, CRITICAL)
   - Fallback aux données par défaut

2. **Support utilisateur**:
   - Formulaires de recherche avec validation
   - Messages d'erreur clairs
   - Historique recherches (aide à l'utilisateur)

3. **Documentation**:
   - Comments exhaustifs dans le code (docblocks PHP)
   - Explications logique métier
   - README du projet

**Points manquants pour "Complet"**:
- Pas d'email support
- Pas de chat/formulaire contact

**Illustration**:
- Service: `app/Services/DataGouvService.php` (catch exceptions)
- Logs: `storage/logs/laravel.log`

---

### 🌐 Compétence 3: **Développer la présence en ligne**
**Vérification**: ✅ OUI

**Preuves**:
1. **Frontend moderne**:
   - Tailwind CSS (responsive design)
   - UX/UI professionnelle
   - Accessible sans JavaScript (fallback)

2. **Carte interactive**:
   - Leaflet.js pour visualisation géographique
   - Design moderne et intuitif
   - Mobile-friendly

3. **Page d'accueil publique**:
   - Présentation claire de la solution
   - Call-to-action explicites
   - Responsive layout (mobile/tablet/desktop)

4. **Accessibilité**:
   - Structure HTML sémantique
   - Contraste des couleurs respecté
   - Formulaires accessibles

**Illustration**:
- Vue: `resources/views/home.blade.php` (Leaflet map)
- CSS: Tailwind dans vues Blade
- JS: `resources/js/app.js`

---

### 📋 Compétence 4: **Travailler en mode projet**
**Vérification**: ✅ OUI

**Preuves**:
1. **Planification**:
   - Hackathon = 15h en contrainte temps
   - Objectif clair (application orientation BTS)
   - Périmètre défini (recherche + stats + carte)

2. **Réalisation itérative**:
   - Branche de développement (`developp`)
   - Commits progressifs (feature = commit)
   - Version contrôlée

3. **Délivérables**:
   - Application fonctionnelle
   - BD opérationnelle
   - API intégrée
   - Frontend complet

4. **Documentation**:
   - Code commenté (docblocks)
   - Structure claire (MVC)
   - README avec instructions

**Illustration**:
- Branche: `git branch` → developp branch
- Commits: `git log --oneline`
- Code: Organisation MVC (Models, Views, Controllers)

---

### 📦 Compétence 5: **Mettre à disposition un service informatique**
**Vérification**: ✅ PARTIELLEMENT

**Preuves**:
1. **Déploiement**:
   - Application fonctionnelle et testée
   - Tests API (routes test-api)
   - Données validées

2. **Accessibilité**:
   - Application accessible en local (php artisan serve)
   - Routes claires et intuitives
   - Documentation d'utilisation

3. **Maintenance**:
   - Système de cache pour stabilité
   - Gestion erreurs robuste
   - Logs de monitoring

4. **Évolutivité**:
   - Architecture extensible (Services pattern)
   - Modèles facilement maintenables
   - Code réutilisable

**Points manquants pour "Complet"**:
- Pas de déploiement en production (heroku/AWS/etc)
- Pas de monitoring continu
- Documentation deploy incomplète

**Illustration**:
- Services: `app/Services/DataGouvService.php` (réutilisable)
- Routes: `routes/web.php` (endpoints clairs)
- Vues: `resources/views/` (UI complète)

---

### 🎓 Compétence 6: **Organiser son développement professionnel**
**Vérification**: ✅ OUI

**Preuves**:
1. **Apprentissage technologique**:
   - Laravel ecosystem (Services, Models, Migrations)
   - APIs publiques (intégration data.gouv.fr)
   - Frontend modern (Tailwind, Alpine)
   - Cartographie (Leaflet.js)

2. **Bonnes pratiques**:
   - MVC architecture
   - Dependency Injection (Laravel DI container)
   - Cache management
   - Error handling & logging
   - Code comments & documentation

3. **Évolution métier**:
   - Projet de synthèse complet (du concept à la réalisation)
   - Portefeuille de compétences variées
   - Contribution à l'orientation scolaire (utilité sociale)

4. **Persistance**:
   - Git versioning (commits réguliers)
   - Code révisable et améliorable
   - Base pour futures versions

**Illustration**:
- Architecture: Pattern Services + Models réutilisables
- Qualité code: PSR standards, docblocks exhaustifs
- Versioning: Git commits documentés

---

## 📊 RÉSUMÉ DES COMPÉTENCES

| Compétence | Couvert | Niveau | Preuves |
|-----------|---------|--------|--------|
| 1. Gérer patrimoine info | ✅ OUI | 5/5 | BD, sécurité, cache |
| 2. Répondre incidents | ✅ PARTIELLEMENT | 3/5 | Logs, fallback, validation |
| 3. Présence en ligne | ✅ OUI | 5/5 | Frontend, carte, UX |
| 4. Mode projet | ✅ OUI | 5/5 | Planning, réalisation, docs |
| 5. Service informatique | ✅ PARTIELLEMENT | 3/5 | App fonctionnelle, pas prod |
| 6. Développement perso | ✅ OUI | 5/5 | Apprentissage, bonnes pratiques |

---

## 📸 CAPTURES D'ÉCRAN À PRÉPARER

Pour la présentation orale E5, prévoir des captures de:

1. **Page d'accueil publique** 
   - Vue: Carte interactive, stats globales
   - URL: `/`

2. **Recherche avancée** (authentifiée)
   - Vue: Formulaire avec tous les filtres
   - URL: `/formations/recherche`

3. **Résultats de recherche**
   - Vue: Liste formations, données filtrées
   - Démonstration des filtres appliqués

4. **Dashboard utilisateur**
   - Vue: Historique, stats perso, top formations
   - URL: `/dashboard`

5. **Code source clé**
   - Service DataGouvService (connexion API)
   - Controller FormationSearchController (recherche)
   - Model SearchStat (BD + analytics)

6. **Base de données**
   - Schéma tables: search_stats, remunerations
   - Requêtes exemples (top formations, etc.)

---

## 💡 ARGUMENTS POUR LA PRÉSENTATION

### Problématique identifiée
> "Les élèves manquent souvent d'informations complètes sur l'offre de formations BTS et les carrières associées. Comment centraliser ces données pour faciliter l'orientation?"

### Solution apportée
> "Une plateforme web qui exploite les données publiques de data.gouv.fr pour proposer une vision holistique: formations disponibles + établissements + salaires des métiers + localisation géographique."

### Innovation pédagogique
> "Démarche data-driven: utilisation de vraies données publiques pour une problématique réelle (orientation scolaire), avec approche analytique (statistiques, analytics)."

### Compétences démontrées
- ✅ Maîtrise Laravel (architecture MVC, Services, Migrations)
- ✅ Intégration API externes (data.gouv.fr, gestion erreurs)
- ✅ Frontend moderne (Tailwind, Leaflet cartographie)
- ✅ Gestion BD (Eloquent ORM, migrations, indexes)
- ✅ Authentification & sécurité
- ✅ Analytics & statistiques
- ✅ Pensée projet (contrainte 15h)

---

## 📝 NOTES POUR LE CANDIDAT

### À compléter dans le tableau Excel:
- [ ] Colonne "Non évaluable": Laisser vide pour ce projet
- [ ] Colonne "Non maîtrisée": Aucune (ce projet couvre toutes les compétences attendues)
- [ ] Colonnes d'évaluation (Maître partielle / Bien maîtrisée / Excelle): À cocher selon votre auto-évaluation
- [ ] Description: Utiliser le contenu du present document

### À préparer pour présentation orale:
1. Diaporama (5 min max): Problème → Solution → Démonstration
2. Démo interactive: Montrer la plateforme en direct
3. Code review: Commenter 2-3 points clés du code
4. Réponses aux questions: Prévoir questions sur architecture, choix tech

### Documents à remettre:
- [ ] Lien Git (repo avec code source complet)
- [ ] README.md du projet
- [ ] Captures écran mentionnées ci-dessus
- [ ] Éventuels documents (UML, schéma BD, etc.)

---

**Document généré automatiquement | À adapter selon votre contexte et votre présentation orale**
