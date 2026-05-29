# Guide SEO & actions à faire — LKS Chauffage

Ce guide couvre les actions **hors code** (à faire dans des outils externes) qui complètent les corrections déjà appliquées au site. Classées par impact.

---

## 1. Activer Google Analytics 4 (mesurer le trafic)

Le code de suivi est **déjà installé** sur toutes les pages, mais inactif tant que l'identifiant n'est pas renseigné.

1. Allez sur https://analytics.google.com → créez un compte + une « propriété » pour lkschauffage.be.
2. Récupérez votre **ID de mesure**, de la forme `G-XXXXXXXXXX`.
3. Dans tous les fichiers `.html`, remplacez les deux occurrences de `G-XXXXXXXXXX` par votre vrai ID.
   (Un simple « Rechercher / Remplacer dans tous les fichiers » de votre éditeur suffit.)
4. Remettez les fichiers en ligne. Le suivi démarre sous 24 h.

## 2. Google Search Console (le plus important pour le référencement)

C'est l'outil qui dit à Google « voici mon site, indexe-le ».

1. Allez sur https://search.google.com/search-console → ajoutez la propriété `lkschauffage.be`.
2. Validez la propriété (par enregistrement DNS chez votre hébergeur, ou via le fichier de vérification fourni).
3. Menu **Sitemaps** → soumettez : `https://lkschauffage.be/sitemap.xml`
   (le sitemap a été refait avec les 11 vraies pages).
4. Surveillez l'onglet **Indexation** pour vérifier que toutes les pages sont prises en compte.

## 3. Fiche Google Business Profile (levier n°1 pour un artisan local)

Pour « chauffagiste Ciney » et requêtes locales, la fiche Google pèse souvent **plus** que le site.

- Créez/revendiquez la fiche sur https://business.google.com
- Renseignez : nom exact (LKS Chauffage et Sanitaire), adresse, téléphone `0477/190.570`, horaires (Lun–Ven 07h30–18h00), zone desservie (50 km autour de Ciney), catégories (« Chauffagiste », « Plombier »).
- Ajoutez des **photos** de chantiers (les mêmes que la page Réalisations).
- Publiez régulièrement (offres, conseils saisonniers).

> Important : les coordonnées (Nom, Adresse, Téléphone) doivent être **strictement identiques** entre le site et la fiche Google. Le site utilise : 102 rue de Monin, 5362 Achet — +32 477 19 05 70.

## 4. Collecte d'avis Google

Les avis sont décisifs pour la conversion locale. Vous avez 3 avis 5★ — visez-en plus.

- Après chaque chantier, envoyez le lien direct d'avis Google au client.
- Objectif réaliste : 1–2 avis/mois. À 15–20 avis, l'effet sur le classement local est net.
- Quand le nombre d'avis augmente, pensez à mettre à jour `reviewCount` dans les données structurées (voir §7 ci-dessous).

## 5. Alléger les images (vitesse = référencement)

La page `marques.html` contient encore les logos de marques **encodés dans le HTML** (base64). C'est le principal point de lenteur restant.

- Exportez chaque logo en fichier `.webp` séparé (ou `.png` optimisé).
- Remplacez les `src="data:image/...."` par `src="logos/nom-marque.webp"`.
- Ajoutez `loading="lazy"` sur ces images.
- Cible : faire passer `marques.html` de ~1,9 Mo à moins de 200 Ko.
- Outils : https://squoosh.app (gratuit) pour convertir/compresser.

## 6. Email professionnel (confiance)

Remplacer `lkschauffage@gmail.com` par `contact@lkschauffage.be` renforce l'image pro.
La plupart des hébergeurs de domaine fournissent une boîte mail incluse.

## 7. Maintenir les données structurées à jour

Des données `LocalBusiness` ont été ajoutées sur l'accueil, Contact et Avis ; la page Avis liste les 3 avis réels avec leur note. Quand vous ajoutez/retirez un avis **affiché sur la page**, mettez à jour en parallèle le bloc `<script type="application/ld+json">` correspondant (champ `reviewCount` et liste `review`), pour que le balisage reste fidèle à ce qui est visible.

Vérifiez vos données structurées ici : https://search.google.com/test/rich-results

---

## Idées d'amélioration (moyen terme)

- **Pages locales ciblées** : créer des pages/sections « Chauffagiste Dinant », « Dépannage chaudière Rochefort », etc., pour capter les communes voisines.
- **Bandeau urgence** permanent en haut : « Dépannage urgent ? ☎ 0477/190.570 » — capte le trafic à forte intention.
- **Page de remerciement** après envoi du formulaire (utile pour mesurer les conversions dans GA4).
- **Avant/après** en photos sur la page Réalisations (très convaincant pour ce métier).
