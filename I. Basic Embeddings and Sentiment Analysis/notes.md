# What did I cover

Simple NLP use case - Sentiment Analysis

1.  Preprocessing / Data Cleaning:
    -   Remove noise - empty spaces, numbers, punctuation, etc.
    -   Remove stop words like 'is', 'a', etc.
    -   Lowercase all words to ensure `He` and `he` are treated the same
    -   Stemming:
        -   Arrive at Base word - May/May not contain meaning
        -   Finally, Finale, Finalised -> Fina
        -   Used for Spam Detection etc - meaning need not be retained
    -   Lemmatization:
        -   Understand the meaning and then arrive to a base word
        -   Finally, Finale, Finalised -> Final
        -   Used for chatbots etc - meaning needs to be preserved
2.  Create Embeddings
    -   CountVectorizer / BagOfWords:
        -   simply consider each unique word in context as feature and assign 0/1 to indicate presence while handling each sentence
    -   TF-IDF:
        -   Identify keywords and hence weigh each word's importance
    -   Word2Vec:
        -   Learns dense word vectors (predictive neural approach); notebook averages word vectors to form sentence embeddings
3.  Do Classifier with given n-dimensional input features and encoded output feature
    -   `LogisticRegression` (used in the notebook)

---

Notebook specifics:

- Dataset source: `mdismielhossenabir/sentiment-analysis` (loaded via `kagglehub`).
- NLTK: downloaded `stopwords` and `wordnet` for preprocessing.
- Preprocessing used: lowercase, remove punctuation (`re.sub`), tokenize by split, remove NLTK `STOP_WORDS`, then lemmatize with `WordNetLemmatizer`.
- Label encoding: `positive` -> `1`, `negative` -> `-1`; dropped NA and cast to `int`.
- Encoders tested: `CountVectorizer`, `TfidfVectorizer`, and `Word2Vec` (Word2Vec params: `vector_size=300`, `window=5`, `min_count=1`, `epochs=20`).
- Classifier used in notebook: `LogisticRegression` (train/test split `test_size=0.2`).

- Dataset load: selected columns `text` and `sentiment` when loading the CSV via `kagglehub`.
- The preprocessing function is applied with `df["text"] = df["text"].apply(preprocess_text)`.
- Encoder outputs: `CountVectorizer`/`TfidfVectorizer` return sparse matrices; `Word2Vec` returns a dense `numpy` array of averaged word vectors.
- Evaluation: notebook prints `accuracy_score` and `classification_report` (target names `['negative','positive']`).
