# ⚡ RÉSUMÉ 1 PAGE - POINTS CLÉS E5
**À imprimer pour l'oublier pas le jour J**

---

## 🎯 MON PROJET (30 secondes)

**Métiers du Numérique - Plateforme d'Orientation BTS**

Appli Laravel qui exploite les données publiques (data.gouv.fr) pour aider 
les élèves à explorer les formations BTS + carrières + salaires. 
Réalisée en 15h lors du hackathon janvier 2026.

---

## ✅ COMPÉTENCES COUVERTES (à cocher)

| # | Compétence | Case | Niveau | Clé |
|----|----------|------|--------|-----|
| 1 | Patrimoine informatique | ☑ | ★★★★★ | BD versionnées + cache + logs |
| 2 | Incidents/assistance | ☑ | ★★★☆☆ | Logs OK, pas chat support |
| 3 | Présence en ligne | ☑ | ★★★★★ | Carte interactive + responsive |
| 4 | Mode projet | ☑ | ★★★★★ | 15h = MVP, Git workflow |
| 5 | Service informatique | ☑ | ★★★☆☆ | Testée localement, pas prod |
| 6 | Développement perso | ☑ | ★★★★★ | Apprentissage complet, bonnes pratiques |

---

## 💾 DESCRIPTION COURTE (à copier-coller)

```
Plateforme Laravel exploitant les APIs publiques data.gouv.fr 
pour l'orientation scolaire vers les BTS du numérique.

Fonctionnalités: Recherche multifiltre, cartographie interactive 
(Leaflet), authentification, dashboard analytics, statistiques 
d'utilisation en base de données.

Architecture MVC complète, cache + fallback, gestion erreurs robuste.
~1200 lignes code. Tests fonctionnels OK. Prête pour démo locale.
```

---

## 🚀 DÉMO (3 minutes)

```
1. Accueil (45s) - URL: http://localhost:8000
   "Voici la page publique avec carte des formations"

2. Recherche (60s) - URL: /formations/recherche (après login)
   "Filtrons par académie... Résultats affichés immédiatement"

3. Dashboard (45s) - URL: /dashboard
   "Historique utilisateur, top formations, analytics"
```

---

## 📁 FICHIERS CLÉS À MONTRER

```
✅ API: app/Services/DataGouvService.php (428 lignes)
✅ Recherche: app/Http/Controllers/FormationSearchController.php
✅ Modèle: app/Models/SearchStat.php (BD + analytics)
✅ BD: database/migrations/2026_01_08_205440_create_search_stats_table.php
```

---

## 🎬 DISCOURS (10 min)

**1. Contexte** (1min)
→ Hackathon 15h, thème APIs publiques, problème orientation BTS

**2. Solution** (1min)
→ Centraliser données + ajouter analytics + cartographie

**3. Architecture** (2min)
→ Laravel, data.gouv.fr, cache, fallback, auth

**4. Démo** (3min)
→ Accueil, recherche, dashboard (voir section DÉMO ci-dessus)

**5. Compétences** (2min)
→ 6 compétences dont 4 "Excellent", 2 "Bon"
→ Points forts: Architecture, code, fonctionnalités
→ Limites: Pas support utilisateurs, pas production

**6. Clôture** (1min)
→ Synthèse apprentissages + prêt pour questions

---

## ❓ TOP 6 QUESTIONS À PRÉVOIR

```
Q1: Pourquoi Laravel?
R: MVC complet, productif, auth intégrée, cache, Eloquent ORM

Q2: Gestion si l'API est down?
R: Cache 24h + fallback données + retry 3x + logs

Q3: Défis rencontrés?
R: Volume données (pagination+cache) et 15h limités (priorisation MVP)

Q4: Comment mesurez-vous le succès?
R: Routes testées ✓, responsive ✓, temps réponse ✓, analytics ✓

Q5: Que feriez-vous différemment?
R: Déploiement prod (AWS), support utilisateurs, tests unitaires, CI/CD

Q6: Pourquoi rémunérations?
R: Orientation holistique: formation + métier + salaire
```

---

## 📸 CAPTURES À PRÉPARER (7 images)

```
1. home.png         → http://localhost:8000/
2. search.png       → http://localhost:8000/formations/recherche
3. results.png      → Résultats de recherche filtrée
4. dashboard.png    → http://localhost:8000/dashboard
5. code_service.png → app/Services/DataGouvService.php
6. code_model.png   → app/Models/SearchStat.php
7. database.png     → PhpMyAdmin (tables search_stats)
```

---

## 🔐 COMMANDES À RETENIR

```bash
# Lancer l'app
php artisan serve

# Voir les logs
tail -f storage/logs/laravel.log

# Voir les branches
git branch -a

# Voir l'historique
git log --oneline | head -20
```

---

## ✅ CHECKLIST JOUR J

- [ ] App lancée localement (php artisan serve)
- [ ] Diaporama prêt (5 slides)
- [ ] Captures d'écran téléchargées
- [ ] Réponses aux Q&A mémorisées
- [ ] Code ouvert dans l'IDE
- [ ] Discours de 10 min préparé
- [ ] Montre avant (accueil), login, recherche, dashboard
- [ ] Démo secs (pas de lag)
- [ ] Questions anticipées résolues
- [ ] Sourire! Vous avez réalisé quelque chose de solide 😊

---

## 💡 POINTS FORTS À INSISTER

✅ **Architecture MVC** solide et maintenable
✅ **Intégration API réelle** (pas de données en dur)
✅ **Sécurité** (authentification, validation, CSRF)
✅ **Performance** (cache, pagination)
✅ **UX/UI** moderne (Tailwind, responsive, Leaflet)
✅ **Code documenté** (docblocks exhaustifs)
✅ **Pensée projet** (15h = MVP = livré)

---

## ⚠️ POINTS À NE PAS EXAGÉRER

❌ "En production" → C'est local seulement
❌ "Parfaitement testé" → Tests manuels, pas unitaires
❌ "Support utilisateurs complet" → Logs + validation seulement
❌ "Scalable à l'infini" → MVP, pas optimisé pour millions d'users

---

## 🎯 CLÉS DU SUCCÈS

1. **Comprendre ce qu'on a fait** (vous pouvez l'expliquer)
2. **Connaître ses limites** (honnêteté = crédibilité)
3. **Montrer le code** (preuve vivante)
4. **Faire la démo** (ça marche → confiance)
5. **Répondre sincèrement** (pas baragouiner)
6. **Relier aux compétences** (jury = checklist compétences)

---

## 📞 EN CAS DE PANIQUE

**L'app crash?**
→ Dire: "Je reboot l'app" (php artisan serve)
→ Montrer le code en attendant

**Oubli discours?**
→ Regarder le diaporama
→ Relire les 5 slides
→ C'est normal d'hésiter (jury le sait)

**Question piégée?**
→ Répondre: "Bonne question, je n'avais pas pensé à ça"
→ Réfléchir 5s avant de répondre
→ Honnêteté > baragouin

**Pas assez de temps?**
→ Sauter la démo, montrer captures
→ Aller à l'essentiel

---

## 🎓 VOTRE FORCE

Vous avez développé une application **VRAIE**, **COMPLÈTE** et **UTILE**.
Ce n'est pas un exercice scolaire artifiel.

C'est ça que le jury veut voir. Donc vous êtes déjà 80% du chemin. ✨

---

**Bonne présentation! 🚀**
