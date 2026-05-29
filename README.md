# LKS Chauffage & Sanitaire — Site web

Site vitrine de **LKS Chauffage et Sanitaire** (Anaël Lieckens), chauffagiste à Ciney,
Province de Namur. Installation, entretien et dépannage de chaudières, sanitaire, VMC
et climatisation.

Domaine de référence : **https://lkschauffage.be** (sans tiret).

## Structure

Site statique HTML/CSS, sans build ni dépendances. Chaque page est autonome (CSS inclus
dans son `<style>`).

| Fichier | Page |
|---|---|
| `index.html` | Accueil |
| `services.html` | Services (aperçu) |
| `chauffage.html` | Chauffage |
| `salle-de-bain.html` | Salle de bain |
| `depannage.html` | Dépannage |
| `realisations.html` | Réalisations |
| `marques.html` | Garanties & Qualité |
| `conseils.html` | Conseils |
| `qui-suis-je.html` | Qui suis-je |
| `avis.html` | Avis clients |
| `contact.html` | Contact |

Annexes : `robots.txt`, `sitemap.xml`, images `real-photo-*.jpg`, `og-image*.jpg`, et le dossier `assets/` (logos de marques + logo du site en WebP).

## Mise en ligne (GitHub Pages)

1. Pousser ce dossier sur un dépôt GitHub.
2. Settings → Pages → branche `main`, dossier racine `/`.
3. Page servie : `index.html`.

Test local : `python3 -m http.server 8000` puis http://localhost:8000

## Historique des corrections (mai 2026)

- **Bug hamburger / débordement mobile** : suppression d'une accolade `}` orpheline dans
  le CSS de chaque page interne (empêchait le footer de se replier → débordement horizontal).
- **Page Marques** : grille des agréments passée en 3 colonnes symétriques (2 puis 1 en mobile).
- **Audit SEO/technique** :
  - Domaine unifié sur `lkschauffage.be` partout (canonical, robots, sitemap).
  - `sitemap.xml` refait avec les 11 vraies URLs (au lieu d'ancres internes).
  - Suppression de la page dupliquée `lks-chauffage-site.html`.
  - Menu unifié sur toutes les pages + ajout des pages « Services » et « Qui suis-je »
    (menu horizontal ≥1281px, hamburger en dessous).
  - Données structurées `LocalBusiness` ajoutées sur Contact et Avis (+ avis réels balisés).
  - Gabarit Google Analytics 4 installé (à activer, voir `GUIDE-SEO.md`).
  - Garde-fou `overflow-x:hidden` contre tout débordement horizontal résiduel.
  - **Allègement des images** : les ~70 logos de `marques.html` (encodés en base64, 1,9 Mo)
    ont été dédupliqués et convertis en WebP dans `assets/` ; le logo du site est désormais
    un fichier WebP partagé (mis en cache sur toutes les pages). `marques.html` passe de
    **1,9 Mo à ~95 Ko**, et chaque autre page perd aussi le logo de 45 Ko qui était inline.

Tests automatisés : 0 débordement horizontal et navigation correcte sur 11 pages × 9 largeurs (320 → 1920 px).

## À faire (hors code)

Voir **`GUIDE-SEO.md`** : activer Analytics, Search Console, fiche Google Business,
collecte d'avis, allègement des images de `marques.html`, email professionnel.
