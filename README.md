# 📋 Micro-Messages : Documentation E5 BTS SIO SLAM

**Projet TP Laravel - 2e année**  
**Date** : Avril 2026

---

## 📑 TABLE DES MATIÈRES

1. [Informations de base](#1-informations-de-base)
2. [Description du projet](#2-description-du-projet)
3. [Réalisations professionnelles](#3-réalisations-professionnelles)
4. [Résumé tableau E5](#4-résumé-tableau-e5)
5. [Points clés diaporama](#5-points-clés-diaporama)
6. [Défis surmontés](#6-défis-surmontés--solutions)
7. [Justification compétences E5](#7-justification-compétences-e5)
8. [Checklist finale](#8-checklist-finale)

---

## 1️⃣ INFORMATIONS DE BASE

### Pour le tableau Excel

- **Nom et Prénom** : [À remplir]
- **N° Candidat** : [À remplir]
- **Centre de formation** : [À remplir]
- **Option** : SLAM ✅
- **Adresse URL Portfolio** : [À remplir si applicable]

---

## 2️⃣ DESCRIPTION DU PROJET

### Titre
**Micro-Messages - Plateforme de Micro-messagerie Sociale**

### Description pour colonne "Polices" (Copier-coller dans Excel)

Plateforme web complète de micro-messagerie inspirée de X (Twitter), développée en Laravel dans un contexte pédagogique. L'application permet aux utilisateurs authentifiés de publier des messages courts (140 caractères), interagir via likes/commentaires/reposts, construire un réseau social (follow/unfollow), communiquer en privé, et recevoir des notifications événementielles. L'interface est responsive et proposée en mode sombre/clair persistant. Le projet démontre une maîtrise complète de Laravel (authentification Breeze, relations Eloquent complexes, migrations BDD, gestion fichiers, sécurité).

### Contexte
- **Type de réalisation** : TP Laravel pratique
- **Année** : 2e année BTS SIO SLAM
- **Cadre** : Travail individuel autonome
- **Énoncé** : https://cours.brosseau.ovh/tp/laravel/x.html

### Objectif pédagogique
Maîtriser les concepts clés de Laravel en implémentant une application web réelle avec authentification, gestion de base de données complexe, relations entre entités, gestion de fichiers, et interface utilisateur moderne.

### Scope réalisé

| Catégorie | État | Détail |
|-----------|------|--------|
| **Core obligatoire** | ✅ | 8/8 éléments (100%) |
| **Évolutions facultatives** | ✅ | 8/11 implémentées (73%) |
| **Bonus (non énumérés)** | ✅ | 4 features (reposts, bookmarks, suggestions, dark mode) |
| **Total** | ✅ | **20 fonctionnalités complètes** |

### Technologies utilisées

**Backend**
- Laravel 12.x
- PHP 8.5
- MySQL
- Laravel Breeze (authentification)
- Laravel Storage (fichiers)

**Frontend**
- Blade (templating)
- Tailwind CSS 3.x
- Alpine.js
- JavaScript Vanilla

**Outils**
- Composer, npm
- Vite (build)
- Git (versioning)

---

## 3️⃣ RÉALISATIONS PROFESSIONNELLES

### Réalisation #1 : Architecture MVC Complète

**Description**  
Implémentation d'une architecture Model-View-Controller rigoureuse avec 6 modèles Eloquent, 11 contrôleurs spécialisés et 44 vues Blade organisées par domaine fonctionnel.

**Détails techniques**
- **Modèles** (app/Models/) : User, Message, Comment, Conversation, DirectMessage, Notification
- **Contrôleurs** (app/Http/Controllers/) : MessageController, ProfileController, FollowerController, LikeController, CommentController, RepostController, BookmarkController, SearchController, DirectMessageController, SuggestionController, NotificationController
- **Vues** : 44 fichiers .blade.php organisés en dossiers (messages/, profiles/, users/, bookmarks/, search/, notifications/, suggestions/, auth/, dm/)
- **Routes** : 30+ routes web + 3 endpoints API

**Preuves concrètes**
- Fichiers : `app/Models/*.php`, `app/Http/Controllers/*.php`, `resources/views/**/`, `routes/web.php`
- Structure : Organisation par domaine métier
- Qualité : Conventions Laravel respectées, noms explicites

**Compétence E5** : Travailler en mode projet

---

### Réalisation #2 : Modélisation Base de Données Complexe

**Description**  
Création d'une base de données relationnelle sophistiquée avec 9 tables interconnectées, relations N:N, relations polymorphes, et contraintes d'intégrité.

**Détails techniques**

**Tables** (9 total) :
1. `users` : Utilisateurs + avatar, banner, bio
2. `messages` : Publications + image
3. `comments` : Commentaires
4. `followers` : Relations de suivi (N:N)
5. `likes` : Likes sur messages (N:N)
6. `reposts` : Reposts (N:N)
7. `bookmarks` : Signets (N:N)
8. `conversations` : Conversations DM
9. `direct_messages` : Messages privés
10. `notifications` : Notifications polymorphes

**Relations principales**
- User → Messages (1:N)
- User → Followers (N:N bidirectionnel)
- Message → Likes/Comments/Reposts/Bookmarks (1:N + N:N)
- Conversation → DirectMessages (1:N)
- Notification polymorphe → Multiple

**Migrations**
- Versions numérotées chronologiquement (2026_01_27_*.php à 2026_02_03_*.php)
- Commentaires explicatifs pour documentation
- Contraintes d'intégrité (onDelete('cascade'), unique indexes)

**Preuves concrètes**
- Fichiers : `database/migrations/*.php` (14 migrations)
- Modèles : `app/Models/*.php` (relations définies)
- Contraintes : Unique indexes, foreign keys, cascade delete

**Compétence E5** : Gérer le patrimoine informatique

---

### Réalisation #3 : Authentification Sécurisée

**Description**  
Mise en place de l'authentification utilisateur via Laravel Breeze avec inscription, connexion, suppression de compte, et protection des routes sensibles.

**Détails techniques**
- **Authentification** : Laravel Breeze (scaffold complet)
- **Password** : Hachage sécurisé (Laravel Hash::make)
- **Routes protégées** : Middleware 'auth' appliqué
- **Session** : Gestion automatique Laravel
- **CSRF** : Protection automatique (@csrf dans formulaires)
- **Vérification** : auth()->check(), auth()->user(), auth()->id()

**Protections**
- Suppression de compte sécurisée
- Messages directs privés
- Publications liées à utilisateur authentifié
- Validations server-side complètes

**Preuves concrètes**
- Fichiers : `routes/auth.php`, `resources/views/auth/*`
- Middleware : `routes/web.php`
- Contrôleurs : Vérifications `auth()->user()`

**Compétence E5** : Gérer le patrimoine informatique

---

### Réalisation #4 : Gestion des Fichiers & Ressources

**Description**  
Implémentation complète du système d'upload de fichiers pour avatars, bannières et images de messages, avec validation, stockage organisé et suppression sécurisée.

**Détails techniques**

**Upload d'images**
- Validation MIME : jpeg, png, jpg, gif, webp
- Limitation taille : 5MB par image
- Stockage : Laravel Storage disque public (`storage/app/public/`)
- Organisation : `/messages/`, implicite par contexte
- Suppression cascade : Images supprimées lors suppression entités

**Implémentation**
- MessageController::store() : Upload image avec message
- ProfileController::update() : Avatar et bannière upload
- Validation automatique : `'image' => 'nullable|image|mimes:...|max:5120'`

**Frontend**
- Preview d'image avant upload (JavaScript FileReader API)
- Bouton upload stylisé
- Suppression possible du preview
- Gestion d'erreurs affichées

**Preuves concrètes**
- Fichiers : `app/Http/Controllers/MessageController.php`, `ProfileController.php`
- Vues : `resources/views/messages/create.blade.php`
- Storage : Références `Storage::store()`, `asset('storage/'...)`

**Compétence E5** : Gérer le patrimoine informatique

---

### Réalisation #5 : Notifications Événementielles

**Description**  
Implémentation d'un système de notifications polymorphes pour notifier utilisateurs lors de nouveaux followers, likes, commentaires et messages directs.

**Détails techniques**

**Types de notifications**
1. **Follow** : Quelqu'un me suit
2. **Like** : Quelqu'un like mon message
3. **Comment** : Quelqu'un commente mon message
4. **DM** : Quelqu'un m'envoie un message direct

**Architecture**
- Modèle Notification : Relations polymorphes (morphTo)
- Champs : user_id (destinataire), from_user_id (émetteur), type, notifiable_type/id, read flag
- Flexibilité : Un modèle pour tous les types

**Création de notifications**
- LikeController : Type 'like'
- CommentController : Type 'comment'
- FollowerController : Type 'follow'
- DirectMessageController : Type 'dm'

**Affichage**
- Page NotificationController::index() : Toutes notifications
- Badge : Compteur unreadNotifications()
- Read flag : Marquage lu/non lu

**Preuves concrètes**
- Modèle : `app/Models/Notification.php` (morphTo, morphs)
- Contrôleur : `app/Http/Controllers/NotificationController.php`
- Utilisation : LikeController, CommentController, FollowerController, DirectMessageController
- Vue : `resources/views/notifications/index.blade.php`

**Compétence E5** : Répondre aux incidents et demandes d'assistance

---

### Réalisation #6 : Messages Privés & Conversations

**Description**  
Système complet de messagerie directe permettant conversations privées entre utilisateurs, avec historique et marquage messages comme lus/non lus.

**Détails techniques**

**Modèles**
- **Conversation** : Regroupement entre 2 utilisateurs
  - Unique constraint : Empêche doublons
  - Méthode `getOtherUser($userId)` : Autre participant
  - Méthode `findOrCreateBetween()` : Crée ou retrouve
  - Relation `lastMessage()` : Dernier message pour preview

- **DirectMessage** : Message dans conversation
  - conversation_id FK, sender_id FK, content, read flag

**Contrôleur DirectMessageController**
- `index()` : Liste conversations de l'utilisateur
- `show($userId)` : Affiche conversation + marque comme lus
- `store()` : Envoie message + notifie destinataire
- `create()` : Formulaire nouvelle conversation

**Features**
- Création automatique conversation si n'existe pas
- Marquage automatique messages comme lus
- Historique complet
- Notifications envoyées
- Tri par conversation la plus récente

**Preuves concrètes**
- Modèles : `app/Models/Conversation.php`, `app/Models/DirectMessage.php`
- Contrôleur : `app/Http/Controllers/DirectMessageController.php`
- Migrations : `database/migrations/*create_conversations_table.php`, `*create_direct_messages_table.php`
- Vues : `resources/views/messages/dm/*.blade.php`

**Compétence E5** : Répondre aux incidents et demandes d'assistance

---

### Réalisation #7 : Interactions Sociales

**Description**  
Système complet d'interactions (likes, commentaires, reposts, bookmarks) permettant aux utilisateurs d'interagir avec messages avec compteurs et indicateurs.

**Détails techniques**

**Interactions**

1. **Likes** (LikeController)
   - Relation N:N User ↔ Message
   - Toggle : Like/Unlike selon état
   - Compteur : `$message->likes()->count()`
   - Check utilisateur : `$message->isLikedBy(auth()->user())`
   - Crée notification

2. **Commentaires** (CommentController)
   - Modèle Comment : user_id FK, message_id FK, content (140 chars)
   - Relation 1:N : Message::comments()
   - Thread sous message
   - Suppression par auteur seulement
   - Crée notification

3. **Reposts** (RepostController)
   - Relation N:N User ↔ Message
   - Toggle pattern (similaire likes)
   - Repost visible dans timeline
   - Compteur

4. **Bookmarks** (BookmarkController)
   - Relation N:N User ↔ Message
   - Toggle pattern
   - Page `/bookmarks` : Liste signets utilisateur
   - Filtrage messages enregistrés

**Pattern toggle**
```
Si User action Message :
  - Si existe : detach() (remove)
  - Si n'existe pas : attach() (add)
Logique : Clic multiple = action/retrait automatique
```

**Preuves concrètes**
- Contrôleurs : `LikeController.php`, `CommentController.php`, `RepostController.php`, `BookmarkController.php`
- Modèles : `app/Models/Message.php` (relations + methods), `app/Models/Comment.php`
- Migrations : `*create_likes_table.php`, `*create_comments_table.php`, etc.
- Vues : Affichage boutons dans `resources/views/messages/*.blade.php`

**Compétence E5** : Développer la présence en ligne

---

### Réalisation #8 : Réseau Social Fonctionnel

**Description**  
Système complet de réseau social permettant suivre/ne plus suivre d'autres utilisateurs, consulter feed personnalisé et découvrir suggestions.

**Détails techniques**

**Follow/Unfollow** (FollowerController)
- Relation N:N : User → User (bidirectionnel asymétrique)
- User.following() : Utilisateurs que je suis
- User.followers() : Mes abonnés
- Table pivot `followers` : Contrainte unique (user_id, followed_id)
- Routes : `/user/{id}/follow` (POST), `/user/{id}/unfollow` (POST)
- Crée notification de type 'follow'

**Feed Personnalisé** (MessageController::feed)
- Affiche messages uniquement des utilisateurs suivis
- Query : `whereIn('user_id', $user->following()->pluck('id'))`
- Tri chronologique
- Page `/feed`

**Suggestions d'utilisateurs** (SuggestionController)
- Affiche utilisateurs que l'utilisateur ne suit pas
- Logique : `where('id', '!=', auth()->id())->whereNotIn('id', following_ids())`
- Page `/suggestions`
- Bouton follow directement

**Affichages**
- Page profil `/user/{id}` : Messages utilisateur
- Listes `/user/{id}/followers`, `/user/{id}/following`
- Compteurs : Abonnés, abonnements

**Preuves concrètes**
- Contrôleurs : `FollowerController.php`, `SuggestionController.php`, `MessageController.php` (feed)
- Modèles : `app/Models/User.php` (following(), followers())
- Migrations : `*create_followers_table.php`
- Vues : `resources/views/messages/feed.blade.php`, `resources/views/suggestions/index.blade.php`

**Compétence E5** : Développer la présence en ligne

---

### Réalisation #9 : Profils Utilisateur Personnalisables

**Description**  
Gestion complète des profils permettant personnaliser avatar, bannière, bio, et consulter/éditer informations. Profils sont point focal identité utilisateur.

**Détails techniques**

**Champs profil** (User model)
- `avatar` : Chemin image avatar (nullable)
- `banner` : Chemin image bannière (nullable)
- `bio` : Bio utilisateur (nullable, max 160 chars)
- Migration : `add_profile_fields_to_users_table`

**Édition de profil** (ProfileController)
- GET `/profile/edit` : Formulaire édition
- PUT `/profile/update` : Enregistre modifications
- Validation : Email unique, image validation
- Upload avatar/banner avec validation
- Suppression ancien fichier avant nouveau
- Flash messages succès/erreur

**Page profil utilisateur** (/user/{id})
- Affichage avatar, bannière, bio, name, email
- Liste messages publié par utilisateur
- Compteurs : messages, followers, following
- Boutons follow/unfollow si ce n'est pas mon profil
- Listes followers/following sur pages dédiées

**Suppression de compte**
- GET `/profile/delete` : Confirmation
- DELETE `/profile/delete` : Suppression cascade
- Redirection après suppression

**Affichage dans vues**
- Avatar dans sidebar
- Avatar et nom sur chaque message/commentaire
- Bannière surnom profil

**Preuves concrètes**
- Contrôleur : `app/Http/Controllers/ProfileController.php`
- Modèle : `app/Models/User.php` (fillable)
- Migration : `*add_profile_fields_to_users_table.php`
- Vues : `resources/views/profile/*`, affichage avatar dans layouts

**Compétence E5** : Développer la présence en ligne

---

### Réalisation #10 : Interface Responsive & UX Moderne

**Description**  
Interface utilisateur moderne, responsive et accessible, avec design inspiré Twitter/X, mode sombre/clair persistant, ergonomie optimisée pour mobile/desktop.

**Détails techniques**

**Framework CSS**
- **Tailwind CSS 3.x** : Utility-first
- Classes : `flex`, `space-x-4`, `rounded-full`, `shadow-md`, etc.
- Responsive : `hidden lg:block`, `sm:`, `md:`, `lg:`, `xl:` breakpoints
- Dark mode : `:dark:` variant, `:class="darkMode ? 'bg-black' : 'bg-white'"`

**Dark Mode avec Alpine.js**
- **State** : `x-data="{ darkMode: localStorage.getItem('darkMode') === 'false' ? false : true }"`
- **Persistence** : `x-init="$watch('darkMode', val => localStorage.setItem('darkMode', val))"`
- **Application** : `:class="darkMode ? 'bg-black text-white' : 'bg-white text-black'"`
- **Bouton toggle** : Bascule localStorage + classe HTML

**Responsive Design**
- Sidebar gauche : `hidden lg:block` (visible desktop, caché mobile)
- Layout 3-colonnes desktop : Sidebar + Main + Rightbar
- Layout mono-colonne mobile : Optimisé petit écran
- Navigation collapsible
- Boutons + inputs adaptés à touch

**Composants Blade**
- `<x-twitter-layout>` : Layout principal réutilisable
- Inclusion navigation, sidebars, structures communes

**Typographie & Design**
- Police Inter, poids 400-700
- Icônes SVG inline (Twitter-like)
- Couleurs : Noir/blanc adaptées mode
- Hover effects fluides, focus states accessibles

**Pagination "Load More"**
- Bouton "Charger plus" au lieu pagination classique
- Appel API asynchrone
- Ajout dynamique messages au DOM
- Indicateur "Pas plus de messages"

**Preuves concrètes**
- Layout : `resources/views/layouts/twitter.blade.php`
- Vues : Toutes utilisent layout et Tailwind
- CSS : `resources/css/app.css`
- JavaScript : Alpine.js dans layouts
- Responsive : Vérifiable en redimensionnant navigateur

**Compétence E5** : Développer la présence en ligne

---

### Réalisation #11 : API & Pagination Asynchrone

**Description**  
Implémentation d'une API REST avec endpoints JSON permettant chargement asynchrone de messages, optimisant l'expérience utilisateur et réduisant charge serveur.

**Détails techniques**

**Endpoints API**
1. **GET /api/messages** : Messages publics paginés
2. **GET /api/user/{id}/messages** : Messages d'un utilisateur paginé
3. **GET /api/feed** : Messages du feed personnalisé (authentifié)

**Structure Response**
```json
{
  "messages": [
    {
      "id": 1,
      "content": "...",
      "user": {...},
      "likes_count": 5,
      "comments": [...]
    }
  ],
  "hasMore": true,
  "nextPage": 2
}
```

**Pagination**
- Limit par défaut : 2 messages par page
- Paramètre `page` : Numéro page demandée
- Boolean `hasMore` : S'il y a plus de messages
- Chargement itératif : Page 1 → 2 → 3

**Eager Loading**
- Requête optimisée : `.with(['user', 'likes', 'comments.user', 'reposts', 'bookmarks'])`
- Réduit N+1 queries problem
- Retourne données complètes en une requête

**Frontend Implementation**
- Bouton "Charger plus" au bas page
- Appel JavaScript fetch() à /api/messages?page=X
- Création de nouveaux éléments DOM
- Update page number pour prochain clic

**Routes**
- Toutes routes API commencent par `/api/`
- Retournent JSON (pas HTML)
- Middleware 'auth' sur endpoints restreints

**Preuves concrètes**
- Routes : `routes/web.php` (GET /api/messages, etc.)
- Contrôleur : `app/Http/Controllers/MessageController.php` (loadMore, loadMoreUser, loadMoreFeed)
- Frontend : JavaScript code dans vues pour fetch + DOM manipulation

**Compétence E5** : Mettre à disposition des utilisateurs un service informatique

---

## 4️⃣ RÉSUMÉ TABLEAU E5

### Description synthétique pour colonne "Polices" (À copier dans Excel)

**Micro-Messages** - Plateforme de micro-messagerie sociale développée en Laravel (2e année). Application web complète avec authentification, gestion de base de données relationnelle complexe, interactions sociales (likes, commentaires, reposts, bookmarks), réseau social (follow/unfollow, feed personnalisé, suggestions), messages directs, notifications polymorphes, profils utilisateur personnalisables, et interface responsive avec mode sombre persistant. Scope : 8/8 core obligatoires + 8/11 évolutions facultatives + 4 bonus = 20 features. Technologies : Laravel 12, PHP 8.5, MySQL, Blade, Tailwind CSS, Alpine.js, Laravel Storage.

### Réalisations listées (Pour tableau Excel)

| # | Titre | Description courte | Compétence E5 |
|---|---|---|---|
| 1 | Architecture MVC Complète | 6 modèles, 11 contrôleurs, 44 vues, 30+ routes | Travailler en mode projet |
| 2 | BD Relationnelle Complexe | 9 tables, relations N:N + polymorphes, migrations versionnées | Gérer le patrimoine informatique |
| 3 | Authentification Sécurisée | Laravel Breeze, middleware, CSRF, hachage password | Gérer le patrimoine informatique |
| 4 | Gestion Fichiers & Ressources | Upload avatar/bannière/images, validation MIME, stockage organisé | Gérer le patrimoine informatique |
| 5 | Notifications Événementielles | Système polymorphe : follow, like, comment, DM | Répondre aux incidents et demandes |
| 6 | Messages Privés & Conversations | Conversations bidirectionnelles, historique, notifications | Répondre aux incidents et demandes |
| 7 | Interactions Sociales Complètes | Likes, commentaires, reposts, bookmarks avec compteurs | Développer la présence en ligne |
| 8 | Réseau Social Fonctionnel | Follow/unfollow, feed personnalisé, suggestions | Développer la présence en ligne |
| 9 | Profils Utilisateur Personnalisables | Avatar, bannière, bio, édition, suppression compte | Développer la présence en ligne |
| 10 | Interface Responsive & UX Moderne | Tailwind CSS, mode sombre/clair persistent, mobile-friendly | Développer la présence en ligne |

---

## 5️⃣ POINTS CLÉS DIAPORAMA

### Structure recommandée (11 slides)

**Slide 1 : Introduction du projet**
- Titre : "Micro-Messages - Plateforme de Micro-messagerie Social"
- Subtitle : "TP Laravel - 2e année BTS SIO SLAM"
- Contexte : Inspiration Twitter/X, objectif = maîtriser Laravel
- Visuels : Logo 𝕏, screenshot du mur public

**Slide 2 : Scope & Réalisations**
- Core obligatoire : 8 éléments ✅
- Évolutions implémentées : 12 features (8 facultatives + 4 bonus)
- Non implémentés : @mentions, groupes, etc.
- Tableau comparatif énoncé vs réalisé

**Slide 3 : Architecture générale**
- Diagramme MVC : Modèles (6), Contrôleurs (11), Vues (44)
- Stack technique : Laravel 12, PHP 8.5, MySQL, Blade, Tailwind, Alpine.js
- Schéma BDD simplifié : 9 tables, relations clés
- Preuves : Structure dossiers app/, routes/web.php (30+ routes), database/migrations/

**Slide 4 : Base de données & Modélisation**
- Modèles clés avec relations :
  - User → Messages (1:N)
  - User → Followers (N:N bidirectionnel)
  - Message → Likes/Comments/Reposts/Bookmarks (N:N)
  - Conversation + DirectMessage (1:N)
  - Notification (polymorphe)
- Diagramme ER simplifié
- Preuves : app/Models/*.php, database/migrations/

**Slide 5 : Fonctionnalités - Interactions sociales**
- Likes avec compteur
- Commentaires (140 chars)
- Reposts (bonus)
- Bookmarks (bonus)
- Preuves : LikeController, CommentController, Message model (relations + methods)

**Slide 6 : Fonctionnalités - Communication**
- Messages privés avec conversations
- Notifications événementielles (follow, like, comment, dm)
- Badge compteur unread
- Preuves : DirectMessageController, NotificationController, Conversation model

**Slide 7 : Fonctionnalités - Réseau Social**
- Follow/Unfollow
- Feed personnalisé (messages des suivis)
- Suggestions d'utilisateurs
- Profiles (avatar, bannière, bio)
- Preuves : FollowerController, SuggestionController, ProfileController

**Slide 8 : Interface & UX**
- Design responsive (mobile-first)
- Mode sombre/clair persistent (localStorage + Alpine.js)
- Design inspiré Twitter/X
- Pagination "Charger plus"
- Preuves : resources/views/layouts/twitter.blade.php, app.css, Alpine.js code

**Slide 9 : API & Performance**
- 30+ routes HTTP organisées
- 3 endpoints API JSON pour pagination asynchrone
- Eager loading Eloquent (.with()) pour optimiser requêtes
- Preuves : routes/web.php, MessageController (@loadMore), API responses

**Slide 10 : Défis surmontés & Apprentissages**
- Défis rencontrés + solutions (voir section 6)
- Compétences acquises (relations BDD, permissions, upload, dark mode)
- Points clés de la maîtrise Laravel

**Slide 11 : Résumé & Compétences E5**
- Récapitulatif scope (20 features)
- Map aux 6 compétences E5 évaluées
- Preuves à présenter

---

## 6️⃣ DÉFIS SURMONTÉS & SOLUTIONS

### Défi 1 : Relations Base de Données Complexes

**Défi** : Implémenter les relations N:N (followers, likes, etc.) et polymorphes (notifications)

**Solution** :
- Utilisation de `belongsToMany()` avec timestamps
- Tables pivot créées via migrations
- Contrainte d'unicité pour éviter doublons (followers: unique['user_id', 'followed_id'])
- Relations polymorphes avec `morphs()` et `morphTo()`

**Preuves** : 
- app/Models/User.php (following(), followers(), likes())
- app/Models/Message.php
- app/Models/Notification.php (morphTo)
- database/migrations/

**Apprentissage** : Compréhension profonde des relations Eloquent, optimisation requêtes

---

### Défi 2 : Upload & Stockage de Fichiers

**Défi** : Gérer les avatars, bannières, images de messages sans encombrer la BDD

**Solution** :
- Laravel Storage disk public
- Validation MIME et taille (5MB)
- Organisation par dossier (messages/, avatars/)
- Suppression cascade lors suppression entités

**Preuves** :
- MessageController.store() (image upload)
- ProfileController (avatar/banner)
- Storage references dans vues
- Validation rules (mimes:jpeg,png,jpg,gif,webp|max:5120)

**Apprentissage** : Gestion fichiers professionnelle, validation sécurisée

---

### Défi 3 : Migrations Évolutives

**Défi** : Ajouter colonnes (avatar, banner, bio) au modèle User sans refonte complète

**Solution** :
- Migration d'altération : `Schema::table('users', ...)`
- Rollback safe avec `down()`
- Séparation migrations core vs évolutions

**Preuves** :
- database/migrations/2026_02_02_175340_add_profile_fields_to_users_table.php

**Apprentissage** : Evolution BDD maîtrisée, versionning de migrations

---

### Défi 4 : Permissions & Authentification

**Défi** : Empêcher un utilisateur de modifier/liker/commenter messages d'autres

**Solution** :
- Middleware 'auth' sur routes protégées
- Vérification `auth()->id()` dans contrôleurs
- Validation implicite par relations (user()->messages())

**Preuves** :
- routes/web.php (middleware)
- MessageController (auth()->user()->messages()->create())
- ProfileController (suppression compte sécurisée)

**Apprentissage** : Sécurité applicative, autorisation granulaire

---

### Défi 5 : Notifications Polymorphes

**Défi** : Gérer 4 types de notifications (follow, like, comment, dm) différentes avec même model

**Solution** :
- Relations polymorphes Laravel (morphTo(), morphs())
- Type string pour identifier événement
- Création ciblée dans chaque contrôleur

**Preuves** :
- Notification model (morphs)
- NotificationController
- Utilisation dans Like/Comment/FollowerController/DirectMessageController

**Apprentissage** : Patterns avancés Eloquent, flexibilité architecturale

---

### Défi 6 : Dark Mode Persistent

**Défi** : Mémoriser préférence dark/light mode entre sessions utilisateur

**Solution** :
- Alpine.js x-data pour état global
- localStorage pour persistence
- x-watch pour réagir aux changements
- :class conditionnel pour appliquer styles

**Preuves** :
- resources/views/layouts/twitter.blade.php :
  - `x-data="{ darkMode: localStorage.getItem('darkMode') === 'false' ? false : true }"`
  - `x-init="$watch('darkMode', val => localStorage.setItem('darkMode', val))"`
  - `:class="darkMode ? 'bg-black text-white' : 'bg-white text-black'"`

**Apprentissage** : Alpine.js avancé, localStorage, UX moderne

---

### Défi 7 : Pagination Asynchrone

**Défi** : Charger plus de messages sans rechargement page (type Twitter "Load More")

**Solution** :
- Endpoints API JSON (/api/messages, /api/user/{id}/messages, /api/feed)
- Response structurée (messages, hasMore, nextPage)
- JavaScript fetch + DOM manipulation
- Query parameter 'page' pour tracker position

**Preuves** :
- MessageController (loadMore, loadMoreUser, loadMoreFeed)
- routes/web.php
- Frontend JavaScript dans vues

**Apprentissage** : API design, AJAX asynchrone, performance UX

---

## 7️⃣ JUSTIFICATION COMPÉTENCES E5

### Compétence 1 : Capacité à rendre compte d'un travail réalisé

**Preuve Micro-Messages** :
- Projet finalisé et fonctionnel
- Documentation README complète
- Code bien structuré et commenté
- Structure logique et maintenable

**À présenter** : Diaporama + portfolio + démo fonctionnalités

---

### Compétence 2 : Gérer le patrimoine informatique

**Preuve Micro-Messages** :
- 9 tables BDD versionnées
- Migrations pour évolution schéma
- Storage fichiers utilisateurs (avatars, images, bannières)
- Sauvegardes via BDD (user data, messages, relations)
- Habilitations via authentification Breeze

**À présenter** : Schéma BDD, migrations, code storage, sécurité

---

### Compétence 3 : Répondre aux incidents et demandes d'assistance

**Preuve Micro-Messages** :
- Système de notifications complet
- Messages directs pour assistance entre utilisateurs
- Gestion des demandes (comments, likes comme feedback)
- Historique des messages privés

**À présenter** : DM fonctionnels, notifications affichées, système événementiel

---

### Compétence 4 : Développer la présence en ligne de l'organisation

**Preuve Micro-Messages** :
- Interface web responsive et moderne
- Design conforme aux standards actuels (Twitter-like)
- Personnalisation utilisateurs (avatar, bannière, bio)
- Partage possible de contenu (reposts, comments)
- Médias numériques intégrés (images)

**À présenter** : Screenshots design, responsive test, UI attrayante

---

### Compétence 5 : Travailler en mode projet

**Preuve Micro-Messages** :
- Objectives clairs (énoncé TP)
- Architecture plannifiée (MVC)
- Livrables définis (App + documentation)
- Découpage en tâches (par domaine fonctionnel)
- Indicateurs de progression (core + évolutions)

**À présenter** : Progression implémentation, structure architecturale

---

### Compétence 6 : Mettre à disposition des utilisateurs un service informatique

**Preuve Micro-Messages** :
- API complète (30+ endpoints)
- Tests fonctionnels (app complète et opérationnelle)
- Déploiement possible (`php artisan serve`)
- Accompagnement utilisateurs (UI intuitive)
- Documentation installation + utilisation

**À présenter** : Démo live (si possible) ou vidéo, endpoints API

---

### Compétence 7 : Organiser son développement professionnel

**Preuve Micro-Messages** :
- Apprentissages : Laravel, Blade, Tailwind, Alpine.js, BDD relations
- Techniques émergentes : Modern frontend + responsive design
- Veille : Utilisation frameworks/libs récents
- Identité professionnelle : Code quality, patterns Laravel

**À présenter** : Technologies utilisées, apprentissages listés, veille

---

## 8️⃣ CHECKLIST FINALE

### Tableau Excel E5
- [ ] Informations de base complétées (nom, prénom, n° candidat, centre)
- [ ] Description du projet remplie (colonne Polices)
- [ ] 10 réalisations principales listées
- [ ] Compétences E5 mappées par réalisation
- [ ] Preuves documentées (références fichiers/routes)

### Diaporama
- [ ] 11 slides structurées
- [ ] Visuels (captures d'écran, schémas)
- [ ] Défis surmontés présentés (2-3 minimum)
- [ ] Apprentissages clairs
- [ ] Mapping compétences E5 visible

### Portfolio
- [ ] URL accessible (si applicable)
- [ ] Application déployée ou démo vidéo
- [ ] Screenshots de toutes les fonctionnalités principales
- [ ] Documentation README lisible

### Présentation orale
- [ ] Notes de présentation préparées
- [ ] Accroche préparée (30 secondes)
- [ ] Démo live préparée (ou vidéo backup)
- [ ] Réponses aux questions pièges préparées

### Preuves techniques
- [ ] Fichiers clés identifiés
- [ ] Routes documentées
- [ ] Screenshots pertinents collectés
- [ ] Extraits de code à présenter

---

## 📌 RESSOURCES

**Fichiers clés du projet**
- `app/Models/*.php` : 6 modèles avec relations
- `app/Http/Controllers/*.php` : 11 contrôleurs
- `database/migrations/*.php` : 14 migrations
- `resources/views/**/` : 44 vues Blade
- `routes/web.php` : 30+ routes
- `README.md` : Documentation complète

**Énoncé du TP**
https://cours.brosseau.ovh/tp/laravel/x.html

---

**Document créé pour E5 BTS SIO SLAM - Micro-Messages**  
**Projet TP Laravel - 2e année**
