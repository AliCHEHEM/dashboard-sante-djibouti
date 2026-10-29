# 🏥 Dashboard — Infrastructures sanitaires de Djibouti

Dashboard interactif (Python / Plotly) construit à partir du chapitre III de l'analyse *Santé* (cartographie censitaire, RGPH-3) :
niveaux de la pyramide sanitaire, types d'infrastructures, fonctionnement, public/privé, lits et personnel par commune et sous-préfecture, carte.

**▶ Ouvrir dans Google Colab :**
`https://colab.research.google.com/github/VOTRE-UTILISATEUR/dashboard-sante-djibouti/blob/main/dashboard_sante_djibouti.ipynb`

(Badge Markdown : `[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](LIEN-CI-DESSUS)`)

## Structure

```
dashboard-sante-djibouti/
├── dashboard_sante_djibouti.ipynb   # le notebook (dashboard + contrôles qualité + export HTML)
├── data/                            # données tabulaires propres (CSV)
│   ├── niveaux.csv
│   ├── regions.csv                  # coordonnées des chefs-lieux (carte)
│   ├── infra_par_type_region.csv
│   ├── fonctionnalite_region.csv
│   ├── secteur_region.csv
│   ├── raisons_non_fonctionnalite.csv
│   ├── djibouti_ville_communes.csv
│   └── sous_prefectures.csv
├── docs/                            # (optionnel) index.html pour GitHub Pages
├── requirements.txt
└── README.md
```

## Mise en ligne sur GitHub (pas à pas)

1. Créez un dépôt **public** sur github.com, nommé `dashboard-sante-djibouti`.
2. Cliquez sur *Add file → Upload files* et déposez **tout le contenu** de ce dossier (notebook, `data/`, README…), puis *Commit changes*.
3. Dans le notebook, section 1, remplacez `GITHUB_USER` par votre nom d'utilisateur GitHub (modifiez le fichier sur GitHub ou dans Colab, puis *Fichier → Enregistrer une copie dans GitHub*).
4. Dans ce README, remplacez `VOTRE-UTILISATEUR` par votre nom d'utilisateur.
5. Ouvrez le lien Colab ci-dessus → *Exécution → Tout exécuter*.

## Publier le dashboard comme site web (GitHub Pages)

1. Exécutez le notebook jusqu'à la dernière cellule : elle télécharge `dashboard.html`.
2. Renommez-le `index.html` et déposez-le dans un dossier `docs/` du dépôt.
3. *Settings → Pages → Deploy from a branch → main / docs*.
4. Votre dashboard est en ligne sur `https://VOTRE-UTILISATEUR.github.io/dashboard-sante-djibouti/`.

## Mettre à jour les données

Modifiez les CSV dans `data/` (directement sur GitHub, icône crayon) puis relancez le notebook. Aucun code à changer tant que les colonnes gardent leur nom.

## Qualité des données

La section 8 du notebook recalcule les totaux du document et liste les incohérences repérées (niveaux = 188 au lieu de 190, « 54 » fonctionnelles hors capitale au lieu de 65, tableau de pourcentages des communes qui correspond en fait aux parts de lits, etc.). Quatre valeurs tronquées dans le document (`2-`, `5-`, `1-`, `4-`) ont été reconstituées par différence avec les totaux.

## Pistes d'évolution

- Ajouter la population (RGPH-3) pour calculer lits et infirmiers pour 1 000 habitants.
- Version application web avec Streamlit (même données, même graphiques).
- Ajouter les effectifs d'infrastructures par commune de Djibouti-Ville (manquants dans le document).
