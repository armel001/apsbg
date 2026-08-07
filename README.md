# Site APSBG — Annuaire des membres

Site statique [Jekyll](https://jekyllrb.com/), pensé pour être hébergé
gratuitement sur **GitHub Pages**. Il affiche le catalogue des membres de
l'APSBG sous forme de fiches (photo, profession, domaine de compétence,
contact).

## Structure du projet

```
apsbg-site/
├── _config.yml            # réglages du site (titre, description, contact...)
├── _data/
│   └── membres.csv         # >>> LA BASE DE DONNÉES DES MEMBRES <<<
├── _includes/
│   ├── header.html         # bannière + navigation
│   ├── footer.html
│   └── member-card.html    # gabarit d'une fiche membre
├── _layouts/
│   └── default.html        # squelette HTML commun à toutes les pages
├── assets/
│   ├── css/style.css       # tout le style visuel du site
│   └── images/
│       ├── banner.png      # bannière de l'association (déjà en place)
│       ├── favicon.png     # icône d'onglet (déjà en place)
│       └── membres/        # photos des membres (voir README dans ce dossier)
├── index.md                 # page d'accueil
└── membres.md                # page « Catalogue des membres »
```

## 1. Mettre à jour la liste des membres

C'est le seul fichier que vous aurez besoin de modifier régulièrement :
**`_data/membres.csv`**.

Exportez votre fichier Excel au format **CSV (séparateur virgule, encodage
UTF-8)** et remplacez le contenu de `_data/membres.csv` par le vôtre, en
gardant exactement les mêmes noms de colonnes :

| Colonne              | Obligatoire | Exemple                          |
|----------------------|:-----------:|-----------------------------------|
| `id`                  | oui         | `1`, `2`, `3`…                    |
| `nom`                 | oui         | `DOSSOU Fabrice`                  |
| `profession`          | non         | `Médecin` (laisser vide si inconnu) |
| `domaine_competence`  | non         | `Cardiologie`                     |
| `secteur`             | non         | `Secteur public`, `Secteur privé`, `ONG / International`… |
| `ville`               | non         | `Conakry` ou adresse/quartier      |
| `email`               | non         | `f.dossou@example.com`            |
| `telephone`           | non         | `+224 620 00 00 01`               |
| `photo`               | non         | `dossou-fabrice.jpg`              |
| `bio`                 | non         | Courte présentation ou activités complémentaires |

Le champ `nom` accepte le nom complet tel qu'il vous est fourni, dans
l'ordre que vous préférez (« Prénom Nom » ou « NOM Prénom ») — le site
n'essaie pas de deviner lequel est le prénom.

⚠️ Si un champ contient une virgule (par ex. dans une bio), encadrez-le de
guillemets doubles : `"Infirmier, spécialisé en soins intensifs."`

Les 17 membres actuellement dans `_data/membres.csv` sont vos données
réelles (import du 07/08/2026). Pour toute mise à jour ultérieure —
nouveau membre, correction —, modifiez directement ce fichier en
respectant le même format de colonnes.

> Note : le fichier source contenait un doublon (une même personne,
> même numéro de téléphone, soumise deux fois) — il a été retiré
> automatiquement lors de l'import.

## 2. Ajouter les photos (facultatif)

Voir `assets/images/membres/README.md`. Un membre sans photo affiche
automatiquement un avatar avec ses initiales — ce n'est pas bloquant.

## 3. Personnaliser les textes

- `_config.yml` : titre, description, e-mail de contact affiché en pied de
  page.
- `index.md` : texte de présentation de l'association sur la page d'accueil
  (actuellement un texte générique à adapter).

## 4. Tester le site en local (facultatif)

Il faut avoir Ruby installé, puis :

```bash
bundle install
bundle exec jekyll serve
```

Le site est alors visible sur `http://localhost:4000`.

## 5. Publier sur GitHub Pages

1. Créez un dépôt sur GitHub (par exemple `apsbg` ou `apsbg-guinee`) et
   poussez-y tout le contenu de ce dossier :

   ```bash
   git init
   git add .
   git commit -m "Site initial APSBG"
   git branch -M main
   git remote add origin https://github.com/<votre-compte>/<nom-du-depot>.git
   git push -u origin main
   ```

2. Dans GitHub : **Settings → Pages → Build and deployment → Source :
   Deploy from a branch**, puis choisissez la branche `main` et le dossier
   `/ (root)`. Enregistrez.

3. Vérifiez/ajustez `baseurl` dans `_config.yml` :
   - Dépôt nommé `<votre-compte>.github.io` → `baseurl: ""`
   - Tout autre nom de dépôt (ex. `apsbg`) → `baseurl: "/apsbg"`

4. Après 1-2 minutes, le site est accessible à l'adresse indiquée dans
   l'onglet **Pages** de votre dépôt (généralement
   `https://<votre-compte>.github.io/<nom-du-depot>/`).

Chaque fois que vous modifiez `_data/membres.csv` (ou tout autre fichier)
et que vous poussez (`git push`), GitHub Pages reconstruit le site
automatiquement — aucune action supplémentaire n'est nécessaire.

## Pistes d'évolution (non incluses dans cette v1)

- Barre de recherche / filtre par domaine de compétence
- Page individuelle détaillée par membre
- Carte de Guinée avec localisation des membres

Ces options avaient été évoquées puis écartées pour cette première version
au profit d'un catalogue simple ; elles peuvent être ajoutées plus tard si
besoin.
