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

## 🗺️ Project Mind Map

```mermaid
mindmap
  root((🎵 Music<br/>Recommender))
    📦 Data
      Kaggle API
        57650 Songs
        artist / song / text
      10K Random Sample
        drop link column
        reset index
    🧹 Preprocessing
      NLTK
        punkt tokenizer
        english stopwords
      regex
        strip non-alpha chars
      Lowercase
      Join cleaned tokens
    📐 Vectorization
      TF-IDF
        max_features 5000
        sparse matrix
        10K × 5K shape
    🔗 Similarity
      Cosine Similarity
        10K × 10K matrix
        pairwise scores
        range 0 to 1
    🎯 Recommender
      Input song name
      Lookup index
      Sort by score desc
      Skip self match
      Return Top 5
    🖥️ Frontend
      Streamlit UI
        text input
        results table
      WordCloud
        matplotlib
        frequency viz
```

---

## 🔬 Pipeline Flow Graph

```mermaid
flowchart TD
    A([🗂️ Kaggle Dataset\n57,650 Songs]) --> B[📥 Download via\nKaggle API]
    B --> C[🎲 Random Sample\n10,000 Songs]
    C --> D[🗑️ Drop link column\nReset index]
    D --> E{🧹 NLTK\nPreprocessing}

    E --> E1[Strip special chars\nvia regex]
    E --> E2[Lowercase\nconversion]
    E --> E3[word_tokenize\ninto tokens]
    E --> E4[Remove English\nstopwords]

    E1 & E2 & E3 & E4 --> F[📐 TF-IDF Vectorizer\nmax_features = 5000]

    F --> G[🔢 Sparse Matrix\n10,000 × 5,000]
    G --> H[🔗 Cosine Similarity\nPairwise computation]
    H --> I[📊 Similarity Matrix\n10,000 × 10,000]

    I --> J[/🎤 Input: Song Name/]
    J --> K{Song in\ndataset?}
    K -- ❌ No --> L([⚠️ Not Found Message])
    K -- ✅ Yes --> M[🔍 Lookup row index]
    M --> N[📈 Sort by similarity\nscore descending]
    N --> O[⏭️ Skip index 0\nself-match]
    O --> P([🎵 Top 5 Similar Songs\nartist + song name])

    style A fill:#1a1a2e,color:#00ffa3,stroke:#00ffa3
    style P fill:#1a1a2e,color:#00ffa3,stroke:#00ffa3
    style L fill:#2d1b1b,color:#ff6b6b,stroke:#ff6b6b
    style E fill:#1a1040,color:#a78bfa,stroke:#7b61ff
    style F fill:#1a1040,color:#a78bfa,stroke:#7b61ff
    style H fill:#1a1040,color:#a78bfa,stroke:#7b61ff
    style K fill:#0d2d1a,color:#6ee7b7,stroke:#00ffa3
```

---

## 🧩 Tech Stack Graph

```mermaid
graph LR
    subgraph INPUT["📥 Data Layer"]
        A1[🏆 Kaggle API] --> A2[(spotify_millsongdata.csv)]
        A2 --> A3[pandas DataFrame]
    end

    subgraph NLP["🧹 NLP Layer"]
        B1[re — regex cleaner]
        B2[nltk — tokenizer]
        B3[stopwords filter]
        B1 --> B4[cleaned_text column]
        B2 --> B4
        B3 --> B4
    end

    subgraph ML["🤖 ML Layer"]
        C1[TfidfVectorizer\nscikit-learn]
        C2[cosine_similarity\nscikit-learn]
        C1 --> C3[Sparse Matrix\n10K × 5K]
        C3 --> C2
        C2 --> C4[Similarity Grid\n10K × 10K]
    end

    subgraph APP["🖥️ App Layer"]
        D1[⚡ Streamlit\ntext input]
        D2[📊 Results Table]
        D3[☁️ WordCloud +\nMatplotlib]
    end

    A3 --> NLP
    B4 --> ML
    C4 --> APP

    style INPUT fill:#0a1628,stroke:#3b82f6,color:#93c5fd
    style NLP fill:#0a1a0a,stroke:#22c55e,color:#86efac
    style ML fill:#1a0a28,stroke:#a855f7,color:#d8b4fe
    style APP fill:#1a0a0a,stroke:#ef4444,color:#fca5a5
```

---

## 🔁 Recommendation Logic Graph

```mermaid
graph TD
    Q([🎤 Query: Song Name]) --> R1[Normalize to lowercase]
    R1 --> R2[Match against df song column]
    R2 --> R3[Get integer index idx]
    R3 --> R4[Slice row from\ncosine_sim matrix]
    R4 --> R5[enumerate scores\nas idx-score pairs]
    R5 --> R6[sort descending\nby score]
    R6 --> R7[slice index 1 to top_n+1\nskip self at 0]
    R7 --> R8[extract song_indices list]
    R8 --> R9([🎵 df artist + song\niloc song_indices])

    style Q fill:#0d2d20,color:#00ffa3,stroke:#00ffa3
    style R9 fill:#0d2d20,color:#00ffa3,stroke:#00ffa3
    style R4 fill:#1a1040,color:#c4b5fd,stroke:#7b61ff
    style R6 fill:#1a1040,color:#c4b5fd,stroke:#7b61ff
```

---

## 🚀 Quick Start

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

```
pandas / numpy / scikit-learn / nltk / wordcloud / matplotlib / streamlit / kaggle
```
</details>

<details>
<summary><b>🔑 Step 3 — Set up Kaggle API</b></summary>
<br/>

> Login to Kaggle → Profile Icon → **Settings** → **API** → **Create New Token**

```bash
mkdir ~/.kaggle
cp kaggle.json ~/.kaggle/
chmod 600 ~/.kaggle/kaggle.json
```
</details>

<details>
<summary><b>📥 Step 4 — Download dataset + Run</b></summary>
<br/>

```bash
kaggle datasets download notshrirang/spotify-million-song-dataset
unzip spotify-million-song-dataset.zip
streamlit run app.py
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
    └── spotify_millsongdata.csv
```

---

## 🔮 Roadmap

```mermaid
timeline
    title 🎵 Music Recommender — Development Roadmap
    section Done ✅
        v1.0 : Lyrics preprocessing with NLTK
             : TF-IDF vectorization
             : Cosine similarity engine
             : Streamlit UI + WordCloud
    section Upcoming 🚧
        v1.1 : Fuzzy song name matching
             : Better not-found handling
        v1.2 : Spotify API integration
             : Album art + audio preview
    section Future 🔮
        v2.0 : Sentence-transformer embeddings
             : Hybrid lyrics + audio features
             : Docker deployment
```

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
