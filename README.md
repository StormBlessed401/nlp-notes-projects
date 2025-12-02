🛍️ Amazon Reviews Sentiment Analysis using TF-IDF & Machine Learning

This project performs sentiment analysis on Amazon product reviews using Natural Language Processing (NLP) and Machine Learning techniques.
The model classifies reviews into Positive or Negative sentiment based on the review text using TF-IDF vectorization and Logistic Regression.

📌 Project Objective

To build a machine learning pipeline that:

Cleans and preprocesses raw text data

Converts text into numerical features via TF-IDF

Trains a classification model

Evaluates the performance using classification metrics

Displays real predictions vs actual sentiment

📂 Dataset

The dataset consists of Amazon product reviews with the following relevant columns:

Score – Rating given by the user (1–5)

Text – Review text written by the user

🎯 Sentiment Mapping
Rating	Sentiment
4–5	Positive
1–2	Negative
3	Removed (Neutral excluded)
🧪 Data Preprocessing Steps

The following steps are applied to clean and prepare the data:

✅ Data Cleaning

Convert all text to lowercase

Remove punctuation, numbers, and extra spaces

Remove English stopwords using NLTK

Handle missing values (NaN, empty strings)

⚖ Data Balancing

The dataset is balanced so that both Positive and Negative reviews have equal samples

Prevents bias toward majority class

🔍 Feature Engineering

Text data is transformed into numerical vectors using:

🧠 TF-IDF (Term Frequency – Inverse Document Frequency)

This converts text into vectors that reflect:

How important a word is within a review

How rare it is across the dataset

Used with:

TfidfVectorizer(max_features=5000)

🤖 Model Training

The model used:

🔷 Logistic Regression

Why?

Fast and efficient for text classification

Performs well on linearly separable data

Easy to interpret

🔀 Train-Test Split

Dataset is split into:

80% Training

20% Testing

📊 Evaluation Metrics

The model is evaluated using:

Accuracy

Precision

Recall

F1-Score

Confusion Matrix

A classification report is printed showing performance for:

Negative Reviews

Positive Reviews

✅ Sample Output

The notebook prints:

Classification report

Confusion matrix

A few real prediction samples:

Example:

Review: "This product is amazing and works perfectly"
True Sentiment: Positive
Predicted: Positive

🛠 Tech Stack

Python

Pandas & NumPy

NLTK

Scikit-learn

Matplotlib & Seaborn

🏗 Project Structure
├── NLP_amazon_reviews_TF-IDF.ipynb   # Jupyter Notebook
├── README.md                        # Project documentation
└── dataset.csv                      # (Optional) Raw dataset file

▶ How to Run the Project
Step 1: Clone the repository
git clone https://github.com/yourusername/amazon-sentiment-analysis

Step 2: Install dependencies
pip install pandas numpy nltk scikit-learn matplotlib seaborn

Step 3: Download NLTK Stopwords (if not already in notebook)
import nltk
nltk.download('stopwords')

Step 4: Open the notebook
jupyter notebook


Then run:

NLP_amazon_reviews_TF-IDF.ipynb

🚀 Possible Improvements

Add deep learning models (LSTM / BERT)

Support neutral sentiment

Build a Flask / Streamlit web app for live predictions

Perform hyperparameter tuning

Add visualization dashboards

🎓 Learning Outcomes

From this project, you learn:

NLP preprocessing pipelines

TF-IDF mechanics

Supervised classification

Evaluation techniques

Real-world ML workflows
