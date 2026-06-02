# Movie Recommender System with Word2Vec

---

## Overview

Movies that users watch together behave like words in a sentence.  
This project trains a **Word2Vec** model on MovieLens watch histories to learn movie embeddings — then uses cosine similarity to recommend similar movies.

---

## Dataset

**MovieLens 20M** — [Kaggle](https://www.kaggle.com/datasets/grouplens/movielens-20m-dataset)

| | |
|--|--|
| Ratings | 20,000,263 |
| Movies | 27,278 |
| Users | 138,493 |
| Period | 1995 – 2015 |

Files used: `rating.csv`, `movie.csv`

---

## How It Works

Each user's watch history = one **"sentence"**  
Each movie = one **"word"**

Word2Vec learns that movies frequently watched together end up close in embedding space.

```
User 42 watched: [Inception, The Matrix, Interstellar, Memento, ...]
                       ↓
         Word2Vec treats this as a sentence
                       ↓
  similar movies end up close in 128-dimensional space
```

---

## Notebook Structure

| Section | Description |
|---------|-------------|
| 1. Load Dataset | Read `rating.csv` + `movie.csv` |
| 2. Build Playlists | Each user → list of liked movies (rating ≥ 4.0) |
| 3. Train Word2Vec | `vector_size=128`, `window=15`, `epochs=20` |
| 4. Recommend | `recommend_movies(movie_id)` |

---

## Quick Start

```python
# Find a movie
find_movie('Matrix')

# Get recommendations
recommend_movies(2571)

# Recommend based on multiple movies
recommend_from_watchlist([58559, 79132, 2959])
```

---

## Requirements

```
gensim==4.3.3
pandas
scikit-learn
matplotlib
```

---

## Results

```
🎬  Matrix, The (1999)
    Genres: Action|Sci-Fi|Thriller

✨  Top 5 recommendations:
   Blair Witch Project (1999)   Thriller         0.385
   Thin Red Line, The (1998)    Action|Drama|War  0.367
   Cube (1997)                  Sci-Fi|Thriller   0.359
   Star Wars: Episode I (1999)  Action|Sci-Fi     0.356
   13th Warrior, The (1999)     Action|Adventure  0.352
```
