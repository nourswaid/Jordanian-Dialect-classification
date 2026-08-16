# Jordanian Arabic Dialect Classification

## Project Overview

This project develops a machine learning model to classify Jordanian Arabic text into one of four regional dialects:

- Ammani
- Fallahi
- Madani
- Bedouin

The model uses character-level TF-IDF features combined with a Linear Support Vector Machine (LinearSVC), which is well suited for dialect identification due to its effectiveness on sparse text features.

---

## Dataset

The dataset contains Arabic text samples labeled with one of the four Jordanian dialects.

Main preprocessing steps include:

- Removing duplicate samples
- Handling missing values
- Normalizing Arabic characters
- Removing unwanted symbols
- Cleaning whitespace
- Standardizing dialect labels

---

## Preprocessing

Text preprocessing includes:

- Unicode normalization
- Arabic letter normalization
- Removal of punctuation
- Removal of non-Arabic symbols
- Whitespace normalization

The cleaned text is stored in:

```
text_clean
```

---

## Feature Extraction

Character-level TF-IDF was used with:

- Analyzer: `char_wb`
- N-grams: `(2,5)`
- Maximum features: `50000`
- Sublinear TF scaling enabled

Character n-grams generally perform better than word features for dialect identification because they capture spelling variations and local linguistic patterns.

---

## Model

Classifier:

```
LinearSVC
```

Parameters:

- class_weight = balanced
- max_iter = 2000

Hyperparameter tuning was performed using GridSearchCV to optimize the regularization parameter (C).

---

## Evaluation

The model was evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix
- ROC-AUC Curve (One-vs-Rest)

---

## Results

The final model achieved approximately:

- Accuracy: **84.4%**

The confusion matrix shows that most dialects are classified correctly, with some overlap between linguistically similar dialects.

---

## Project Structure

```
project/
│
├── pattern.ipynb
├── FullData.xlsx
├── README.md
└── requirements.txt
```

---

## Required Libraries

```bash
pip install pandas numpy scikit-learn matplotlib seaborn openpyxl
```

---

## Running the Project

1. Load the dataset.
2. Clean and preprocess the text.
3. Split the data into training and testing sets.
4. Extract TF-IDF character n-gram features.
5. Train the LinearSVC model.
6. Perform hyperparameter tuning.
7. Evaluate the model.
8. Visualize the confusion matrix and ROC curve.

---

## Future Improvements

- Fine-tune AraBERT for dialect classification.
- Experiment with FastText embeddings.
- Address class imbalance using augmentation techniques.
- Compare classical machine learning models with transformer-based models.

---

## Author

Jordanian Arabic Dialect Classification Project
