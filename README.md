# GUIDE DE REMPLISSAGE - TABLEAU DE SYNTHÈSE E5
**Votre projet: Métiers du Numérique - Plateforme d'Orientation BTS**

---

## 🎯 SECTION IDENTIFICATION

### À remplir dans votre fichier Excel:

**Nom et prénom**: [Votre nom]  
**N° candidat**: [Votre numéro]

**Centre de formation**: [Votre centre]  
**Option**: ☐ SISR   ☑ SLAM

**Adresse URL du portfolio**: [Sera remplie après avec les 4 réalisations]

---

## 📋 SECTION RÉALISATIONS PROFESSIONNELLES

### Intitulé et liste des documents/productions associés

```
Intitulé: MÉTIERS DU NUMÉRIQUE - PLATEFORME WEB D'ORIENTATION BTS

Type: Réalisation en cours de formation (TP - Hackathon janvier 2026)

Documents/Productions associés:
1. Code source (branche developp du Git) 
2. Application Laravel fonctionnelle (local)
3. Base de données (search_stats, remunerations tables)
4. Documentation technique (docblocks PHP + README)
5. Captures écrans (page d'accueil, recherche, dashboard, carte)
6. Diaporama présentation (à créer)
```

---

## ✅ SECTION COMPÉTENCES MISES EN ŒUVRE

**Instructions**: Pour chaque compétence, cochez ✓ si elle est couverte par le projet

### Ligne 1: **Gérer le patrimoine informatique**

```
Champ "Compétences mises en œuvre":
- Recenser et identifier les ressources numériques
  ✓ Base de données (2 tables): search_stats, remunerations
  ✓ Données API: formations BTS, effectifs par académie
  ✓ Ressources serveur: cache, logs

- Mettre en place et vérifier les niveaux d'habilitation 
  ✓ Authentification utilisateurs (login/register)
  ✓ Routes protégées (/dashboard, /formations/recherche)
  ✓ Roles implicites: utilisateurs = accès filtres avancés

- Vérifier les conditions de continuité d'un service informatique
  ✓ Cache 24h pour données API (stabilité)
  ✓ Fallback données par défaut si API indisponible
  ✓ Gestion erreurs robuste (try-catch, logs)

- Gérer des sauvegardes
  ✓ Database migrations (versions BD)
  ✓ Git versioning (historique complet)

- Vérifier le respect des règles d'utilisation des ressources numériques
  ✓ Respect CNIL (données anonymisées en stats)
  ✓ Respect des termes data.gouv.fr

✓ Cocher: OUI - Compétence couverte
Niveau: ☐ Non maîtrisée | ☐ Maîtrisée partiellement | ☑ Bien maîtrisée | ☐ Excellente
```

---

### Ligne 2: **Répondre aux incidents et demandes d'assistance**

```
Champ "Compétences mises en œuvre":
- Collecter, suivre et orienter les demandes
  ✓ Formulaire de recherche (collecte critères utilisateur)
  ✓ Enregistrement en BD (SearchStat model)
  ✓ Historique affichée dans dashboard

- Traiter les demandes concernant les services réseau et système
  ✓ Gestion API réseau (data.gouv.fr timeout, retry)
  ✓ Gestion erreurs système (base de données, cache)

- Traiter les demandes concernant les applications
  ✓ Validation des données (Request validation)
  ✓ Messages d'erreur explicites
  ✓ Fallback interfaces claires

- Participer à l'évaluation d'un incident ou d'une évolution
  ✓ Logs détaillés (app.log avec timestamps)
  ✓ Métriques d'utilisation (recherches par académie, etc.)

- Participer à la résolution des demandes
  ✓ Documentation du code (docblocks exhaustifs)
  ✓ Architecture claire pour maintenance

⚠️ Cocher: PARTIELLEMENT - Preuves d'assistance utilisateur limitées
Niveau: ☐ Non maîtrisée | ☑ Maîtrisée partiellement | ☐ Bien maîtrisée | ☐ Excellente

Note: Compétence démontrant la gestion des erreurs, validation, logs. 
Absence de chat/email support = pas "Bien maîtrisée"
```

