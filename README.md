# 🎬 Movie Recommender System

A content-based movie recommender system built using the TMDB 5000 dataset. 
Enter any movie and get 5 similar movie recommendations with posters.

## 🔗 Live Demo
[Click here to open the app](https://movie-recommender-system-mlprojectcse4mrid.streamlit.app/)

---

## 📌 What It Does
- Takes a movie name as input
- Recommends 5 similar movies using Machine Learning
- Displays movie posters fetched from the TMDB API

---

## 🧠 Algorithm Used — Content-Based Filtering

This project uses **Content-Based Filtering** — a type of recommender system 
that suggests movies based on the features of the movie itself, 
not based on what other users watched.

### How it works step by step:

1. **Data Collection** — Used the TMDB 5000 Movie Dataset from Kaggle
   which contains metadata for 5000 movies including genres, 
   keywords, cast, crew and overview.

2. **Feature Extraction** — The following features were extracted 
   for each movie:
   - Genres (e.g., Action, Drama)
   - Keywords (e.g., revenge, space)
   - Top 3 Cast members
   - Director name
   - Movie overview (plot summary)

3. **Tag Creation** — All extracted features were combined into 
   a single "tags" string per movie.
   Example: `"action adventure spacetravel interstellar nolanfilm"`

4. **Text Preprocessing** — Applied stemming using NLTK's 
   PorterStemmer to reduce words to their root form.
   Example: `"fighting" → "fight"`, `"actions" → "action"`
   This ensures similar words are treated as the same feature.

5. **Vectorization using CountVectorizer** — Converted the tags 
   text into numerical vectors using Bag of Words technique.
   Each movie becomes a vector of 5000 numbers representing 
   word frequencies.

6. **Cosine Similarity** — Calculated similarity score between 
   every pair of movies using Cosine Similarity.
   - Score of 1 = identical movies
   - Score of 0 = completely different movies
   The result is a 5000 x 5000 similarity matrix.

7. **Recommendation** — When a user selects a movie, the system:
   - Finds that movie's row in the similarity matrix
   - Sorts all other movies by similarity score
   - Returns the top 5 most similar movies

---

## 🗂️ Project Structure

| File | Description |
|------|-------------|
| `app.py` | Main Streamlit web application |
| `notebook86c26b4f17.ipynb` | Data processing notebook — generates model files |
| `movie_list.pkl` | Processed movie dataframe (serialized) |
| `requirements.txt` | Python dependencies |

> **Note:** `similarity.pkl` (176 MB cosine similarity matrix) is stored 
> on Google Drive and auto-downloaded by the app on first run using `gdown`.

---

## 🛠️ Tech Stack

| Technology | Purpose |
|------------|---------|
| Python | Core language |
| Pandas & NumPy | Data processing |
| Scikit-learn | CountVectorizer + Cosine Similarity |
| NLTK | Text stemming |
| Pickle | Saving/loading model files |
| Streamlit | Web app framework |
| gdown | Downloading large files from Google Drive |
| TMDB API | Fetching movie poster images |

---

## 🚀 How to Run Locally
```bash
pip install -r requirements.txt
streamlit run app.py
```

---

## 📊 Dataset
- **Source:** [TMDB 5000 Movie Dataset — Kaggle](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)
- **Files used:** `tmdb_5000_movies.csv` and `tmdb_5000_credits.csv`
- **Size:** ~5000 movies with full metadata

---

## 👤 Author
Made by **Ndroid-mskt**  
DTU — Computer Science Engineering
