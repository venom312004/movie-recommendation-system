# 🎬 Movie Recommender System

![Python](https://img.shields.io/badge/Python-3.11-blue?style=for-the-badge&logo=python)
![FastAPI](https://img.shields.io/badge/FastAPI-0.111-green?style=for-the-badge&logo=fastapi)
![Streamlit](https://img.shields.io/badge/Streamlit-1.36-red?style=for-the-badge&logo=streamlit)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.5-orange?style=for-the-badge&logo=scikit-learn)
![Deployed](https://img.shields.io/badge/Deployed-Render-purple?style=for-the-badge&logo=render)

> A full-stack AI-powered movie recommendation system built with a FastAPI backend and Streamlit frontend, deployed on Render.

🔗 **Live Demo:** [movie-recommendation-system-53su.onrender.com](https://movie-recommendation-system-53su.onrender.com)

---

## 📌 Overview

This project is an end-to-end machine learning application that recommends movies based on content similarity. Users can search for any movie title and receive intelligent recommendations powered by TF-IDF vectorization and cosine similarity, enriched with real-time data from the TMDB API.

---

## ✨ Features

- 🔍 **Keyword Search** with live dropdown suggestions
- 🎯 **Content-Based Recommendations** using TF-IDF + Cosine Similarity
- 🎭 **Genre-Based Recommendations** via TMDB Discover API
- 🖼️ **Movie Posters & Details** fetched from TMDB API
- 🏠 **Home Feed** with Trending, Popular, Top Rated, Upcoming movies
- ⚡ **Fast REST API** built with FastAPI
- 📱 **Responsive UI** built with Streamlit

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | Streamlit |
| **Backend** | FastAPI + Uvicorn |
| **ML Model** | TF-IDF Vectorizer + Cosine Similarity |
| **Data Processing** | Pandas, NumPy, Scikit-learn |
| **External API** | TMDB (The Movie Database) |
| **Deployment** | Render (Free Tier) |
| **Language** | Python 3.11 |

---

## 🧠 How It Works

```
User Input (Movie Title)
        ↓
TMDB API → Fetch Movie Details + Poster
        ↓
TF-IDF Matrix → Cosine Similarity → Top N Similar Movies
        ↓
TMDB API → Enrich recommendations with posters
        ↓
Streamlit UI → Display results
```

1. The dataset (`movies_metadata.csv`) is preprocessed and a **TF-IDF matrix** is built on movie overviews
2. When a user searches for a movie, **cosine similarity** is computed against all movies
3. Top similar movies are returned along with **TMDB metadata** (posters, ratings, genres)
4. Genre-based recommendations are fetched via **TMDB Discover API**

---

## 📁 Project Structure

```
movie-recommendation-system/
│
├── main.py                 # FastAPI backend (REST API)
├── app.py                  # Streamlit frontend (UI)
├── generate_pkl.py         # Script to generate ML pickle files
├── requirements.txt        # Python dependencies
├── runtime.txt             # Python version for Render
├── .python-version         # Python version file
│
├── movies_metadata.csv     # Dataset (45,000+ movies)
├── df.pkl                  # Preprocessed DataFrame
├── tfidf.pkl               # TF-IDF Vectorizer
├── tfidf_matrix.pkl        # TF-IDF Matrix (sparse)
└── indices.pkl             # Movie title → index mapping
```

---

## 🚀 Getting Started

### Prerequisites
- Python 3.11
- TMDB API Key → [Get it here](https://www.themoviedb.org/settings/api)

### Installation

```bash
# Clone the repository
git clone https://github.com/venom312004/movie-recommendation-system.git
cd movie-recommendation-system

# Create virtual environment
python -m venv .venv
.venv\Scripts\activate  # Windows
# source .venv/bin/activate  # Mac/Linux

# Install dependencies
pip install -r requirements.txt
```

### Setup Environment Variables

Create a `.env` file in the root directory:
```
TMDB_API_KEY=your_tmdb_api_key_here
```

### Generate ML Files

```bash
python generate_pkl.py
```

### Run Locally

```bash
# Start FastAPI backend
uvicorn main:app --reload

# Start Streamlit frontend (in a new terminal)
streamlit run app.py
```

---

## 🌐 API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/health` | Health check |
| GET | `/home?category=trending` | Home feed movies |
| GET | `/tmdb/search?query=avatar` | Search movies |
| GET | `/movie/id/{tmdb_id}` | Movie details |
| GET | `/recommend/tfidf?title=Avatar` | TF-IDF recommendations |
| GET | `/recommend/genre?tmdb_id=19995` | Genre recommendations |
| GET | `/movie/search?query=Avatar` | Full bundle (details + recs) |

---

## 📊 Dataset

- **Source:** [TMDB Movies Metadata](https://www.kaggle.com/datasets/rounakbanik/the-movies-dataset)
- **Size:** 45,000+ movies
- **Features used:** `title`, `overview`, `genres`

---

## 🙋‍♂️ Author

**Pranjal Pandey**

[![GitHub](https://img.shields.io/badge/GitHub-venom312004-black?style=flat&logo=github)](https://github.com/venom312004)

---

## ⭐ Show Your Support

If you found this project helpful, please consider giving it a **star** on GitHub! ⭐