---

### Ligne 3: **Développer la présence en ligne de l'organisation**

```
Champ "Compétences mises en œuvre":
- Participer à la valorisation de l'image de l'organisation
  ✓ Interface moderne (Tailwind CSS)
  ✓ Branding cohérent (couleurs, typographie, layout)
  ✓ Message clair (plateforme orientation scolaire)

- Référencer les services en ligne et mesurer leur visibilité
  ✓ SEO basics: meta tags, structure HTML sémantique
  ✓ Mesure visibilité: analytics via SearchStat (formations recherchées)
  ✓ API publique endpoint (/api/formations-map)

- Participer à l'évolution d'un site web
  ✓ Responsive design (mobile/tablet/desktop)
  ✓ Amélioration UX (filtres avancés, carte interactive)
  ✓ Évolutivité: Services réutilisables, architecture extensible

✓ Cocher: OUI - Compétence couverte
Niveau: ☐ Non maîtrisée | ☐ Maîtrisée partiellement | ☑ Bien maîtrisée | ☐ Excellente
```

---

### Ligne 4: **Travailler en mode projet**

```
Champ "Compétences mises en œuvre":
- Analyser les objectifs et les modalités d'organisation du projet
  ✓ Objectif clair: plateforme orientation BTS (hackathon)
  ✓ Contrainte temps: 15h (5-8 janvier 2026)
  ✓ Modalités: projet solo, données publiques

- Planifier les activités
  ✓ Sprints de 4 jours
  ✓ Features principales: recherche + API + BD + frontend
  ✓ Priorités: MVP fonctionnel > polish

- Évaluer les indicateurs de suivi du projet et analyser les écarts
  ✓ Tests manuels de chaque feature
  ✓ Validation des données (fixtures)
  ✓ Tests routes API

- Participer à l'évolution du projet
  ✓ Branches Git (master vs developp)
  ✓ Commits progressifs par feature
  ✓ Versionning explicite

- Faciliter la coordination des équipes
  ✓ Code bien organisé (MVC)
  ✓ Documentation pour futurs développeurs
  ✓ Architecture compréhensible

✓ Cocher: OUI - Compétence couverte
Niveau: ☐ Non maîtrisée | ☐ Maîtrisée partiellement | ☑ Bien maîtrisée | ☐ Excellente
```

---

### Ligne 5: **Mettre à disposition des utilisateurs un service informatique**

```
Champ "Compétences mises en œuvre":
- Réaliser les tests d'intégration et d'acceptation d'un service
  ✓ Routes de test (/test-api, /test-api/uniques, /test-api/detail)
  ✓ Validation données (Request validation rules)
  ✓ Tests API responses (JSON output validé)

- Déployer un service
  ✓ Application fonctionnelle et prête
  ✓ Migrations BD (php artisan migrate)
  ✓ Seeding données (if needed)

- Accompagner les utilisateurs lors de la mise en place d'un service
  ✓ Interface intuitive (UI/UX professionnelle)
  ✓ Aide contextuelle (messages clairs, validations)
  ✓ Documentation (README du projet)

- Assurer le service déployé et donne satisfaction à l'utilisateur
  ✓ Cache pour performance
  ✓ Fallback pour résilience
  ✓ Monitoring via logs

⚠️ Cocher: PARTIELLEMENT - Application locale, pas en production
Niveau: ☐ Non maîtrisée | ☑ Maîtrisée partiellement | ☐ Bien maîtrisée | ☐ Excellente

Note: Déploiement complet et monitoring en production = "Bien maîtrisée"
Absence = limitation majeure
```

---

### Ligne 6: **Organiser son développement professionnel**

