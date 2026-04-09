<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:00ffa3,50:7b61ff,100:ff6b6b&height=220&section=header&text=🎵%20Music%20Recommender&fontSize=48&fontColor=ffffff&fontAlignY=40&desc=Lyrics-Based%20Content%20Filtering%20%7C%20TF-IDF%20%2B%20Cosine%20Similarity&descAlignY=62&descColor=cccccc&animation=fadeIn" width="100%"/>

<br/>

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=22&duration=3000&pause=800&color=00FFA3&center=true&vCenter=true&multiline=true&width=700&height=80&lines=Feed+it+a+song+%F0%9F%8E%B5;Get+back+5+that+feel+the+same+%F0%9F%94%8D;Built+on+57%2C650+songs+%E2%9C%85" alt="Typing SVG" />

<br/><br/>

[![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org)
[![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)](https://streamlit.io)
[![NLTK](https://img.shields.io/badge/NLTK-3F7CAC?style=for-the-badge&logo=python&logoColor=white)](https://nltk.org)
[![Kaggle](https://img.shields.io/badge/Kaggle-20BEFF?style=for-the-badge&logo=kaggle&logoColor=white)](https://kaggle.com)
[![License](https://img.shields.io/badge/License-CC0--1.0-lightgrey?style=for-the-badge)](https://creativecommons.org/publicdomain/zero/1.0/)

<br/>

[![Stars](https://img.shields.io/github/stars/your-username/music-recommendation-app-python?style=social)](https://github.com/your-username/music-recommendation-app-python/stargazers)
[![Forks](https://img.shields.io/github/forks/your-username/music-recommendation-app-python?style=social)](https://github.com/your-username/music-recommendation-app-python/network/members)

</div>

---

## 🌊 Overview

<table>
<tr>
<td width="50%">

### What it does
A **content-based music recommendation system** that analyzes song lyrics using NLP to find musically similar tracks.

- 🎤 Processes **raw lyrics** — not metadata
- 🧹 Cleans text with **NLTK** (regex + stopwords)
- 📐 Vectorizes with **TF-IDF** (5,000 features)
- 🔗 Scores with **Cosine Similarity**
- ⚡ Serves results via **Streamlit**

</td>
<td width="50%">

### Dataset Stats

| Metric | Value |
|--------|-------|
| 🎵 Total Songs | **57,650** |
| 🎲 Model Sample | **10,000** |
| 📐 TF-IDF Features | **5,000** |
| 📊 Similarity Matrix | **10K × 10K** |
| 🏆 Top Artists | Donna Summer, Bob Dylan… |
| 🎯 Output | **Top 5 recommendations** |

</td>
</tr>
</table>

---

## 🔬 System Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                     🎵 MUSIC RECOMMENDER PIPELINE               │
└─────────────────────────────────────────────────────────────────┘

  📦 Kaggle Dataset          🎲 10K Random Sample
  (57,650 songs)    ──────►  (for performance)
       │                            │
       ▼                            ▼
  ┌─────────────────────────────────────────┐
  │           🧹 NLTK PREPROCESSING         │
  │  • Strip special chars  (regex)         │
  │  • Lowercase conversion                 │
  │  • word_tokenize()                      │
  │  • Remove English stopwords             │
  └──────────────────┬──────────────────────┘
                     │
                     ▼
  ┌─────────────────────────────────────────┐
  │         📐 TF-IDF VECTORIZATION         │
  │  TfidfVectorizer(max_features=5000)     │
  │  Output: sparse matrix [10K × 5K]      │
  └──────────────────┬──────────────────────┘
                     │
                     ▼
  ┌─────────────────────────────────────────┐
  │         🔗 COSINE SIMILARITY            │
  │  cosine_similarity(tfidf, tfidf)        │
  │  Output: dense matrix [10K × 10K]      │
  └──────────────────┬──────────────────────┘
                     │
                     ▼
  ┌─────────────────────────────────────────┐
  │         🎯 RECOMMENDATION ENGINE        │
  │  Input:  song name (string)             │
  │  Lookup: index in dataframe             │
  │  Sort:   similarity scores desc         │
  │  Return: Top-N artist + song names      │
  └─────────────────────────────────────────┘
```

---

## 🚀 Quick Start

<details>
<summary><b>📋 Prerequisites</b></summary>
<br/>

```
Python 3.7+
Kaggle account (for dataset download)
```
</details>

<details>
<summary><b>⚙️ Step 1 — Clone the repo</b></summary>
<br/>

```bash
git clone https://github.com/your-username/music-recommendation-app-python.git
cd music-recommendation-app-python
```
</details>

<details>
<summary><b>📦 Step 2 — Install dependencies</b></summary>
<br/>

```bash
pip install -r requirements.txt
```

**requirements.txt:**
```
pandas
numpy
scikit-learn
nltk
wordcloud
matplotlib
streamlit
kaggle
```
</details>

<details>
<summary><b>🔑 Step 3 — Set up Kaggle API</b></summary>
<br/>

> Login to Kaggle → Profile Icon → **Settings** → **API** → **Create New Token**
> This downloads `kaggle.json`

```bash
# Linux / macOS
mkdir ~/.kaggle
cp kaggle.json ~/.kaggle/
chmod 600 ~/.kaggle/kaggle.json

# Windows (PowerShell)
mkdir $env:USERPROFILE\.kaggle
Copy-Item kaggle.json $env:USERPROFILE\.kaggle\
```
</details>

<details>
<summary><b>📥 Step 4 — Download the dataset</b></summary>
<br/>

```bash
kaggle datasets download notshrirang/spotify-million-song-dataset
unzip spotify-million-song-dataset.zip
```
</details>

<details>
<summary><b>▶️ Step 5 — Run the app</b></summary>
<br/>

```bash
streamlit run app.py
```

App opens at → **`http://localhost:8501`**
</details>

---

## 🧠 Core Code

<details open>
<summary><b>🧹 Text Preprocessing</b></summary>
<br/>

```python
import re
import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize

nltk.download('punkt')
nltk.download('stopwords')

stop_words = set(stopwords.words('english'))

def preprocess_text(text):
    # Remove special characters and numbers
    text = re.sub(r"[^a-zA-Z\s]", "", text)
    # Convert to lowercase
    text = text.lower()
    # Tokenize
    tokens = word_tokenize(text)
    # Remove stopwords
    tokens = [word for word in tokens if word not in stop_words]
    return " ".join(tokens)

# Apply to all lyrics
df['cleaned_text'] = df['text'].apply(preprocess_text)
```
</details>

<details open>
<summary><b>📐 TF-IDF + Cosine Similarity</b></summary>
<br/>

```python
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.metrics.pairwise import cosine_similarity

# Vectorize
tfidf_vectorizer = TfidfVectorizer(max_features=5000)
tfidf_matrix    = tfidf_vectorizer.fit_transform(df['cleaned_text'])

# Compute similarity (10K x 10K matrix)
cosine_sim = cosine_similarity(tfidf_matrix, tfidf_matrix)
```
</details>

<details open>
<summary><b>🎯 Recommendation Function</b></summary>
<br/>

```python
def recommend_songs(song_name, cosine_sim=cosine_sim, df=df, top_n=5):
    # Find song index (case-insensitive)
    idx = df[df['song'].str.lower() == song_name.lower()].index
    if len(idx) == 0:
        return "Song not found in the dataset!"
    idx = idx[0]

    # Sort by similarity score, skip index 0 (self-match)
    sim_scores = list(enumerate(cosine_sim[idx]))
    sim_scores = sorted(sim_scores, key=lambda x: x[1], reverse=True)
    sim_scores = sim_scores[1:top_n + 1]

    # Return artist + song name
    song_indices = [i[0] for i in sim_scores]
    return df[['artist', 'song']].iloc[song_indices]
```
</details>

<details>
<summary><b>🖥️ Full Streamlit App (app.py)</b></summary>
<br/>

```python
import streamlit as st
import pandas as pd
import re
import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.metrics.pairwise import cosine_similarity
from wordcloud import WordCloud
import matplotlib.pyplot as plt

st.set_page_config(page_title="🎵 Music Recommender", layout="wide")
st.title("🎵 Music Recommendation System")
st.markdown("*Find songs with similar lyrics — powered by TF-IDF & Cosine Similarity*")

@st.cache_data
def load_and_process():
    df = pd.read_csv("spotify_millsongdata.csv")
    df = df.sample(10000).drop('link', axis=1).reset_index(drop=True)

    nltk.download('punkt', quiet=True)
    nltk.download('stopwords', quiet=True)
    stop_words = set(stopwords.words('english'))

    def clean(text):
        text = re.sub(r"[^a-zA-Z\s]", "", text).lower()
        tokens = word_tokenize(text)
        return " ".join([w for w in tokens if w not in stop_words])

    df['cleaned_text'] = df['text'].apply(clean)
    tfidf = TfidfVectorizer(max_features=5000).fit_transform(df['cleaned_text'])
    sim   = cosine_similarity(tfidf, tfidf)
    return df, sim

with st.spinner("Loading model..."):
    df, cosine_sim = load_and_process()

col1, col2 = st.columns([2, 1])

with col1:
    song_input = st.text_input("Enter a song name:", placeholder="e.g. For The First Time")
    if song_input:
        idx = df[df['song'].str.lower() == song_input.lower()].index
        if len(idx) == 0:
            st.error("Song not found in the dataset!")
        else:
            idx = idx[0]
            sim_scores = sorted(enumerate(cosine_sim[idx]), key=lambda x: x[1], reverse=True)[1:6]
            result = df[['artist', 'song']].iloc[[i[0] for i in sim_scores]]
            st.success(f"Top 5 recommendations for **{song_input}**")
            st.dataframe(result, use_container_width=True)

with col2:
    st.subheader("☁️ Lyric Word Cloud")
    sample = " ".join(df['cleaned_text'].sample(500))
    wc = WordCloud(width=400, height=300, background_color='black',
                   colormap='cool').generate(sample)
    fig, ax = plt.subplots(figsize=(5, 3.5))
    ax.imshow(wc, interpolation='bilinear')
    ax.axis('off')
    fig.patch.set_facecolor('black')
    st.pyplot(fig)
```
</details>

---

## 💡 Example Output

```
Input: "For The First Time"

┌──────────────────────┬────────────────────────┐
│ Artist               │ Song                   │
├──────────────────────┼────────────────────────┤
│ Van Halen            │ Mine All Mine          │
│ The Beatles          │ I Me Mine              │
│ Bob Seger            │ I Wonder               │
│ Nat King Cole        │ Because You're Mine    │
│ Linda Ronstadt       │ He Was Mine            │
└──────────────────────┴────────────────────────┘
```

---

## 🛠️ Tech Stack

<div align="center">
<img src="https://skillicons.dev/icons?i=python,sklearn&theme=dark" height="48"/>
</div>

<br/>

| Tool | Role |
|------|------|
| `pandas` | Data loading & manipulation |
| `numpy` | Numerical operations |
| `scikit-learn` | TF-IDF vectorization + cosine similarity |
| `nltk` | Tokenization & stopword removal |
| `wordcloud` | Lyric frequency visualization |
| `matplotlib` | Plotting |
| `streamlit` | Interactive web UI |
| `kaggle` | Dataset download via API |

---

## 📁 Project Structure

```
music-recommendation-app-python/
│
├── 📄 app.py                      ← Streamlit UI
├── 📓 notebook.ipynb              ← Full analysis notebook
├── 📋 requirements.txt            ← Python dependencies
├── 🔑 kaggle.json                 ← API key (DO NOT commit!)
├── 📖 README.md                   ← You are here
│
└── 📁 data/
    └── spotify_millsongdata.csv   ← Downloaded via Kaggle API
```

> ⚠️ Add `kaggle.json` and `*.csv` to `.gitignore` — never commit credentials or large data files!

---

## 🔮 Roadmap

- [x] Content-based filtering on lyrics
- [x] TF-IDF + cosine similarity
- [x] Streamlit frontend
- [x] WordCloud visualization
- [ ] Fuzzy song name matching
- [ ] Spotify API — album art + audio preview
- [ ] Sentence-transformer semantic embeddings
- [ ] Hybrid model: lyrics + audio features (BPM, key, energy)
- [ ] Docker deployment

---

## 📜 License

Dataset: [CC0-1.0](https://creativecommons.org/publicdomain/zero/1.0/) via [Kaggle](https://www.kaggle.com/datasets/notshrirang/spotify-million-song-dataset/data)  
Code: [MIT](./LICENSE)

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:ff6b6b,50:7b61ff,100:00ffa3&height=140&section=footer&animation=fadeIn" width="100%"/>

**Built with 🎵 by [your-username](https://github.com/your-username)**

*If this helped you, drop a ⭐ — it means a lot!*

</div>
