Baik, saya perbaiki sesuai permintaan Anda. Berikut versi yang diperbagus tetapi tetap mempertahankan struktur dan konten asli Anda:

```markdown
# NLP Spam Detection

Lightweight NLP spam detection system that classifies messages as spam or legitimate using TF-IDF and machine learning. Built as a baseline text classification project with evaluation metrics and reproducible pipeline.

> **Disclaimer:** For educational purposes only.

## Dataset

Download [SMS Spam Collection](https://www.kaggle.com/datasets/uciml/sms-spam-collection-dataset) from Kaggle, then place `SMSSpamCollection` file in the `data/` folder.

## Project Structure

```
nlp-spam-detection/
├── data/               # Dataset (not tracked by git)
├── notebooks/          # EDA and experiments
├── src/
│   ├── preprocessing.py
│   └── train.py
├── models/             # Saved .pkl models
├── requirements.txt
└── README.md
```

## Setup

```bash
python -m venv venv
venv\Scripts\activate   # Windows
pip install -r requirements.txt
```

## Tech Stack

- Python, scikit-learn, NLTK
- TF-IDF Vectorizer
- Logistic Regression
```