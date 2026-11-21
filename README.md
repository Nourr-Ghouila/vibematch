# 🎧 VibeMatch

VibeMatch is a hybrid music recommendation system I'm building as my final project for the GOMYCODE Data Scientist program.

It started from a simple frustration: with millions of songs available, I keep going back to the same artists, and generic playlists like "Top 50" are the same for everyone. They don't know what I like, and they don't know my mood. With VibeMatch, I want to find songs that match my vibe: ones that sound like a track I love, that people with similar taste enjoy, or that fit how I feel right now, even on my very first visit.

> Project in progress.

## Features

- **More like this**: pick a song and get tracks with a similar sound, even from different artists
- **For you**: personalized recommendations learned from the listening habits of people with similar taste
- **Instant start**: new users choose three songs or genres they like and get recommendations right away, with no listening history needed
- **Mood search**: describe what you want in plain French or English ("something calm to study late at night") and get matching songs
- **Mood playlists**: automatic playlists such as "Acoustic chill", "Energy" or "Party"
- **Genre detection**: upload an MP3, VibeMatch listens to it, predicts its genre with a confidence score and suggests similar songs from the catalog
- **Variety slider**: choose the balance between familiar picks and new discoveries
- **Explanations and feedback**: every recommendation says why it was suggested, and likes and dislikes refine the next ones
- **Insights**: charts on genres, moods and a century of musical trends

## My approach

I chose a hybrid approach because each recommendation method makes up for the weaknesses of the others:

- **Audio similarity**: each song is described by its audio features (energy, positivity, danceability, acousticness, tempo…). I compare them with cosine similarity, which works even for a brand-new user with no history.
- **Collaborative filtering**: I use real listening histories and an ALS matrix factorization model to learn hidden tastes shared by listeners. This is what brings surprise and discovery beyond songs that simply sound alike.
- **Natural language mood search**: I turn song descriptions and user requests into vectors with Sentence-BERT, so the search understands the meaning of a sentence rather than matching keywords ("revise" can find "study").
- **Genre detection with deep learning**: I convert audio into mel-spectrograms and train a CNN on them, then compare it with a fine-tuned pre-trained model.

The results are combined into one final list, then re-ranked to keep it varied and avoid recommending only the most popular songs. I evaluate each model against simple baselines (most popular songs and random picks) to check that it actually adds value.

## Getting started

```bash
git clone https://github.com/Nourr-Ghouila/vibematch.git
cd vibematch

python -m venv .venv
.venv\Scripts\activate          # Windows
# source .venv/bin/activate     # macOS / Linux

pip install -r requirements.txt
```

The main catalog comes from the [Spotify Dataset on Kaggle](https://www.kaggle.com/datasets/vatsalmavani/spotify-dataset). The CSV files go in `data/raw/Spotify/`.

```bash
python src/train.py             # trains and saves the models
streamlit run app/app.py        # launches the app
```

## Tech stack

- **Data**: pandas, NumPy, SQLite
- **Machine learning**: scikit-learn (cosine similarity, K-Means), implicit (ALS)
- **Deep learning**: PyTorch, librosa (mel-spectrograms, CNN, transfer learning)
- **NLP**: sentence-transformers, FAISS
- **Visualization**: Matplotlib, Seaborn, Plotly, Tableau Public
- **App**: Streamlit

## Project structure

```
vibematch/
├── app/            Streamlit app
├── src/            data loading, preparation, recommendation engine
├── notebooks/      my exploration and modeling choices
├── models/         trained models
├── data/           raw and processed data
└── requirements.txt
```

---

Nour Ghouila · Data Scientist in training, GOMYCODE
