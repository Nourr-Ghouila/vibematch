# VibeMatch

VibeMatch recommande des morceaux qui ont la même vibe que celui que vous aimez.

Choisissez un titre, VibeMatch analyse son profil sonore (énergie, dansabilité, humeur, acoustique, tempo…) et propose les morceaux qui lui ressemblent le plus, parmi plus de 170 000 titres sortis entre 1921 et 2020.

> Projet en cours de développement.

## Fonctionnalités

- **Recherche d'un morceau** par titre ou par artiste
- **Recommandations personnalisées** : les morceaux les plus proches, avec leur score de similarité
- **Profil audio** du morceau choisi, comparé à ceux des recommandations
- **Carte des vibes** : visualisation des groupes de morceaux aux ambiances proches
- **Exploration** de l'évolution de la musique au fil des décennies

## Comment ça marche

Chaque morceau est décrit par une dizaine de caractéristiques audio. Après normalisation, les morceaux sont regroupés par ambiance avec un algorithme de clustering (KMeans). Pour un titre donné, VibeMatch recherche ensuite les morceaux les plus proches avec la similarité cosinus.

Les recommandations reposent uniquement sur le son des morceaux, pas sur l'historique d'écoute des utilisateurs. VibeMatch peut donc recommander un titre peu connu dès lors qu'il a la bonne vibe.

## Lancer le projet

```bash
git clone https://github.com/Nourr-Ghouila/vibematch.git
cd vibematch

python -m venv .venv
.venv\Scripts\activate          # Windows
# source .venv/bin/activate     # macOS / Linux

pip install -r requirements.txt
```

Les données proviennent du [Spotify Dataset sur Kaggle](https://www.kaggle.com/datasets/vatsalmavani/spotify-dataset). Les fichiers CSV sont à placer dans `data/raw/Spotify/`.

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
├── notebooks/      exploration et choix de modélisation
├── models/         modèles entraînés
├── data/           données brutes et transformées
└── requirements.txt
```

---

Nour Ghouila · Projet de fin de formation Data Scientist, GOMYCODE
