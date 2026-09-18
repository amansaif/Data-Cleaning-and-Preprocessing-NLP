# 🧹 Data Cleaning and Preprocessing for NLP

A beginner-friendly Natural Language Processing (NLP) project demonstrating common **text data cleaning and preprocessing techniques using Python and NLTK**.

The notebook shows how raw text can be cleaned and transformed into useful tokens for further NLP tasks.

## 📌 Project Overview

Text data collected from real-world sources often contains unnecessary punctuation, common words, spelling mistakes, and unstructured sentences.

This project demonstrates a basic preprocessing pipeline that includes:

* Word Tokenization
* Sentence Tokenization
* Punctuation Removal
* Stop Word Removal
* Spelling Correction using `pyspellchecker`
* Spelling Correction using `TextBlob`
* Combining preprocessing techniques into a single function

## 🛠️ Technologies & Libraries

* **Python**
* **NLTK**
* **pyspellchecker**
* **TextBlob**
* **Jupyter Notebook / Google Colab**

## 📂 Project Structure

```text
Data-Cleaning-and-Preprocessing/
│
├── 2401201145_Data_Cleaning_and_Preprocessing.ipynb
└── README.md
```

## 🔍 Preprocessing Techniques

### 1. Word Tokenization

Word tokenization divides text into individual words and punctuation marks called **tokens**.

Example:

```text
Input:
Ram is a good cook, but he can't make pulses.

Output:
['Ram', 'is', 'a', 'good', 'cook', ',', 'but', 'he', 'ca', "n't", 'make', 'pulses', '.']
```

Implemented using:

```python
word_tokenize()
```

---

### 2. Sentence Tokenization

Sentence tokenization divides a paragraph or document into individual sentences.

Example:

```text
Input:
Ram is a good cook.
He is only 18 years old.

Output:
[
    'Ram is a good cook.',
    'He is only 18 years old.'
]
```

Implemented using:

```python
sent_tokenize()
```

---

### 3. Removing Punctuation

Punctuation marks such as:

```text
! ? , . ^ % # $ & *
```

can be removed when they are not useful for a particular NLP task.

The project uses Python's `string.punctuation` to identify punctuation characters.

---

### 4. Stop Word Removal

Stop words are very common words that may provide limited useful information for some NLP tasks.

Examples include:

```text
is
a
but
he
the
and
```

The project uses NLTK's English stop-word list.

```python
from nltk.corpus import stopwords

stopwords.words('english')
```

---

### 5. Spelling Correction with `pyspellchecker`

Real-world text can contain spelling mistakes.

For example:

```text
i havv a gud, bd, and ugly situton
```

The `pyspellchecker` library is used to identify and correct misspelled words.

```python
from spellchecker import SpellChecker
```

---

### 6. Spelling Correction with TextBlob

The project also demonstrates spelling correction using **TextBlob**.

Example:

```text
Input:
i havv bot godd fod

Output:
I have got good food
```

Implemented using:

```python
from textblob import TextBlob
```

---

## 🔄 Complete Preprocessing Pipeline

The notebook combines several preprocessing operations into a single function:

```text
Raw Text
   ↓
Tokenization
   ↓
Spelling Correction
   ↓
Punctuation Removal
   ↓
Stop Word Removal
   ↓
Cleaned Tokens
```

The main function is:

```python
def preprocess_text(text):
    tokens = word_tokenize(text)

    tokens = [
        spell.correction(word) if spell.correction(word) else word
        for word in tokens
    ]

    tokens = [
        word for word in tokens
        if word not in string.punctuation
    ]

    tokens = [
        word for word in tokens
        if word.lower() not in stopwords.words('english')
    ]

    return tokens
```

### Example

**Original text:**

```text
Ram is a gud cook, but he can't makke pulses!!
```

The preprocessing function converts the raw sentence into a cleaner collection of tokens.

## ⚙️ Installation

Install the required libraries using:

```bash
pip install nltk
pip install pyspellchecker
pip install textblob
```

Then download the required NLTK resources:

```python
import nltk

nltk.download('punkt')
nltk.download('punkt_tab')
nltk.download('stopwords')
```

## ▶️ How to Run

### Using Google Colab

1. Open the `.ipynb` file in Google Colab.
2. Run the installation cells.
3. Run the NLTK download cells.
4. Execute the notebook cells sequentially.
5. Observe the output of each preprocessing technique.

### Using Jupyter Notebook

Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
```

Navigate to the project directory:

```bash
cd Data-Cleaning-and-Preprocessing
```

Open the notebook:

```bash
jupyter notebook
```

Then run:

```text
2401201145_Data_Cleaning_and_Preprocessing.ipynb
```

## 🎯 Learning Objectives

This project helps demonstrate:

* How raw text is converted into tokens
* How sentences can be separated from paragraphs
* How punctuation can be removed
* How stop words can be filtered
* How spelling mistakes can be corrected
* How multiple preprocessing operations can be combined into an NLP pipeline
* Basic use of Python NLP libraries

## 🚀 Possible Future Improvements

The preprocessing pipeline can be extended with:

* Lowercasing
* Stemming
* Lemmatization
* Regular-expression based cleaning
* Removing URLs and email addresses
* Removing emojis and special characters
* Named Entity Recognition (NER)
* Part-of-Speech (POS) tagging
* TF-IDF vectorization
* Word embeddings
* Sentiment analysis

## 📚 Use Cases

Text preprocessing is commonly used before tasks such as:

* 💬 Sentiment Analysis
* 📰 Text Classification
* 🤖 Chatbots
* 🔎 Search Engines
* 📄 Document Classification
* 🧠 Machine Learning for NLP
* 📊 Text Analytics

## 👨‍💻 Author

**Mohd Aman**

BCA | Artificial Intelligence & Data Science

---

⭐ If you find this project useful, consider giving the repository a star!
