# Email Spam Detection 

## Description
A complete Natural Language Processing (NLP) pipeline that classifies emails as **Spam** or **Ham (Not Spam)**. The project covers the full lifecycle of an ML text classification problem  from raw text cleaning and TF-IDF feature extraction to training multiple classifiers, cross-validating them, and evaluating on a held out test set with industry-standard metrics.

## Dataset
- **Source:** Simulated dataset modelled after the [UCI SMS Spam Collection](https://archive.ics.uci.edu/ml/datasets/SMS+Spam+Collection)
- **Description:** 1,000 labelled messages (~87% ham, ~13% spam), reflecting the real-world class imbalance found in email/SMS datasets. Ham messages simulate everyday communication; spam messages include patterns common to phishing, prize scams, and unsolicited marketing.

## Steps Performed
1. **Data Loading** — Synthetic generation of a realistic labelled dataset
2. **Exploratory Data Analysis** — Class distribution, text length, and word count distributions visualised for spam vs ham
3. **Data Cleaning** — Lowercasing, URL / phone number / email masking with regex, punctuation removal, stopword filtering
4. **Feature Extraction** — TF-IDF vectorisation with unigrams + bigrams (`ngram_range=(1,2)`), top 5,000 features, `sublinear_tf=True`
5. **Model Training** — Naïve Bayes, Logistic Regression, and Linear SVM trained with 5-fold stratified cross-validation
6. **Evaluation** — Accuracy, Precision, Recall, F1-score, confusion matrix on a 20% held-out test set
7. **Inference Demo** — Real-time classification of new email strings

## Results
| Model | CV Accuracy | Test Accuracy |
|---|---|---|
| Naïve Bayes | ~0.96 | ~0.96 |
| Logistic Regression | ~0.97 | ~0.97 |
| Linear SVM | ~0.98 | ~0.98 |

- **Best model:** Linear SVM — highest precision and recall for spam class
- Spam emails reliably trigger on uppercase words, monetary amounts, and exclamation marks
- Class imbalance makes **Recall for Spam** the most critical production metric

## Tools Used
- Python 3.10+
- NumPy, Pandas
- Scikit-learn (TfidfVectorizer, MultinomialNB, LogisticRegression, LinearSVC, Pipeline)
- Matplotlib, Seaborn

## Conclusion
TF-IDF combined with a Linear SVM is a strong, fast baseline for spam detection that requires no deep learning. The project also highlights the importance of handling class imbalance and choosing the right evaluation metric (Recall over Accuracy) in safety critical classification tasks. Future work includes using BERT embeddings and deploying the classifier as a real-time email filtering microservice.

## Author
ATHARVA H SAWANT

