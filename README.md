# NLP Spam Detection

Lightweight spam detection system that classifies SMS messages as spam or ham using TF-IDF and Logistic Regression. Built as a reproducible baseline for text classification with proper evaluation metrics.

> **Disclaimer:** For educational purposes only.

---

## Results

| Metric | Ham | Spam |
|--------|-----|------|
| Precision | 0.99 | 0.88 |
| Recall | 0.98 | 0.92 |
| F1-score | 0.98 | **0.90** |
| Accuracy (overall) | | **0.97** |

> F1-score is used as the primary metric due to class imbalance (87% ham, 13% spam).

---

## Dataset

Download [SMS Spam Collection](https://www.kaggle.com/datasets/uciml/sms-spam-collection-dataset) from Kaggle, then place the CSV file in the `data/` folder:

```
data/
└── SMS Spam Collection Dataset.csv
```

---

## Project Structure

```
nlp-spam-detection/
├── data/                          # Dataset (not tracked by git)
├── notebooks/
│   ├── 01_eda.ipynb               # Exploratory data analysis
│   ├── 02_preprocessing.ipynb     # Text cleaning pipeline
│   ├── 03_train.ipynb             # Model training & evaluation
│   ├── 04_save_model.ipynb        # Export model to .pkl
│   └── 05_demo.ipynb              # Interactive prediction demo
├── models/
│   ├── spam_classifier.pkl        # Trained Logistic Regression model
│   └── tfidf_vectorizer.pkl       # Fitted TF-IDF vectorizer
├── requirements.txt
└── README.md
```

---

## Setup

```bash
# Clone the repository
git clone https://github.com/your-username/nlp-spam-detection.git
cd nlp-spam-detection

# Create and activate virtual environment
python -m venv venv
venv\Scripts\activate        # Windows
source venv/bin/activate     # macOS/Linux

# Install dependencies
pip install -r requirements.txt
```

---

## Usage

Run notebooks in order:

```
01_eda.ipynb           → Understand the dataset
02_preprocessing.ipynb → Clean and prepare text
03_train.ipynb         → Train and evaluate the model
04_save_model.ipynb    → Save model to models/
05_demo.ipynb          → Try predictions interactively
```

Or load the saved model directly:

```python
import pickle

with open('models/tfidf_vectorizer.pkl', 'rb') as f:
    tfidf = pickle.load(f)

with open('models/spam_classifier.pkl', 'rb') as f:
    model = pickle.load(f)

# Predict
text = ["Congratulations! You've won a FREE prize. Call now!"]
vec = tfidf.transform(text)
print(model.predict(vec))  # [1] = spam, [0] = ham
```

---

## Pipeline

```
Raw text
  → Lowercase + remove symbols/numbers
  → Remove stopwords
  → Stemming (Porter Stemmer)
  → TF-IDF vectorization (5000 features, unigram + bigram)
  → Logistic Regression (class_weight='balanced')
  → Spam / Ham
```

---

## Tech Stack

- Python 3.x
- scikit-learn — TF-IDF, Logistic Regression, metrics
- NLTK — stopwords, stemming
- pandas, matplotlib, seaborn

---

## Limitations

- Trained on English SMS data from 2005 — may underperform on modern phishing patterns
- Weak on context-aware spam (e.g. URLs, social engineering without trigger keywords)
- Not suitable for Indonesian/multilingual spam without retraining