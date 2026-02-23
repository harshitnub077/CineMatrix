# 🎬 CineMatrix: Movie Recommender System

CineMatrix is a Machine Learning-powered movie recommendation system designed to help users discover films tailored to their specific tastes. By leveraging detailed metadata from thousands of movies, including genres, cast, crew, and keywords, the system utilizes content-based filtering to provide highly accurate suggestions.

---

## 🌟 Key Features

- **Content-Based Filtering**: Recommends movies similar to the one you choose based on an advanced natural language processing (NLP) model analyzing narrative elements, cast, and creative crew.
- **Intuitive Web Interface**: Built with [Streamlit](https://streamlit.io/), the interface is fast, responsive, and incredibly user-friendly.
- **Dynamic Posters**: Automatically fetches high-quality movie posters using the [TMDB API](https://www.themoviedb.org/documentation/api) for every recommendation.
- **Efficient Data Handling**: The core similarity matrix is aggressively compressed using `bz2` to ensure blazing-fast load times and seamless deployment across cloud platforms like Streamlit Cloud—bypassing GitHub's strict file size limits.

---

## 🛠️ Tech Stack

- **Python**: Core programming language.
- **Pandas & NumPy**: For efficient data processing and matrix manipulation.
- **Scikit-Learn**: To generate Bag of Words and compute cosine similarity distances.
- **NLTK (Natural Language Toolkit)**: For text stemming and preprocessing the movie overview data.
- **Streamlit**: For the frontend user interface.
- **Pickle & BZ2**: For serializing and compressing Machine Learning models.
- **Requests**: To make HTTP calls to the TMDB API.

---

## 🚀 How It Works

1. **Data Collection & Cleaning**: The system processes the massive TMDB 5000 movies and credits datasets by merging them, cleaning null values, extracting nested JSON data, and converting strings into lists.
2. **Text Processing**: Keywords, overview text, genres, top cast, and director details are tokenized, stripped of spaces, stemmed, and merged into a single "Tags" corpus for every movie.
3. **Vectorization**: The system uses `CountVectorizer` to transform the "Tags" into mathematical vectors (Bag of Words technique).
4. **Similarity Scoring**: We compute the **Cosine Similarity** between all movies. The smaller the angle between two movie vectors, the more similar they are!
5. **Recommendation Pipeline**: When a user selects a movie, the system finds the 5 closest vectors and outputs the corresponding movie titles and posters.

---

## 💻 Installation & Local Setup

### Prerequisites

Ensure you have Python 3.8+ installed on your system. You will also need to generate your own API Key from TMDB for the posters to load.

### Steps

1. **Clone the repository:**
   ```bash
   git clone https://github.com/harshitnub077/CineMatrix.git
   cd CineMatrix
   ```

2. **Create a virtual environment (Recommended):**
   ```bash
   python -m venv .venv
   source .venv/bin/activate  # On Windows use: .venv\Scripts\activate
   ```

3. **Install the dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Update the TMDB API Key:**
   - Open `app.py`.
   - Locate the `fetch_poster()` function.
   - Replace the `api_key=...` parameter with your own TMDB API key.

5. **Run the Streamlit application:**
   ```bash
   streamlit run app.py
   ```

---

## 📦 Project Structure

```text
CineMatrix/
├── .devcontainer/         # VS Code Remote Container configs
├── .gitignore             # Ignored files, safely tracking large .bz2 files
├── README.md              # Project documentation
├── app.py                 # Core Streamlit web application
├── main.ipynb             # Jupyter Notebook detailing the entire ML pipeline
├── movies.pkl             # Serialized Pandas DataFrame
├── movies_dict.pkl        # Serialized dictionary of movie data
├── requirements.txt       # Python dependencies
├── setup.sh               # Optional deployment script 
└── similarity.pkl.bz2     # Highly compressed Cosine Similarity matrix (32MB)
```

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/harshitnub077/CineMatrix/issues).

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📜 License

Distributed under the MIT License. See `LICENSE` for more information.

---

<p align="center">
  Made with ❤️ by <a href="https://github.com/harshitnub077">Harshit</a>
</p>
