# 🎧 VibeMatch

**Système de recommandation musicale basé sur les caractéristiques audio de Spotify.**

Projet de fin de formation **GOMYCODE — Data Scientist**.

---

## Le projet

Quand on aime un morceau, on cherche souvent d'autres titres qui ont la même « vibe » : la même énergie, la même ambiance, le même rythme. VibeMatch répond à ce besoin. À partir d'un morceau choisi, l'application recommande des titres au profil sonore proche.

L'approche est une **recommandation basée sur le contenu** : chaque morceau est décrit par ses caractéristiques audio (dansabilité, énergie, valence, acoustique, tempo…). Je regroupe les morceaux similaires par **clustering**, puis je recommande les plus proches à l'aide d'une **mesure de similarité**.

## Les données

J'utilise le dataset **Spotify 1921-2020** disponible sur Kaggle :
👉 [Spotify Dataset (Kaggle)](https://www.kaggle.com/datasets/vatsalmavani/spotify-dataset)

| Fichier | Contenu | Taille |
|---|---|---|
| `data.csv` | Un morceau par ligne, avec ses caractéristiques audio | 170 653 morceaux |
| `data_by_genres.csv` | Moyennes des caractéristiques par genre | 2 973 genres |
| `data_by_artist.csv` | Moyennes des caractéristiques par artiste | 28 680 artistes |
| `data_by_year.csv` | Moyennes des caractéristiques par année | 100 années |

Les fichiers sont trop volumineux pour GitHub. Pour reproduire le projet, il faut les télécharger et les placer dans `data/raw/Spotify/`.

## Démarche

| Étape | Notebook | Statut |
|---|---|---|
| 1. Chargement et découverte des données | `01_data_loading.ipynb` | ✅ Terminé |
| 2. Analyse exploratoire (évolution par décennie, genres, corrélations) | `02_eda.ipynb` | ⏳ À venir |
| 3. Clustering des morceaux et des genres (KMeans, PCA) | `03_clustering.ipynb` | ⏳ À venir |
| 4. Moteur de recommandation (similarité cosinus) | `04_recommendation.ipynb` | ⏳ À venir |
| 5. Application web interactive | `app/` (Streamlit) | ⏳ À venir |

## Premiers constats

- Les données sont complètes : aucune valeur manquante et aucun doublon.
- Les variables numériques sont sur des échelles très différentes (`tempo`, `loudness`, `duration_ms`), une normalisation est nécessaire avant le clustering.
- Le dataset est plafonné à environ 2 000 morceaux par an. Les volumes par décennie ne reflètent donc pas la production musicale réelle.

## Structure du projet

```
VibeMatch/
├── data/
│   ├── raw/          # Données d'origine (non versionnées)
│   └── processed/    # Données transformées
├── notebooks/        # Exploration et modélisation, dans l'ordre
├── src/              # Code Python réutilisable (chargement, features, recommandation)
├── models/           # Modèles entraînés (non versionnés)
├── app/              # Application Streamlit
└── requirements.txt
```

## Installation

```bash
git clone https://github.com/Nourr-Ghouila/vibematch.git
cd vibematch

python -m venv .venv
.venv\Scripts\activate        # Windows
# source .venv/bin/activate   # macOS / Linux

pip install -r requirements.txt
```

Ensuite, je place les fichiers du dataset dans `data/raw/Spotify/` et je lance Jupyter :

```bash
jupyter notebook notebooks/
```

## Outils

Python · pandas · NumPy · Matplotlib · Seaborn · Plotly · scikit-learn · Streamlit

## Contact

**Nour Ghouila** — Data Scientist en formation (GOMYCODE)
GitHub : [@Nourr-Ghouila](https://github.com/Nourr-Ghouila)
