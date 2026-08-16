# Jordanian Arabic Dialect Classification

## Project Overview

This project develops a machine learning model to classify Jordanian Arabic text into one of four regional dialects:

* Ammani
* Fallahi
* Madani
* Bedouin

The model uses character-level TF-IDF features combined with a Linear Support Vector Machine (LinearSVC), which is well suited for dialect identification due to its effectiveness on sparse text features.

---

## Dataset

The dataset was **self-collected specifically for this project**. It consists of Arabic text samples labeled according to one of four Jordanian regional dialects:

* Ammani
* Fallahi
* Madani
* Bedouin

The data was collected and organized manually rather than being obtained from a standard benchmark dataset.

Main preprocessing steps include:

* Removing duplicate samples
* Handling missing values
* Normalizing Arabic characters
* Removing unwanted symbols
* Cleaning whitespace
* Standardizing dialect labels

---

## Preprocessing

Text preprocessing includes:

* Unicode normalization
* Arabic letter normalization
* Removal of punctuation
* Removal of non-Arabic symbols
* Whitespace normalization

The cleaned text is stored in:

```text
text_clean
```

---

## Feature Extraction

Character-level TF-IDF was used with:

* Analyzer: `char_wb`
* N-grams: `(2,5)`
* Maximum features: `50000`
* Sublinear TF scaling enabled

Character n-grams generally perform well for dialect identification because they capture spelling variations, character patterns, and local linguistic characteristics that can distinguish regional dialects.

---

## Model

Classifier:

```text
LinearSVC
```

Parameters:

* `class_weight = balanced`
* `max_iter = 2000`

Hyperparameter tuning was performed using GridSearchCV to optimize the regularization parameter (`C`).

---

## Evaluation

The model was evaluated using:

* Accuracy
* Precision
* Recall
* F1-score
* Confusion Matrix
* ROC-AUC Curve (One-vs-Rest)
* **Prediction confidence scores**

Confidence scores are calculated to indicate how strongly the model favors the predicted dialect compared with the alternative classes.

---

## Results

The final model achieved approximately:

* **Accuracy: 84.4%**
* **Macro F1-score: 83%**

The model performed particularly well on the Ammani dialect, while some confusion occurred between linguistically similar dialects, especially Fallahi and Karaki.

The training accuracy was approximately **99.5%**, compared with **84.4%** on the test set, indicating a noticeable degree of overfitting. However, the model maintained reasonable performance across all four dialect classes.

Prediction confidence scores were also calculated to provide an additional indication of how strongly the model supported each dialect prediction.

---

## Project Structure

```text
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

1. Load the self-collected dataset.
2. Clean and preprocess the text.
3. Split the data into training and testing sets.
4. Extract TF-IDF character n-gram features.
5. Train the LinearSVC model.
6. Perform hyperparameter tuning.
7. Evaluate the model on the held-out test set.
8. Calculate prediction confidence scores.
9. Visualize the confusion matrix and ROC curve.

---

## Future Improvements

* Fine-tune AraBERT for dialect classification.
* Experiment with FastText embeddings.
* Address class imbalance using augmentation techniques.
* Compare classical machine learning models with transformer-based models.
* Expand the self-collected dataset to improve generalization and reduce overfitting.

---

## Author

Jordanian Arabic Dialect Classification Project
