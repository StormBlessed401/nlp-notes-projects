
#  TF-IDF: Term Frequency – Inverse Document Frequency

TF-IDF is a technique to evaluate how **important** a word is in a **document**, relative to a **collection of documents** (corpus).

---

## Formula (at a glance)

```
TF-IDF = TF * IDF
```

---

## 1. Term Frequency (TF)
**What it tells:**  
How *frequently* a word appears in a single document.

**Formula:**

```
TF(word) = (Number of times word appears in document) / (Total words in document)
```

**Example:**

- Document: "Python is great. Python is easy."  
- TF("Python") = 2 / 6 = **0.33**

---

## 2. Inverse Document Frequency (IDF)
**What it tells:**  
How *rare or unique* the word is across **all** documents.

**Formula:**

```
IDF(word) = log_e (Total number of documents / Number of documents with the word)
```

But the formula goes through a slight change that is adding +1 to the actual idf:
<img width="1153" height="286" alt="image" src="https://github.com/user-attachments/assets/8d9d8c51-e877-4aaa-9a7c-f2730d24d67b" />

**Example:**

- "the" appears in every document → IDF ≈ 0  
- "TF-IDF" appears only in 1 document out of 100 → IDF ≈ high

---

## Final Meaning of TF-IDF

- High **TF** → word is important in this doc  
- High **IDF** → word is unique in the corpus  

✅ So **high TF-IDF = important and unique word**  
❌ Low TF-IDF = either common or not important

---

## Example

### 3 documents:

```
Doc1: "Python is great"
Doc2: "Python is easy"
Doc3: "Java is great"
```

Compute TF-IDF for “Python” in Doc1:

- TF = 1/3 = 0.33  
- IDF = log(3 / 2) ≈ 0.18  

**TF-IDF = 0.33 * 0.18 ≈ 0.06**

→ "Python" is important but not unique.

---

## Applications of TF-IDF

- **Keyword extraction**
- **Search engines**
- **Stopword filtering**
- **Text classification** and **Sentiment analysis**

---

## Limitations

- Doesn’t capture **context or meaning**
- Ignores **word order**
- Weak with **short texts**
- Doesn’t understand **synonyms**

For better understanding, explore **Word2Vec**, **BERT**, etc.

---

## Quick Python Code (with scikit-learn)

```python
from sklearn.feature_extraction.text import TfidfVectorizer

docs = ["Python is great", "Python is easy", "Java is great"]
vectorizer = TfidfVectorizer()
tfidf_matrix = vectorizer.fit_transform(docs)

print(vectorizer.get_feature_names_out())
print(tfidf_matrix.toarray())
```

Working example of TF-IDF and how to calculate TF and IDF individually and multiplying them together:

<img width="1183" height="548" alt="image" src="https://github.com/user-attachments/assets/a21ba76b-0483-4444-92b3-d3825f5c4902" />

<img width="1121" height="240" alt="image" src="https://github.com/user-attachments/assets/4f776b5d-cc12-4b2c-bae0-556187579fe2" />







