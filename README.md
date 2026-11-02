# Site DMB & CO — dmb-renovation.fr

Site vitrine de **DMB & CO** (Marie Favier, architecte d'intérieur & décoratrice · Alexandre Favier, maître d'œuvre), 23 rue des Pins Francs, 33210 Toulenne. Rénovation, extension, architecture d'intérieur à Langon et dans le Sud-Gironde.

Ce dossier est **le site complet, prêt à être servi tel quel** : du HTML, du CSS et un peu de JavaScript dans chaque page, plus les photos dans `img/`. Aucun outil à installer, aucune base de données, aucun CMS. On l'ouvre dans un navigateur, on l'édite dans n'importe quel éditeur de texte (ou avec ChatGPT / Claude), on le pousse sur GitHub et il est en ligne.

---

## 1. Hébergement et mise en ligne

| Élément | Valeur |
|---|---|
| Dépôt GitHub (source = ce dossier) | `github.com/cobalio/dmb-renovation`, branche `main` |
| Hébergement | **GitHub Pages** (gratuit), servi depuis la racine de `main` |
| Domaine | `dmb-renovation.fr` (fichier `CNAME`), registrar **OVH** |
| DNS à avoir chez OVH | `@` A → 185.199.108.153 / 185.199.109.153 / 185.199.110.153 / 185.199.111.153 · `www` CNAME → `cobalio.github.io.` |
| Ancien hébergeur | Squarespace (dmb-renovation.fr) et dmbandco.fr — les textes et photos en viennent |

**Publier une modification** : modifier le fichier, `git commit`, `git push origin main` (ou « Commit changes » directement dans l'interface GitHub). GitHub Pages redéploie en 1 à 2 minutes. Pas de build, pas de compilation.

Fichiers à **ne pas supprimer** : `CNAME` (le domaine), `.nojekyll`, `robots.txt`, `sitemap.xml`, `404.html`, `favicon.ico`.

---

## 2. Arborescence (29 pages)

Chaque page est un dossier contenant un `index.html` → URL propre sans extension.

```
/                                   Accueil
/prestations/                       Nos métiers (liste)
/prestations/renovation-maison/     + renovation-salle-de-bain, renovation-cuisine, extension-maison,
                                      amenagement-exterieur, pool-house, espace-professionnel,
                                      maitrise-oeuvre, architecture-interieur, decoration-interieur,
                                      relooking-home-staging, autorisation-urbanisme,
                                      visite-conseil-avant-achat, chambre-amis-dortoir   (14 métiers)
/realisations/                      Galerie des chantiers (avant / après, légendes de Marie)
/secteur/                           Sud-Gironde (liste des communes)
/secteur/toulenne/  /langon/  /coimeres/   Pages villes = 1 page par ville où il y a de vrais chantiers
/notre-equipe/                      Marie & Alexandre
/faq/                               Questions fréquentes (textes de Marie)
/simulateur/                        « Estimation gratuite » : questionnaire en 7 étapes
/contact/                           Contact (reprend le questionnaire)
/mentions-legales/  /politique-de-confidentialite/
/home/                              simple redirection vers / (ancienne URL Squarespace)
img/                                62 photos, nommées pour le SEO (voir §4)
sitemap.xml  robots.txt  404.html  CNAME  favicon.ico
```

**Règle d'or** : ne pas créer de pages « villes » en série avec les mêmes photos. Une page ville n'existe que s'il y a un vrai chantier à y montrer.

---

## 3. Charte graphique (identique sur toutes les pages)

Les couleurs sont des variables CSS déclarées en haut de chaque page dans `:root` ; les réutiliser plutôt que des codes en dur.

| Variable | Valeur | Usage |
|---|---|---|
| `--forest` | `#1F3328` (foncé) / `--fill` `#3A5C48` | vert DMB : boutons, pied de page, encarts |
| `--sage` / `--sage-2` | `#84B598` / vert clair | accents, badges, fonds doux |
| `--bg` | `#F6F2EC` | fond crème des pages |
| `--ink` / `--ink-2` | `#2C2C2C` / gris chaud | texte |
| `--line` | `#DED6CB` | bordures, filets |
| `--label` | `#4F7560` | petits libellés en capitales espacées |

- **Polices** (Google Fonts, chargées dans `<head>`) : **Crimson Pro** (titres, serif) et **Urbanist** (texte, sans-serif).
- **Logo** : SVG inline « DMB & CO. » dans l'en-tête et le pied de page (texte vectorisé, pas d'image).
- **Icônes** : petit pack SVG en traits fins (home, hammer, plan, palette, wallet, ruler, users, check, bed, sun, leaf, key, briefcase, star, eye…), copié-collé dans les pages. Pour une nouvelle icône, rester dans ce style : 24×24, `fill:none`, trait 1.6, bouts arrondis.
- **Composants** : boutons `.btn .btn-primary` (vert plein) / `.btn-ghost`, cartes `.card`, sections `.section` et `.section.band` (bandeau beige), bloc d'appel à l'action vert en bas de page, fil d'Ariane, FAQ en `<details>`.
- Arrondis généreux (16–26 px), beaucoup d'air, photos en grand.

