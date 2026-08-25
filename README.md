# SQL Injection and XSS Detection Model

## Model Overview

This project provides a deep learning model for classifying HTTP request payloads into three categories:

- **Normal**
- **SQL Injection (SQLi)**
- **Cross-Site Scripting (XSS)**

The final model uses a **Bidirectional Long Short-Term Memory (Bi-LSTM)** architecture to learn sequential patterns within web request payloads.

Bi-LSTM processes sequences in both forward and backward directions, allowing the model to capture contextual and structural relationships in payloads more effectively than a standard unidirectional LSTM.

---

## Dataset

The dataset used for model development was obtained from publicly available datasets on **Kaggle**.

The dataset contains web application payload samples representing three classes:

- Normal
- SQL Injection
- Cross-Site Scripting (XSS)

The payloads were used to train the model to learn relationships between input sequences and their corresponding attack labels.

For the model comparison experiment, the dataset was divided into:

- **Training Set: 80%**
- **Testing Set: 20%**

Training, validation, and testing data were used to support model training, hyperparameter adjustment, early stopping, and final performance evaluation.

---

## Data Preprocessing

Before training, raw payload data was transformed into a format suitable for the neural network.

### 1. Data Classification

Payloads were classified into:

```text
Normal
SQL Injection
Cross-Site Scripting (XSS)
```

Irrelevant data was filtered to keep the dataset aligned with the classification task.

### 2. Data Cleaning

Raw payloads may contain noisy or unnecessary information.

Data cleaning was performed using techniques including **Regular Expressions (Regex)** to remove selected unwanted elements and normalize the input before training.

### 3. Data Annotation

Each payload was assigned one of three labels:

```text
Normal
SQL Injection
XSS
```

### 4. Tokenization

The cleaned payload text was transformed into numerical token sequences using a tokenizer.

### 5. Sequence Encoding and Padding

Tokenized payloads were converted into numerical sequences and padded to a fixed maximum length:

```text
max_len = 40
```

This ensures a consistent input shape for the model.

---

## Model Architecture

The final architecture is based on a **Bidirectional Long Short-Term Memory (Bi-LSTM)** network.

```text
Input Payload
      │
      ▼
Tokenizer
      │
      ▼
Sequence Encoding
      │
      ▼
Padding (max_len = 40)
      │
      ▼
Embedding Layer
      │
      ▼
SpatialDropout1D
      │
      ▼
Bidirectional LSTM
      │
      ▼
GlobalMaxPooling1D
      │
      ▼
Dropout
      │
      ▼
Dense + Softmax
      │
      ▼
Normal / SQLi / XSS
```

### Embedding Layer

The embedding layer converts token IDs into dense numerical vectors.

```text
Vocabulary Size: 4,000
Embedding Dimension: 128
```

### SpatialDropout1D

SpatialDropout1D is used to reduce overfitting by randomly dropping portions of the embedding features during training.

### Bidirectional LSTM

The core layer is a **Bidirectional LSTM**.

```text
Forward  →→→
Backward ←←←
```

The outputs from both directions are combined so the model can learn contextual relationships from both sides of the sequence.

```text
LSTM Units: 64
```

### GlobalMaxPooling1D

GlobalMaxPooling1D extracts the strongest features learned across the sequence and reduces the dimensionality of the model output.

### Dropout

A dropout layer is used to reduce overfitting.

```text
Dropout Rate: 0.5
```

### Dense Classification Layer

The final Dense layer uses **Softmax** activation to generate a probability distribution across the three classes:

```text
Normal
SQL Injection
XSS
```

---

## Model Parameters

| Parameter | Value | Description |
|---|---:|---|
| `vocab_size` | 4000 | Maximum vocabulary size |
| `max_len` | 40 | Maximum input sequence length |
| `embedding_dim` | 128 | Embedding vector dimension |
| `lstm_units` | 64 | Number of LSTM units |
| `dropout` | 0.5 | Dropout rate |

---

## Training Configuration

| Parameter | Value |
|---|---:|
| Epochs | 10 |
| Batch Size | 64 |
| Cross-validation Folds | 5 |
| Early Stopping Patience | 3 |
| Reduce LR Patience | 2 |
| Reduce LR Factor | 0.5 |
| Selective Prediction Target Reject | 0.10 |

---

## Stratified K-Fold Cross Validation

The model was evaluated using **Stratified 5-Fold Cross Validation**.

```text
Number of folds = 5
```

Stratification was used to preserve the class distribution across folds.

For each fold:

