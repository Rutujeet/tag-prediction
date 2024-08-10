## Predict Tags on StackOverflow

This project predicts tags for StackOverflow titles using machine learning models. The dataset includes:

- **train.tsv**: Contains titles and associated tags.
- **test.tsv**: Contains titles for which we predict tags.
- **validation.tsv**: Similar to the train file but used for validation.

### Data Preprocessing

- Convert text to lowercase
- Remove non-textual characters, digits, and hashtags
- Tokenize words
- Remove stopwords
- Count words and tags

### Models

1. **Bag of Words**: Represents text as a multiset of words, ignoring grammar and word order but keeping word frequency.
2. **TF-IDF**: Enhances the bag-of-words model by accounting for word frequency across the dataset, reducing the weight of common words.

**Multi-class Classification**: Used `OneVsRestClassifier` with `LogisticRegression` (l1 and l2 penalties) for both models.

### Results

The best performance was achieved using TF-IDF with l1 penalty:

- **F1 (Micro) Score**: 0.6735

### Sample Predictions

Here are some predictions on the test set:

- "Warning: mysql_query() expects parameter 2 to be resource, object given" → ('mysql', 'php')
- "get click coordinates from <input type='image'> via javascript" → ('javascript',)
- "How to implement cloud storage for media assets in ZF?" → ()
- "What is catcomplete in jQuery's autocomplete plugin?" → ('javascript', 'jquery')
- "Error building Android app with Cordova 3.1 CLI" → ('android', 'java')

### Top Words for Tags

**c**
- Positive: printf, fscanf, malloc, scanf, c
- Negative: c #, php, javascript, java, python

**python**
- Positive: tkinter, matplotlib, numpy, pandas, python
- Negative: php, java, c, django python, jquery

**java**
- Positive: jtable, jar, hibernate, spring, java
- Negative: php, python, ruby, rails, django