---

## 4. Photos

- Toutes dans `img/`, **uniquement de vraies photos des chantiers DMB** (récupérées des sites Squarespace). Pas d'image générée par IA, pas de banque d'images.
- Nom de fichier = description SEO en minuscules, mots séparés par des tirets, avec la ville quand on la connaît :
  `renovation-salle-de-bain-beton-cire-bois-toulenne.jpg`, `construction-pool-house-apres-travaux-sud-gironde.webp`, `marie-favier-architecte-interieur-langon.jpg`.
- Formats : `.webp` (léger) ou `.jpg`. Viser < 300 Ko, largeur 1600–2500 px. Toujours remplir l'attribut `alt` en français, descriptif (« Douche à l'italienne en béton ciré, rénovation de salle de bain à Toulenne »), et `width`/`height` + `loading="lazy"` sauf pour l'image du haut de page.
- Image de partage (Open Graph) : `img/dmb-and-co-renovation-langon-partage.jpg` (1200×630).

**Ajouter une photo à une réalisation** : déposer le fichier dans `img/`, puis dupliquer un bloc `<figure>` existant dans `realisations/index.html` (et/ou la page métier concernée) en changeant `src`, `alt` et la légende.

---

## 5. Textes et SEO

- Les textes sont **ceux de Marie** (repris mot pour mot de Squarespace : accueil, prestations, formules d'architecture d'intérieur, FAQ, légendes). Garder ce ton : « nous », direct, concret, Sud-Gironde.
- **Décision en vigueur : aucun prix affiché sur le site** (ni dans la FAQ, ni dans les prestations, ni dans le simulateur). Les tarifs sont donnés de vive voix après une première estimation.
- Chaque page a : un `<title>` unique (≈ 60 caractères, finit par « | DMB & CO »), une `<meta name="description">` (≈ 150 caractères), une seule balise `<h1>`, une balise `canonical` (`https://dmb-renovation.fr/…/`), les balises Open Graph / Twitter, et des **données structurées JSON-LD** (`GeneralContractor` pour l'entreprise, `Service` pour un métier, `BreadcrumbList`, `FAQPage` quand il y a une FAQ, `AggregateRating` sur l'accueil).
- Fiches Google Business liées (pied de page + JSON-LD `sameAs`) : Marie (5,0 · 21 avis) et Alexandre (5,0 · 7 avis).
- **Nouvelle page** : copier le dossier d'une page du même type (par ex. `prestations/pool-house/`), renommer le dossier (slug en minuscules avec tirets), adapter title / description / h1 / canonical / JSON-LD / fil d'Ariane / textes / photos, puis **ajouter l'URL dans `sitemap.xml`** et un lien depuis la page liste (`prestations/index.html` ou `secteur/index.html`) et le pied de page si pertinent.

---

## 6. Le simulateur d'estimation (`/simulateur/`, aussi sur l'accueil et `/contact/`)

Questionnaire en 7 étapes, une question par écran, barre de progression :

