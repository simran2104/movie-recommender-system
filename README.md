# 🎬 Movie Recommender System

A **content-based movie recommendation system** built with Python and Streamlit. The application recommends movies based on their similarity in plot, cast, director, keywords, and spoken language.

## 🌐 Demo

Try the live application:

👉 **[Movie Recommender System]()**

Select a movie and get recommendations based on its content and metadata.

## 📌 Project Overview

This project uses the **TMDB Movies Daily Updates** dataset from Kaggle to build a content-based movie recommendation system.

Movie information such as the overview, cast, director, keywords, and spoken language is combined into a single `tags` feature. The tags are converted into numerical vectors using **CountVectorizer**, and movie similarity is used to generate recommendations.

The final model is integrated into an interactive **Streamlit web application**.

## 🔄 How It Works

```text
Movie Dataset
     ↓
Data Cleaning & Preprocessing
     ↓
Feature Engineering
     ↓
Create Movie Tags
     ↓
CountVectorizer
     ↓
Movie Vectors
     ↓
Similarity Calculation
     ↓
Movie Recommendations
     ↓
Streamlit Web App
```

## ✨ Features

* 🎬 Select a movie and get similar movie recommendations
* 🔎 Content-based movie similarity
* 📝 Uses movie overview, cast, director, keywords, and language
* 🤖 Bag of Words text vectorization
* 🌐 Interactive Streamlit web application

## 🛠️ Technologies Used

* **Python**
* **Pandas** – Data manipulation and preprocessing
* **NumPy** – Numerical operations
* **Scikit-learn** – Text vectorization and similarity
* **Streamlit** – Web application
* **Jupyter Notebook** – Development and experimentation

## 📊 Dataset

The project uses the **TMDB Movies Daily Updates** dataset provided by **Alan Vourch** on Kaggle.

[TMDB Movies Daily Updates Dataset](https://www.kaggle.com/datasets/alanvourch/tmdb-movies-daily-updates?utm_source=chatgpt.com)

## 🎯 Goal

The goal of this project was to build an end-to-end machine learning application, from **data preprocessing and feature engineering to recommendation generation and web deployment**.

## 📚 What I Learned

* Data cleaning and preprocessing
* Feature engineering
* Natural Language Processing
* Bag of Words
* Text vectorization
* Content-based recommendation systems
* Vector similarity
* Building ML-powered web applications
* Deploying applications with Streamlit
