# 🎬 CineMatch — Movie Recommendation System

<div align="center">

### Discover Your Next Favorite Movie with Machine Learning & NLP

**An end-to-end content-based movie recommendation web application built using Python, Natural Language Processing, scikit-learn, and Streamlit.**

[![Live Demo](https://img.shields.io/badge/🚀_Live_Demo-Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)](https://movie-recommendation-system-ashiwany25.streamlit.app)
[![GitHub](https://img.shields.io/badge/Source_Code-GitHub-181717?style=for-the-badge&logo=github)](https://github.com/Ashiwany25/Movie-Recommendation-System)

![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=flat-square&logo=python&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-Web_App-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-Machine_Learning-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data_Processing-150458?style=flat-square&logo=pandas&logoColor=white)
![NLP](https://img.shields.io/badge/NLP-Content_Based_Recommendation-blueviolet?style=flat-square)

**[🌐 Launch Live Application](https://movie-recommendation-system-ashiwany25.streamlit.app) • [💻 View Source Code](https://github.com/Ashiwany25/Movie-Recommendation-System)**

</div>

---

## 📌 Project Overview

**CineMatch** is an intelligent movie recommendation system that helps users discover movies similar to their favorites using **content-based filtering**.

The application analyzes movie descriptions, genres, and keywords to identify relationships between movies and generate relevant recommendations.

Unlike traditional recommendation systems that depend on user ratings or viewing histories, CineMatch uses the characteristics of the movies themselves.

The project demonstrates a complete machine learning application workflow, from data preprocessing and feature engineering to similarity-based recommendations, API integration, and cloud deployment.

### 🎯 Project Objectives

- Develop a content-based movie recommendation engine.
- Apply Natural Language Processing to movie metadata.
- Represent movie information using numerical feature vectors.
- Measure similarity between movies using cosine similarity.
- Build an interactive and responsive web application.
- Integrate TMDB API for real movie posters.
- Deploy the application publicly using Streamlit Community Cloud.

---

## ✨ Key Features

| Feature | Description |
|---|---|
| 🔎 Movie Search | Search and select movies from the available dataset |
| 🎯 Smart Recommendations | Discover movies similar to your selected title |
| 🧠 NLP-Powered Engine | Analyze descriptions, genres, and keywords |
| 📊 Cosine Similarity | Rank movies according to their content similarity |
| 🎬 Movie Posters | Fetch movie poster images using the TMDB API |
| ⭐ Movie Information | Display release year, ratings, genres, and overview |
| 🎛️ Custom Recommendations | Choose between 3 and 10 recommended movies |
| 🌙 Dark-Themed UI | Modern interface built using Streamlit |
| ⚡ Efficient Processing | Streamlit caching reduces repeated computation |
| ☁️ Cloud Deployment | Accessible through a public Streamlit website |

---

## 🌐 Live Application

**Experience the project here:**

### 🚀 [Open CineMatch — Movie Recommendation System](https://movie-recommendation-system-ashiwany25.streamlit.app)

### How to Use

1. Open the live application.
2. Search for a movie you enjoy.
3. Select the movie from the dropdown.
4. Choose how many recommendations you want.
5. Click **✨ Recommend movies**.
6. Explore recommended movies with posters, ratings, genres, and descriptions.

**Example:** Selecting a science-fiction movie such as *Avatar* may return movies with similar genres, story elements, or keywords.

Recommendations are generated dynamically from the available movie metadata.

---

## 🧠 Recommendation System Architecture

```text
                  ┌───────────────────────┐
                  │   TMDB Movies Dataset │
                  │  tmdb_5000_movies.csv │
                  └───────────┬───────────┘
                              │
                              ▼
                  ┌───────────────────────┐
                  │   Data Preprocessing  │
                  │  Cleaning & Parsing   │
                  └───────────┬───────────┘
                              │
                              ▼
                  ┌───────────────────────┐
                  │    Feature Extraction │
                  │ Overview + Genres +   │
                  │       Keywords        │
                  └───────────┬───────────┘
                              │
                              ▼
                  ┌───────────────────────┐
                  │    Text Vectorization │
                  │    CountVectorizer    │
                  │    Max 5000 Features  │
                  └───────────┬───────────┘
                              │
                              ▼
                  ┌───────────────────────┐
                  │    Cosine Similarity  │
                  │    Similarity Scores  │
                  └───────────┬───────────┘
                              │
                              ▼
                  ┌───────────────────────┐
                  │  Recommendation Engine│
                  │   Top Similar Movies  │
                  └───────────┬───────────┘
                              │
                              ▼
                  ┌───────────────────────┐
                  │     Streamlit UI      │
                  │ Movie Cards + Posters │
                  └───────────────────────┘
```

---

## ⚙️ How the Recommendation Engine Works

### 1. Dataset Loading

The application loads the TMDB movie metadata dataset using pandas.

```python
movies = pd.read_csv("data/tmdb_5000_movies.csv")
```

The dataset includes information such as:

- Movie ID and title
- Movie overview
- Genres
- Keywords
- Release date
- Average user rating

### 2. Data Preprocessing

The application prepares the dataset by:

- Removing duplicate movie IDs.
- Removing records with missing titles or overviews.
- Parsing JSON-formatted genre and keyword fields.
- Normalizing text to lowercase.
- Combining related words into consistent tokens.

For example:

```text
Science Fiction → sciencefiction
```

This helps preserve multiword genre and keyword names as individual features.

### 3. Feature Engineering

Each movie is represented by a combined text description called **tags**.

The tags are created from:

```text
Movie Tags = Overview + Genres + Keywords
```

Genres and keywords receive additional weight through repeated tokens.

This helps the recommendation engine consider both the movie's plot and its metadata.

### 4. Text Vectorization

Machine learning algorithms cannot directly calculate similarity between raw text descriptions.

Therefore, the application uses **CountVectorizer** from scikit-learn.

```python
CountVectorizer(
    max_features=5000,
    stop_words="english"
)
```

**Why CountVectorizer?**

- Converts text into numerical vectors.
- Represents the frequency of words.
- Removes common English stop words.
- Is simple, efficient, and interpretable.
- Works well as a baseline for content-based recommendations.

The application uses up to **5,000 vocabulary features**.

### 5. Cosine Similarity

The recommendation engine measures similarity between movie vectors using cosine similarity.

\[
\text{Cosine Similarity}(A,B)
=
\frac{A\cdot B}{\|A\|\|B\|}
\]

Where:

- \(A\) represents the selected movie vector.
- \(B\) represents another movie vector.
- A higher similarity score indicates greater similarity in the extracted text features.

The algorithm compares the selected movie with the available catalog, ranks the similarity scores, and excludes the selected movie itself.

### 6. Recommendation Generation

The system:

1. Finds the selected movie in the dataset.
2. Calculates its cosine similarity with other movies.
3. Sorts the results by similarity score.
4. Excludes the selected movie.
5. Returns the requested number of recommendations.

This approach is known as **content-based filtering**.

### 7. Movie Poster Integration

The application uses the **TMDB API** to retrieve poster images.

```text
Selected Movie
      │
      ▼
TMDB Movie ID
      │
      ▼
TMDB API Request
      │
      ▼
Poster Path
      │
      ▼
Movie Poster Display
```

The TMDB API is used for poster retrieval, not for calculating the recommendations.

---

## 🛠️ Technology Stack

| Category | Technology | Purpose |
|---|---|---|
| Programming | Python | Core application development |
| Data Processing | Pandas | Data cleaning and manipulation |
| Machine Learning | Scikit-learn | Vectorization and similarity calculations |
| NLP | CountVectorizer | Converting text into numerical features |
| Recommendation | Cosine Similarity | Ranking related movies |
| Frontend | Streamlit | Interactive user interface |
| API Integration | TMDB API | Retrieving movie posters |
| HTTP Requests | Requests | Communicating with TMDB |
| Deployment | Streamlit Community Cloud | Hosting the live application |
| Version Control | Git & GitHub | Source code management |

---

## 📂 Project Structure

```text
Movie-Recommendation-System/
│
├── app.py
│   └── Streamlit application and recommendation engine
│
├── data/
│   ├── tmdb_5000_movies.csv
│   └── README.md
│
├── .streamlit/
│   ├── config.toml
│   └── secrets.toml.example
│
├── requirements.txt
│   └── Python dependencies
│
├── .gitignore
│   └── Excluded files and sensitive information
│
└── README.md
    └── Project documentation
```

---

## 📊 Dataset Information

**Dataset:** TMDB 5000 Movie Metadata

**Source:** [Kaggle — TMDB Movie Metadata](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)

The source dataset contains metadata for approximately 5,000 movies.

The application uses:

```text
tmdb_5000_movies.csv
```

The following columns are required:

| Column | Description |
|---|---|
| `id` | Unique TMDB movie identifier |
| `title` | Movie title |
| `overview` | Plot summary |
| `genres` | Movie genres |
| `keywords` | Descriptive keywords |
| `release_date` | Release date |
| `vote_average` | Average TMDB rating |

**Note:** The current application does not require `tmdb_5000_credits.csv`.

Dataset redistribution is subject to the source's applicable terms.

---

## 💻 Installation and Local Setup

### Prerequisites

Make sure the following are installed:

- Python 3.10 or newer
- Git
- VS Code or another Python editor
- Internet connection for poster retrieval
- TMDB API key (optional for recommendations, required for posters)

### Step 1 — Clone the Repository

```bash
git clone https://github.com/Ashiwany25/Movie-Recommendation-System.git
```

Navigate into the project:

```bash
cd Movie-Recommendation-System
```

### Step 2 — Create a Virtual Environment

**macOS / Linux**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

**Windows PowerShell**

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

### Step 3 — Install Dependencies

```bash
pip install -r requirements.txt
```

The main dependencies include:

```text
streamlit
pandas
scikit-learn
requests
```

### Step 4 — Prepare the Dataset

Ensure the dataset is available at:

```text
data/tmdb_5000_movies.csv
```

If it is not present, download it from the Kaggle source and place it in the `data` directory.

### Step 5 — Configure TMDB API

Create a file named:

```text
.streamlit/secrets.toml
```

Add:

```toml
TMDB_API_KEY = "YOUR_TMDB_API_KEY"
```

Obtain your API key from:

https://www.themoviedb.org/settings/api

**Security:** Never commit real API keys or credentials to GitHub.

### Step 6 — Run the Application

```bash
streamlit run app.py
```

The application will normally open at:

```text
http://localhost:8501
```

---

## ☁️ Deployment on Streamlit Community Cloud

This project is deployed using **Streamlit Community Cloud**.

### Deployment Steps

1. Push the application code to GitHub.
2. Open [Streamlit Community Cloud](https://share.streamlit.io/).
3. Sign in using GitHub.
4. Select **Create app**.
5. Choose the repository:

   `Ashiwany25/Movie-Recommendation-System`

6. Select the `main` branch.
7. Set the main file path to `app.py`.
8. Make sure the required dataset is available in the deployment.
9. Configure the TMDB API key under **App Settings → Secrets**.
10. Deploy the application.

### Production Application

**Live URL:**

https://movie-recommendation-system-ashiwany25.streamlit.app

---

## 🧪 Testing and Validation

The deployed application can be checked using the following functional tests:

| Test Case | Expected Result |
|---|---|
| Application startup | Streamlit interface loads successfully |
| Movie selection | Movie titles appear in the selection field |
| Recommendation generation | Similar movies are returned |
| Result count | The selected number of recommendations appears |
| Poster retrieval | Available TMDB posters are displayed |
| Movie information | Titles, ratings, genres, and overviews are displayed |
| Missing API key | App continues with a poster-unavailable fallback |
| Missing dataset | Application displays a dataset warning |

**Validation status:** The deployed application has been manually confirmed to display movie recommendations and posters. Formal recommendation relevance benchmarks and automated test results are not reported.

---

## 📈 Performance and Design Considerations

The application includes several practical optimizations:

**1. Streamlit caching**

Processed movie data and vectorized features are cached to reduce repeated work.

**2. Sparse feature representation**

CountVectorizer produces a sparse matrix, avoiding the need to store a dense feature vector for every movie.

**3. On-demand similarity calculation**

Similarity scores are computed for the selected movie when recommendations are requested.

**4. Poster caching**

TMDB poster lookups are cached to reduce repeated API requests.

**5. Configurable recommendation count**

Users can select between 3 and 10 results without changing the underlying model.

---

## 🔍 Content-Based vs Collaborative Filtering

| Content-Based Filtering | Collaborative Filtering |
|---|---|
| Uses movie characteristics | Uses user interactions |
| Does not require user history | Usually requires user behavior |
| Can recommend based on one selected movie | Learns patterns across users |
| Works with metadata | Works with ratings, clicks, or watch history |
| Used in this project | Not implemented in this project |

CineMatch uses content-based filtering because the available dataset contains rich movie metadata but does not provide the user interaction history needed for collaborative filtering.

---

## ⚠️ Current Limitations

Although CineMatch provides useful content-based recommendations, some limitations remain:

- Recommendations depend on the quality of movie descriptions and metadata.
- The system does not learn individual user preferences over time.
- Recommendations are restricted to the available movie catalog.
- The current implementation does not use actor or director information.
- Text-based similarity does not always reflect personal taste.
- Movie posters depend on TMDB API availability.
- Formal accuracy, precision, recall, and ranking-quality evaluations have not yet been performed.

---

## 🚀 Future Enhancements

Potential improvements include:

- **Semantic embeddings:** Use Sentence Transformers or other embedding models for deeper text similarity.
- **Hybrid recommendations:** Combine content-based and collaborative filtering.
- **Cast and director features:** Enrich the recommendation engine with additional metadata.
- **User accounts:** Save favorites and recommendation history.
- **Genre filters:** Allow filtering by genre, year, and rating.
- **Movie trailers:** Integrate trailer links where available.
- **Evaluation metrics:** Measure Precision@K, Recall@K, and ranking relevance using suitable evaluation data.
- **Expanded movie catalog:** Support additional movies and updated metadata.
- **Personalized recommendations:** Adapt recommendations using explicit user preferences.

---

## 🎓 Key Learning Outcomes

This project demonstrates practical experience with:

- Python application development
- Data preprocessing and feature engineering
- Natural Language Processing fundamentals
- Bag-of-words text representation
- Cosine similarity and vector mathematics
- Content-based recommendation algorithms
- API integration and error handling
- Streamlit interface development
- Caching and application performance
- Git and GitHub version control
- Cloud deployment and configuration management
- Secure management of API credentials

---

## 🙏 Acknowledgements

Special thanks to:

- [The Movie Database (TMDB)](https://www.themoviedb.org/) for movie metadata and poster API services.
- [Kaggle](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata) for hosting the TMDB 5000 Movie Metadata dataset.
- [Scikit-learn](https://scikit-learn.org/) for machine learning tools.
- [Streamlit](https://streamlit.io/) for web application development and deployment.

*This product uses the TMDB API but is not endorsed or certified by TMDB.*

Movie poster images belong to their respective rights holders.

---

## 👨‍💻 Developer

<div align="center">

<h2>Ashiwany Kumar</h2>

<h3>Computer Science & Engineering (AI & ML)</h3>

<p>Haldia Institute of Technology</p>

<a href="https://github.com/Ashiwany25">
  <img src="https://img.shields.io/badge/GitHub-Ashiwany25-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub Profile"/>
</a>

</div>

<br>

---

<div align="center">

<h2>⭐ Support This Project</h2>

<p>If you found this project useful, consider giving it a ⭐ on GitHub.</p>

<p><b>Made with ❤️ using Python, NLP, Machine Learning, and Streamlit.</b></p>

<p>
  <a href="https://ashiwany-spam-classifier.streamlit.app/">🚀 Live Demo</a>
  |
  <a href="https://github.com/Ashiwany25/Email-Spam-Classifier">💻 GitHub Repository</a>
</p>

</div>
