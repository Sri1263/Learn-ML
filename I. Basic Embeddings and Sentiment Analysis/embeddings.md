# Embedding basics

    Embeddings are numerical representations of text specially used in NLP

### NLP Use Cases
- Text Classification
- NER
- Text Similarity/Analogy
- Q & A

Pre-processing text 
- tokenization
- removing stopwards and punctuation
- sliding context window - identify contexts and words - to learn word relationships
- Model is trained to predict the word bassed on context - positioning semantically similar words together

---
![Image](https://cdn.analyticsvidhya.com/wp-content/uploads/2025/04/01-image38.webp)
---

## Embedding Methods

### 1. **Frequency Based Embeddings**:

- *Idea*: significance of word depends on how frequently it occurs in the text

    #### One Hot Encoding:
    - For a vocabulary of size \(N\), each word is represented by a vector of length \(N\), with a '1' at the index of the word and '0' everywhere else.
    #### Bag Of Words:
    - A vector of length \(N\) (vocabulary size) where each position \(i\) contains the count (or occurrence) of the \(i\)-th word in the document.
    #### TF-IDF - Term Frequency Inverse Document Frequency:
    - highlights words specific to context rather than context [words like 'a', 'the' will have low TF-IDF scores]

### 2. **Prediction Based Embeddings**:
- Captures semantic relationships between words
- understands that 'dog' might be used with words like 'tail' or 'bark'

    #### Word2Vec [Google 2013]
    -   Converts text into numerical vectors that capture semantic and syntactic meaning (e.g., enabling calculations like `(king-man+woman)~queen` )
    1. *CBOW*:
        Continuous Bag Of Words - Predicts Target word based on surrounding Context words
    2. *SKIP-GRAM*:
        Predics Context words based on given target word

    #### GLOVE [Stanford Univ 2014]
    -   Global Vectors for Word Representation
    -   Uses co-occurence statistics to create word vectors
    -   How often do words appear together - create relationships

3. **Contextual Based Embedding**:
- Traditional Word Embeddings assign fixed Vectors to Words, these assign vectors based on context
- Makes it possible to give 'Bank' diff embeddings in 'Bank of River' and 'Withdrawing from Bank'


---

Sources
-   [What are Word Embeddings? - IBM Tech](https://www.youtube.com/watch?v=wgfSDrqYMJ4&list=TLPQMDcwMjIwMja6LdqtehyYcQ&index=2)