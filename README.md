# 🎬 Movie Recommender System

A **content-based movie recommender system** that recommends movies based on the similarity of their content and metadata.

The project takes movie information such as plot overview, cast, director, spoken language and keywords, processes this information into a combined **tags** representation, converts the text into numerical vectors, and uses vector similarity to identify movies with similar characteristics.

---

## 📌 Project Overview

Recommendation systems are widely used by platforms such as Netflix, YouTube and Spotify to help users discover relevant content.

There are three common types of recommender systems:

### 1. Content-Based Recommender

Recommends items based on the characteristics of items that a user has previously shown interest in.

For movies, recommendations can be based on attributes such as:

* Genre
* Plot / overview
* Cast
* Director
* Keywords
* Language

#### 2. Collaborative Filtering

Recommends items based on the behaviour of similar users.

The system identifies users with similar preferences and recommends content that similar users have interacted with or enjoyed.

#### 3. Hybrid Recommender

Combines both:

* Content-based filtering
* Collaborative filtering

This project currently implements a **Content-Based Recommender System**.

---

## 📊 Dataset

The project uses the **TMDB Movies Daily Updates** dataset available on Kaggle.

**Dataset:** TMDB Movies Daily Updates
**Source:** Alan Vourch

Dataset link:

https://www.kaggle.com/datasets/alanvourch/tmdb-movies-daily-updates

The dataset contains movie-related information including:

* Movie title
* Release date
* IMDb ID
* Movie overview
* Spoken languages
* Cast
* Other movie metadata

The original dataset contains approximately **1.23 million movie records and 30 columns**.

For this recommender system, only the features useful for content-based recommendation are retained.

---

## 🔄 Project Flow

```text
Dataset
   ↓
Data Cleaning
   ↓
Data Pre-processing
   ↓
Feature Engineering
   ↓
Create Movie Tags
   ↓
Text Vectorization
   ↓
Movie Vectors
   ↓
Calculate Similarity
   ↓
Recommend Similar Movies
   ↓
Web Application
   ↓
Deployment
```

---

## 🧹 Data Cleaning & Pre-processing

The original dataset contains many columns and a significant amount of missing data.

The first step was to select the features that are useful for the recommendation system:

```text
title
release_date
imdb_id
overview
spoken_languages
cast
director
keywords
popularity
```

The original dataset was reduced from 30 columns to these relevant features.

#### Missing Values

Missing values were handled during preprocessing.
Duplicate records were also checked.


---

## 🏷️ Creating Movie Tags

The main idea behind this project is to represent each movie using a single text field called **`tags`**.

The following information is combined:

```text
Overview
+
Spoken Languages
+
Cast
+
Director
+
Keywords
```

This produces a single textual representation of each movie.

For example:

```text
Movie
  ↓
Overview
Spoken Language
Cast
Director
Keywords
  ↓
Combined
  ↓
Tags
```

The project creates a new dataset containing:

```text
title
imdb_id
tags
```

An example of the resulting `tags` field contains information about the movie's story, language, actors, director and keywords.

## 🔢 Text Vectorization

Machine learning algorithms cannot directly work with raw text.

Therefore, the movie tags need to be converted into numerical vectors.

The basic idea is:

```text
Movie Tags
     ↓
Text Vectorization
     ↓
Numerical Vector
     ↓
Represent Movie in Vector Space
```

Different text vectorization techniques can be used, including:

* Bag of Words
* TF-IDF
* Word Embeddings
* Transformer-based embeddings

This project currently uses **Bag of Words** through Scikit-learn's `CountVectorizer`.

---

## 🛍️ Bag of Words

The **Bag of Words (BoW)** approach represents text based on the frequency of words.

For example:

```text
Movie A:
"action hero adventure"

Movie B:
"action hero comedy"
```

The vocabulary could be:

```text
action
adventure
comedy
hero
```

The movies can then be represented as numerical vectors:

```text
Movie A → [1, 1, 0, 1]
Movie B → [1, 0, 1, 1]
```

Each movie therefore becomes a point in a high-dimensional vector space.

Movies with similar content should have similar vectors.

---

## 🔤 CountVectorizer

The project uses:

```python
from sklearn.feature_extraction.text import CountVectorizer
```

A `CountVectorizer` is configured to:

* Keep the most relevant words/features
* Remove English stop words
* Ignore very rare words

Current configuration:

```python
CountVectorizer(
    max_features=10000,
    stop_words='english',
    min_df=5
)
```

### Why remove stop words?

Words such as:

```text
the
a
an
in
is
are
to
```

usually provide little information about what makes one movie different from another.

Removing these words allows the model to focus more on meaningful terms.

### Feature Selection

The current implementation keeps up to **10,000 features** and ignores words appearing in fewer than 5 documents.

This produces a movie-feature matrix where:

```text
Rows    → Movies
Columns → Words / Features
Values  → Number of times a word appears
```

Conceptually:

```text
             action  comedy  hero  horror  ...
Movie 1         2       0      1      0
Movie 2         1       2      0      0
Movie 3         0       0      1      3
...
```

The resulting vectors are then used to determine similarity between movies.

---

## 📐 Movie Similarity

Once every movie has been converted into a vector, movies can be compared based on the similarity between their vectors.

Conceptually:

```text
Movie A → Vector A
Movie B → Vector B
Movie C → Vector C
Movie D → Vector D

             ↓

       Similarity Calculation

             ↓

Movies with the closest vectors
             ↓
       Recommended Movies
```

The recommendation system therefore finds movies whose vector representations are closest to the selected movie.

---

## 🚧 Current Project Status

### Completed

* [x] Dataset downloaded from Kaggle
* [x] Initial dataset exploration
* [x] Feature selection
* [x] Missing-value handling
* [x] Duplicate checking
* [x] Date preprocessing
* [x] Text preprocessing
* [x] Cast/director/keyword preprocessing
* [x] Created combined `tags` feature
* [x] Created cleaned movie dataset
* [x] Implemented Bag of Words
* [x] Implemented `CountVectorizer`
* [x] Generated movie vectors

### Next Steps

* [ ] Calculate movie-to-movie similarity
* [ ] Implement recommendation function
* [ ] Test recommendation quality
* [ ] Build web interface
* [ ] Connect the recommendation model to the website
* [ ] Deploy the application

---

## 🛠️ Technologies Used

* **Python**
* **Pandas** - Data manipulation and preprocessing
* **NumPy** - Numerical operations
* **Scikit-learn** - Text vectorization and machine learning
* **Jupyter Notebook** - Development and experimentation
* **Kaggle** - Dataset source

---

## 🎯 Goal

The goal of this project is to understand how a **content-based recommendation system** works from end to end:

```text
Raw Data
   ↓
Data Cleaning
   ↓
Feature Engineering
   ↓
Text Processing
   ↓
Vectorization
   ↓
Similarity Calculation
   ↓
Movie Recommendation
   ↓
Web Application
```

This project also demonstrates how machine learning techniques can be integrated into a software application rather than being used only inside a notebook.

---

## 📚 Learning Outcomes

Through this project, I am exploring:

* Data cleaning and preprocessing
* Feature engineering
* Natural Language Processing
* Bag of Words
* Text vectorization
* Content-based recommendation systems
* Vector similarity
* Building ML-powered applications
* Deploying machine learning models as web applications

---

## 📌 Dataset Attribution

This project uses the **TMDB Movies Daily Updates** dataset provided by Alan Vourch on Kaggle.

Dataset:
https://www.kaggle.com/datasets/alanvourch/tmdb-movies-daily-updates

Please refer to the original dataset page for its licensing and usage terms.