1. Divide the dataset into training and validation subsets.
2. Convert payload text to token sequences.
3. Apply padding.
4. Calculate class weights to reduce the effect of class imbalance.
5. Train the model using Early Stopping and Reduce Learning Rate on Plateau.
6. Evaluate the model on validation data.
7. Record model performance for comparison.

---

## Handling Class Imbalance

Class weights were calculated during training to reduce the impact of class imbalance.

This helps prevent the model from becoming overly biased toward the majority class.

---

## Early Stopping

Early Stopping was used to reduce overfitting.

```text
patience = 3
```

Training was stopped when validation loss did not improve for the configured patience period.

---

## Learning Rate Adjustment

The learning rate was automatically reduced when model performance stopped improving.

```text
reduce_lr_patience = 2
reduce_lr_factor   = 0.5
```

---

## Selective Prediction

The model incorporates a **Selective Prediction** mechanism.

Instead of forcing a prediction for every input, the model can reject predictions with insufficient confidence.

```text
target_reject = 0.10
```

Both global and per-class thresholds were considered.

```text
Input Payload
      ↓
Preprocessing
      ↓
Tokenizer
      ↓
Padding
      ↓
Bi-LSTM
      ↓
Class Probabilities
      ↓
Confidence Threshold
     / \
Accept  Reject
  ↓
Normal / SQLi / XSS
```

---

## Model Selection

Three deep learning architectures were evaluated:

- Convolutional Neural Network (**CNN**)
- Long Short-Term Memory (**LSTM**)
- Bidirectional Long Short-Term Memory (**Bi-LSTM**)

| Model | Accuracy | Precision | Recall | F1-Score | False Positive Rate |
|---|---:|---:|---:|---:|---:|
| CNN | 88.32% | 87.54% | 88.32% | 87.21% | 11.68% |
| LSTM | 92.15% | 91.78% | 92.15% | 91.64% | 7.85% |
| **Bi-LSTM** | **95.47%** | **95.87%** | **95.47%** | **95.53%** | **4.53%** |

Bi-LSTM achieved the best overall performance and was selected as the final architecture.

---

## Final Model Performance

```text
Accuracy             : 95.47%
Weighted Precision   : 95.87%
Weighted Recall      : 95.47%
Weighted F1-Score    : 95.53%
False Positive Rate  : 4.53%
```

---

## Performance by Class

| Class | Precision | Recall | F1-Score | Support |
|---|---:|---:|---:|---:|
| Normal | 85.40% | 96.97% | 90.82% | 10,779 |
| SQL Injection | 98.29% | 91.61% | 94.83% | 20,692 |
| XSS | 99.88% | 99.55% | 99.71% | 15,643 |
| **Weighted Average** | **95.87%** | **95.47%** | **95.53%** | **47,114** |

---

## Confusion Matrix

The final evaluation was performed on **47,114 samples**.

| Actual \ Predicted | Normal | SQL Injection | XSS |
|---|---:|---:|---:|
| Normal | 10,452 | 314 | 13 |
| SQL Injection | 1,731 | 18,955 | 6 |
| XSS | 56 | 15 | 15,572 |

```text
Correct Predictions = 44,979 / 47,114
Accuracy            = 95.47%
False Positive Rate = 4.53%
```

---

## Model Inference

During inference, an input payload follows the same preprocessing procedure used during model development.

```text
Raw Payload
     ↓
Text Preprocessing
     ↓
Tokenizer
     ↓
Sequence Encoding
     ↓
Padding to max_len = 40
     ↓
Bi-LSTM Model
     ↓
Softmax Probabilities
     ↓
Selective Prediction
     ↓
Predicted Class
```

The model produces a probability distribution across the supported classes. The class with the highest probability is selected when it satisfies the configured confidence threshold.

---

## Development Environment

The main tools used during model development were:

```text
Python
TensorFlow 2.15.0
Scikit-learn 1.4.2
NumPy 1.26.4
Pandas 2.2.2
MLflow 2.12.1
```

- **TensorFlow / Keras** was used to construct and train the Bi-LSTM model.
- **Scikit-learn** was used for Stratified K-Fold Cross Validation and evaluation metrics.
- **MLflow** was used to track experiment parameters and model performance across training folds.

---

## Model Artifacts

The published release may contain the trained model and supporting inference artifacts, for example:

```text
model.h5
tokenizer
labels
```

These artifacts should be used together with the same preprocessing, tokenization, sequence length, and label mapping used during model development.

---

## Note

This repository focuses on the **AI model development and inference artifacts**. Web application, frontend, backend, database, and dashboard implementation details are intentionally excluded.