```
Champ "Compétences mises en œuvre":
- Mettre en place son environnement d'apprentissage personnel
  ✓ Environnement Laravel local (docker, valet, sail)
  ✓ Outils development: VS Code, git, Postman
  ✓ Resources: docs Laravel, data.gouv.fr API docs

- Mettre en œuvre des outils et stratégies de veille informationnelle
  ✓ Suivi API data.gouv.fr (modifications données)
  ✓ Monitoring logs (erreurs métier)
  ✓ Analytics (formations recherchées = insight métier)

- Gérer son identité professionnelle
  ✓ Portfolio (ce projet + 3 autres = 4 réalisations)
  ✓ GitHub public (versionning visible)
  ✓ Démonstration compétences variées

- Développer son projet professionnel
  ✓ Apprentissage progressif: Laravel → Services → API
  ✓ Application réelle (orientation = use case authentique)
  ✓ Évolution possible (V2 avec plus de données, déploiement prod)

✓ Cocher: OUI - Compétence couverte
Niveau: ☐ Non maîtrisée | ☐ Maîtrisée partiellement | ☑ Bien maîtrisée | ☐ Excellente
```

---

## 📊 TABLEAU RÉCAPITULATIF À COCHER

| # | Compétence | Couvert | Niveau | Case à cocher |
|----|-----------|---------|--------|---------------|
| 1 | Gérer patrimoine informatique | ✅ OUI | Bien maîtrisée | ☑ Bien (5/5) |
| 2 | Répondre incidents/assistance | ✅ PARTIELLEMENT | Partiellement | ☑ Partiel (3/5) |
| 3 | Présence en ligne | ✅ OUI | Bien maîtrisée | ☑ Bien (5/5) |
| 4 | Mode projet | ✅ OUI | Bien maîtrisée | ☑ Bien (5/5) |
| 5 | Service informatique | ✅ PARTIELLEMENT | Partiellement | ☑ Partiel (3/5) |
| 6 | Développement professionnel | ✅ OUI | Bien maîtrisée | ☑ Bien (5/5) |

---

## 📝 DESCRIPTION À SAISIR DANS LE TABLEAU

### Section "Réalisations en cours de formation"

**Pour la ligne de votre projet, saisir**:

```
Intitulé: 
Métiers du Numérique - Plateforme web d'orientation BTS

Type de réalisation:
Réalisation en cours de formation (TP) - Hackathon janvier 2026

Description détaillée (à adapter dans la case du tableau):
« Application web développée en 15h lors du hackathon de janvier 2026.
Objectif: créer une plateforme d'orientation permettant aux élèves 
de découvrir les formations BTS du numérique en France.

Architecture: Application Laravel 12 complète avec frontend Blade/Tailwind,
cartographie interactive (Leaflet), authentification utilisateurs, et 
enregistrement des statistiques de recherche.

Données: Exploitation des APIs publiques de data.gouv.fr pour les 
effectifs BTS et rémunérations des métiers du numérique.

Fonctionnalités principales:
- Recherche avancée multifiltre (académie, ville, année, salaire)
- Dashboard avec analytics (formations/académies populaires)
- Cartographie interactive des établissements
- Authentification utilisateurs et gestion profils
- Système de cache et gestion erreurs robuste
- Enregistrement automatique des statistiques de recherche

Technologies: Laravel 12, MySQL, Blade, Tailwind CSS, Alpine.js, 
Leaflet.js, Vite.

Compétences mises en œuvre: 
Gestion BD, authentification, consommation API, frontend moderne,
architecture MVC, analytics & statistiques, travail sous contrainte 
temps, gestion erreurs et logging. »

Documents/productions associés:
- Code source (GitHub, branche developp)
- Application fonctionnelle (prête démo)
- Base de données (schéma + données de test)
- Captures écrans (page d'accueil, recherche, dashboard, carte)
- Documentation technique (docblocks, README)
```

---

## 🎬 PRÉPARATION DE LA PRÉSENTATION ORALE

### Diaporama (5 min max):

**Diapo 1**: Contexte
- Hackathon janvier 2026 (15h)
- Thème: APIs publiques
- Problématique: orientation scolaire

