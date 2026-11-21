# 🎧 VibeMatch

VibeMatch est un système de recommandation musicale que je développe dans le cadre de mon projet de fin de formation Data Scientist chez GOMYCODE.

L'idée m'est venue d'une situation simple : quand j'aime un morceau, j'ai envie d'en trouver d'autres qui ont la même ambiance, la même énergie, le même rythme. Avec VibeMatch, je choisis un titre et l'application me propose les morceaux dont le profil sonore est le plus proche, parmi plus de 170 000 titres sortis entre 1921 et 2020.

> Projet en cours de développement.

## Fonctionnalités

- **Recherche d'un morceau** par titre ou par artiste
- **Recommandations** des morceaux les plus proches, avec leur score de similarité
- **Profil audio** du morceau choisi, comparé à ceux des recommandations
- **Carte des vibes** : visualisation des groupes de morceaux aux ambiances proches
- **Exploration** de l'évolution de la musique au fil des décennies

## Mon approche

J'ai choisi une recommandation basée sur le contenu. Chaque morceau est décrit par une dizaine de caractéristiques audio (dansabilité, énergie, humeur, acoustique, tempo…). Je les normalise, puis je regroupe les morceaux par ambiance avec KMeans. Pour un titre donné, je cherche ensuite les morceaux les plus proches avec la similarité cosinus.

Ce choix me permet de ne dépendre que du son des morceaux, sans historique d'écoute. VibeMatch peut donc recommander un titre peu connu dès lors qu'il a la bonne vibe.

## Lancer le projet

```bash
git clone https://github.com/Nourr-Ghouila/vibematch.git
cd vibematch

python -m venv .venv
.venv\Scripts\activate          # Windows
# source .venv/bin/activate     # macOS / Linux

pip install -r requirements.txt
```

J'utilise le [Spotify Dataset disponible sur Kaggle](https://www.kaggle.com/datasets/vatsalmavani/spotify-dataset). Les fichiers CSV sont à placer dans `data/raw/Spotify/`.

```bash
python src/train.py             # entraîne et sauvegarde les modèles
streamlit run app/app.py        # lance l'application
```

## Stack technique

- **Données** : pandas, NumPy
- **Machine learning** : scikit-learn (KMeans, PCA, similarité cosinus)
- **Visualisation** : Matplotlib, Seaborn, Plotly
- **Application** : Streamlit

## Structure

```
vibematch/
├── app/            application Streamlit
├── src/            chargement des données, préparation, moteur de recommandation
├── notebooks/      mon exploration et mes choix de modélisation
├── models/         modèles entraînés
├── data/           données brutes et transformées
└── requirements.txt
```

---

Nour Ghouila · Data Scientist en formation, GOMYCODE
