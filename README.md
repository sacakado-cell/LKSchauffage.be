# LKS Chauffage & Sanitaire — Site web

Site vitrine de **LKS Chauffage et Sanitaire** (Anaël Lieckens), chauffagiste à Ciney,
Province de Namur. Installation, entretien et dépannage de chaudières, sanitaire, VMC
et climatisation.

## Structure

Site statique en HTML/CSS (pas de build, pas de dépendances). Chaque page est
autonome : le CSS est inclus dans le `<style>` de la page et les images/logos sont
soit des fichiers `.jpg`, soit du base64 inline.

| Fichier | Page |
|---|---|
| `index.html` | Accueil |
| `chauffage.html` | Chauffage |
| `salle-de-bain.html` | Salle de bain |
| `depannage.html` | Dépannage |
| `realisations.html` | Réalisations |
| `marques.html` | Garanties & Qualité |
| `conseils.html` | Conseils |
| `avis.html` | Avis clients |
| `qui-suis-je.html` | Qui suis-je |
| `contact.html` | Contact |
| `services.html` | Services (page complémentaire) |

Fichiers annexes : `robots.txt`, `sitemap.xml`, images `real-photo-*.jpg`,
images Open Graph `og-image.jpg` / `og-image-square.jpg`.

> `lks-chauffage-site.html` est une ancienne version conservée à titre d'archive.
> Elle n'est pas liée depuis la navigation et peut être supprimée si elle n'est plus utile.

## Mise en ligne (GitHub Pages)

1. Pousser ce dossier sur un dépôt GitHub.
2. Dans **Settings → Pages**, choisir la branche `main` et le dossier racine `/`.
3. La page d'accueil servie sera `index.html`.

Pour un test en local, ouvrir simplement `index.html` dans un navigateur, ou lancer
un petit serveur :

```bash
python3 -m http.server 8000
# puis ouvrir http://localhost:8000
```

## Correctif mobile (mai 2026)

Toutes les pages internes contenaient une accolade `}` orpheline dans leur `<style>`,
ce qui désynchronisait le parseur CSS et empêchait le footer de se replier sur mobile.
Conséquence : la page débordait horizontalement et, la barre de navigation étant en
`position: fixed`, le bouton hamburger se retrouvait hors de l'écran à droite.

Correction appliquée :

- Suppression de l'accolade `}` superflue dans chaque page concernée.
- `qui-suis-je.html` : ajout d'une media query repliant ses grilles 2 colonnes
  (définies en style *inline*) en 1 colonne sur petit écran.

Vérifié sans débordement horizontal et hamburger visible aux largeurs
320 / 360 / 768 / 1200 px.
