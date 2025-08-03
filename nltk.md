 What is NLTK?
NLTK stands for Natural Language Toolkit — it’s a Python library used for working with human language data (text). It's one of the most widely used libraries for basic NLP tasks.

🔹 What can it do?
Once you've imported nltk, you can use it for:

Tokenization (splitting text into words/sentences)

Stopword removal (removing common words like "the", "is", "and")

Stemming/Lemmatization (reducing words to root form, e.g., "running" → "run")

Part-of-speech tagging

Text classification

and much more.

🔹 Example:
from nltk.corpus import stopwords
nltk.download('stopwords')

stop_words = set(stopwords.words('english'))
This code removes common English stopwords from your text like "is", "a", "the", etc.