1. Projet : Rénovation complète / Rénovation partielle / Extension / Architecture d'intérieur
2. Budget envisagé : < 10 k€ · 10–39 k€ · 40–59 k€ · 60–99 k€ · 100–200 k€ · > 200 k€
3. Surface (curseur)
4. Pièces concernées et nombre (chambre, salon, cuisine, salle de bain, WC, bureau, entrée, extérieur, autre)
5. Accompagnement d'une architecte d'intérieur pour la conception : oui / non / je ne sais pas
6. Accompagnement et suivi de chantier : oui / non / je ne sais pas
7. Coordonnées « pour obtenir votre estimation personnalisée »

Le visiteur **ne voit aucun montant**. Une fourchette est calculée en coulisse (barème interne : €/m² par type de projet, forfaits par pièce, +8 à 15 % de maîtrise d'œuvre si suivi, +80 €/m² de conception si architecte) et **envoyée avec toutes les réponses par e-mail à contact@dmbandco.fr** (relais FormSubmit, `https://formsubmit.co/ajax/contact@dmbandco.fr`, variable `ENDPOINT` dans le `<script>` en bas des trois pages). L'e-mail arrive sous forme de tableau, le « Répondre à » est l'adresse du visiteur, et le visiteur reçoit un accusé de réception automatique.

- **Activation (une seule fois)** : au tout premier envoi, FormSubmit adresse à contact@dmbandco.fr un e-mail « Activate form » : cliquer le bouton. Tant que ce n'est pas fait, les demandes sont retenues ; ensuite elles arrivent instantanément. Pour changer l'adresse de réception, remplacer l'e-mail dans `ENDPOINT` (dans les trois pages) et refaire l'activation.
- En cas d'indisponibilité du relais, la page affiche un lien « envoyer par e-mail » pré-rempli et le téléphone d'Alexandre.
- Option prévue mais non activée : envoi parallèle vers ArtiMano (vitrine `dmb-and-co`, compte contact@dmbandco.fr) via `https://artimano.fr/api/public/vitrine/dmb-and-co/demande` une fois cet endpoint déployé.

Le barème et les libellés des questions sont dans la variable `D` du même script : modifier là, dans les trois pages à l'identique (`simulateur/index.html`, `index.html`, `contact/index.html`).

Anti-spam : champ caché « Site web » (pot de miel), limite de 5 envois / 10 minutes / adresse IP côté ArtiMano, case de consentement obligatoire.

---

## 7. Travailler avec ChatGPT ou Claude sur ce site

Donner à l'assistant ce README **et** le fichier HTML de la page concernée (ou la page la plus proche quand on en crée une). Exemples de demandes qui marchent bien :

- « Voici `prestations/pool-house/index.html`. Crée `prestations/renovation-combles/index.html` sur le même modèle, même charte, pour la rénovation et l'aménagement de combles à Langon. Titre, description, h1, canonical, JSON-LD, fil d'Ariane, FAQ de 3 questions sans prix, et dis-moi la ligne à ajouter dans `sitemap.xml`. »
- « Réécris la section "Pourquoi un architecte d'intérieur" avec mon ton (je te colle mes notes), sans toucher au HTML autour. »
- « Propose 6 noms de fichiers SEO et 6 textes `alt` pour ces photos de chantier (je te décris chaque photo, ville : Coimères). »
- « Vérifie que cette page respecte la charte : variables CSS, polices Crimson Pro / Urbanist, une seule h1, pas de prix, images avec alt / width / height / lazy. »
- « Ajoute une étape au simulateur ("Type de bien : maison / appartement") entre la surface et les pièces, dans la variable `D` et dans `flow()`, puis donne-moi le même patch pour les 3 pages. »

À rappeler à l'assistant si besoin : **pas d'images générées par IA**, **pas de prix affichés**, **pas de nouvelles pages villes sans vrai chantier**, garder les URL existantes (le SEO est dessus).

---

## 8. Contacts techniques

- Site, hébergement GitHub, simulateur, ArtiMano : Julien Marchal — hello@cobalio.com
- Domaine (OVH) : compte DMB & CO
- Mentions légales : DMB & CO, SAS au capital de 1 000 €, RCS 13093822800017, TVA FR04130938228
