# 🎬 CineMatch — Movie Recommendation System

**A content-based movie recommendation application built with Python, NLP, scikit-learn, and Streamlit.**

[![Python](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)](https://www.python.org/) [![Streamlit](https://img.shields.io/badge/Streamlit-App-FF4B4B?logo=streamlit&logoColor=white)](https://streamlit.io/) [![scikit-learn](https://img.shields.io/badge/scikit--learn-NLP-F7931E?logo=scikitlearn&logoColor=white)](https://scikit-learn.org/)

## Overview

CineMatch recommends movies similar to a title selected by the user. It analyzes plot descriptions, genres, and keywords from the TMDB 5000 Movie Metadata dataset using a bag-of-words representation and cosine similarity.

## Features

- Search for a movie by title
- Get 3–10 similar movie recommendations
- Weighted overview, genre, and keyword features
- Movie release year, average rating, genres, and synopsis
- Optional movie posters using the TMDB API
- Dark-themed responsive Streamlit interface
- Cached dataset, feature matrix, and poster requests

## Tech Stack

| Technology | Role |
|---|---|
| Python | Application logic |
| pandas | Data preprocessing |
| scikit-learn | CountVectorizer and cosine similarity |
| Streamlit | Interactive web application |
| TMDB API | Optional poster retrieval |

## Recommendation Pipeline

```text
TMDB Movies CSV
      ↓
Clean titles and metadata
      ↓
Combine overview + weighted genres + keywords
      ↓
CountVectorizer (up to 5,000 features)
      ↓
Cosine similarity
      ↓
Rank and display 3–10 similar movies
```

This is a **content-based** recommender, not a collaborative-filtering model. It does not use personal viewing histories, cast, or director features.

## Project Structure

```text
Movie-Recommendation-System/
├── app.py
├── requirements.txt
├── README.md
├── .gitignore
├── .streamlit/
│   ├── config.toml
│   └── secrets.toml.example
└── data/
    ├── README.md
    └── tmdb_5000_movies.csv  # Add this yourself
```

## Dataset

Download [TMDB 5000 Movie Metadata](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata) and place `tmdb_5000_movies.csv` in `data/`. The credits CSV is not required. Review the dataset terms before redistributing.

## Local Setup

```bash
git clone https://github.com/Ashiwany25/Movie-Recommendation-System.git
cd Movie-Recommendation-System
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
streamlit run app.py
```

For Windows PowerShell, activate with `.venv\Scripts\Activate.ps1`.

## Movie Posters

Create `.streamlit/secrets.toml` locally with:

```toml
TMDB_API_KEY = "your_tmdb_v3_api_key"
```

On Streamlit Community Cloud, add the same setting in **App settings → Secrets**. Never commit the real key.

## Deployment

1. Upload the project to your GitHub repository.
2. Add the dataset to `data/` if redistribution is permitted.
3. On [Streamlit Community Cloud](https://share.streamlit.io/), create a new app from your repository.
4. Set the entry point to `app.py` and add `TMDB_API_KEY` in Secrets if you want posters.
5. Deploy.

## Limitations and Future Work

The model relies on metadata similarity rather than user feedback. Potential improvements include adding cast/director metadata, semantic embeddings, user feedback, and relevance evaluation.

## Acknowledgements

- [TMDB 5000 Movie Metadata](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)
- [CampusX Movie Recommender](https://github.com/campusx-official/movie-recommender-system-tmdb-dataset) — inspiration
- [TMDB](https://www.themoviedb.org/) — metadata and poster API

*This product uses the TMDB API but is not endorsed or certified by TMDB.*