**Diapo 2**: Solution proposée
- Centralisation données BTS
- Recherche avancée multifiltre
- Cartographie + analytics

**Diapo 3**: Architecture technique
- Stack: Laravel 12 + Blade + Tailwind
- Sources: data.gouv.fr APIs
- BD + Cache + Authentification

**Diapo 4**: Démonstration live (ou vidéo)
- Page d'accueil + carte
- Recherche avancée (filtrer)
- Dashboard utilisateur

**Diapo 5**: Compétences démontrées
- Tableau des 6 compétences
- Points forts et adaptations possibles

### Points à démontrer:

1. **Page d'accueil** (30s)
   - Montrer carte interactive
   - Stats globales visibles

2. **Recherche avancée** (45s)
   - Faire un filtre (ex: académie Île-de-France)
   - Montrer résultats filtrés
   - Commenter l'API en arrière-plan

3. **Dashboard** (30s)
   - Montrer historique utilisateur
   - Top formations recherchées
   - Analytics

4. **Code clé** (45s)
   - Montrer DataGouvService (API)
   - Montrer migrations BD
   - Expliquer architecture

---

## 📸 CAPTURES À PRÉPARER

### Images pour portfolio/slides:

1. **home.png** - Page d'accueil avec carte
   ```bash
   URL: http://localhost:8000/
   Action: Ouvrir et faire une capture (Alt+Print)
   ```

2. **search.png** - Formulaire recherche avancée
   ```bash
   URL: http://localhost:8000/formations/recherche (après login)
   Captures filtres: académies, villes, année, salaire
   ```

3. **results.png** - Résultats de recherche
   ```bash
   Action: Appliquer filtre et montrer résultats
   ```

4. **dashboard.png** - Dashboard utilisateur
   ```bash
   URL: http://localhost:8000/dashboard
   Montrer stats, historique, top formations
   ```

5. **code_service.png** - Code DataGouvService
   ```bash
   Fichier: app/Services/DataGouvService.php
   Sélectionner: Méthode getBTSNumerique + connexion API
   ```

6. **code_model.png** - Modèle SearchStat
   ```bash
   Fichier: app/Models/SearchStat.php
   Sélectionner: Relationships + scopes
   ```

7. **database.png** - Schéma BD
   ```bash
   Outils: PhpMyAdmin ou DB client
   Montrer: tables search_stats, remunerations + indexes
   ```

---

## ❓ QUESTIONS POSSIBLES À L'ORAL

### Sur le projet:
- Q: "Pourquoi avoir choisi cet outils/cette architecture?"
  R: "Laravel offre une structure MVC solide, Blade pour templating, 
     Eloquent ORM pour BD. Parfait pour ce cas d'usage en 15h."

- Q: "Comment gérez-vous l'indisponibilité de l'API data.gouv?"
  R: "Via un système de fallback: données par défaut en cache local, 
     retry automatique 3x, logs détaillés pour debug."

- Q: "Quels défis avez-vous rencontrés?"
  R: "Volume de données API important → pagination/cache. 
     Déploiement local vs production → focus MVP local en 15h."

### Sur les compétences:
- Q: "Montrez-moi la sécurité de l'app?"
  R: "Authentification bcrypt, CSRF tokens, validation Request, 
     SQL injection prevention via Eloquent ORM."

- Q: "Comment mesurez-vous le succès du service?"
  R: "Analytics SearchStat: formations recherchées, académies populaires, 
     UX feedback via logs et métriques."

---

## ✅ CHECKLIST FINALE

Avant présentation orale:

- [ ] Document E5 rempli (tableau Excel)
- [ ] Diaporama préparé (5 slides)
- [ ] Captures d'écran prises
- [ ] Démo pratiquée (app locale lancée)
- [ ] Code commenté et présentable
- [ ] Réponses aux questions préparées
- [ ] Git repo accessible (branch developp)
- [ ] README du projet à jour
- [ ] Preuves compétences rassemblées

---

**Bonne chance pour votre présentation E5! 🎓**
