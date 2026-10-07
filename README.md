# Customer Review NLP Analytics

End-to-end NLP portfolio project for analyzing Amazon customer reviews with classical machine learning, deep learning and transformer-based models.

## Business Problem

Large retailers receive thousands of customer reviews that are difficult to analyze manually. This project explores how NLP can automatically:

- classify reviews as **negative, neutral or positive**
- compare multiple modeling approaches
- summarize groups of customer reviews
- visualize model performance
- identify limitations and opportunities for a production-ready sentiment system

## Dataset

The coursework uses a public Amazon product-review dataset originally sourced from Datafiniti. One of the notebooks reports approximately **34,660 source reviews** before preprocessing.

Sentiment labels are derived from ratings:

| Rating | Sentiment |
|---|---|
| 1â€“2 | Negative |
| 3 | Neutral |
| 4â€“5 | Positive |

The dataset itself is not duplicated in this repository. See `data/README.md`.

## Modeling Approaches

### 1. Traditional NLP + Machine Learning

The classical NLP workflow includes:

- text cleaning
- TF-IDF vectorization
- class balancing experiments
- Naive Bayes
- Random Forest
- Gradient Boosting
- XGBoost
- voting / stacking experiments
- confusion matrices and classification reports

The original coursework notebook produced very high Random Forest scores after SMOTE-based balancing. Because the historical notebook applies resampling before the final train/test split, those numbers should be treated as **coursework results rather than production-grade estimates**. A leakage-safe pipeline would resample only the training data or perform resampling inside cross-validation folds.

### 2. LSTM Sentiment Classifier

A 3-class LSTM model was trained for negative, neutral and positive sentiment.

Historical notebook output reports approximately:

- **94.82% overall accuracy**
- weighted / macro performance around **0.95**
- training and validation curves
- per-class evaluation

As with the traditional ML experiment, the preprocessing / balancing sequence should be reevaluated using a leakage-safe split before treating this as a production estimate.

### 3. Pretrained BERT Baseline

A pretrained sentiment model was evaluated as a baseline:

`nlptown/bert-base-multilingual-uncased-sentiment`

The coursework evaluation reported:

- **91.3% accuracy** on the evaluated dataset
- weighted F1 around **0.924**

This baseline is useful because it shows what a pretrained model can do before task-specific fine-tuning.

### 4. Fine-Tuned BERT

`bert-base-uncased` was fine-tuned for three-class sentiment classification using an 80/20 train/validation split.

Historical validation results:

| Epoch | Validation Accuracy | Weighted F1 |
|---:|---:|---:|
| 1 | **94.84%** | 93.28% |
| 2 | 94.72% | 93.73% |
| 3 | 94.43% | **94.19%** |

The evaluation also exposes an important business / modeling issue: the positive class dominates the dataset, while the neutral class is much harder to classify. This is a useful reminder that **accuracy alone is not enough** for imbalanced NLP tasks.

### 5. Transformer Summarization

A `t5-small` summarization experiment is included to explore automatic review summarization.

The notebook includes:

- transformer tokenization
- fine-tuning
- training / validation loss
- generation of review summaries

## Repository Structure

```text
Customer-Review-NLP-Analytics/
â”œâ”€â”€ README.md
â”œâ”€â”€ ATTRIBUTION.md
â”œâ”€â”€ requirements.txt
â”œâ”€â”€ .gitignore
â”œâ”€â”€ data/
â”‚   â””â”€â”€ README.md
â”œâ”€â”€ notebooks/
â”‚   â”œâ”€â”€ 01_traditional_nlp.ipynb
â”‚   â”œâ”€â”€ 02_lstm_sentiment.ipynb
â”‚   â”œâ”€â”€ 03_bert_foundation.ipynb
â”‚   â”œâ”€â”€ 04_bert_finetuned.ipynb
â”‚   â””â”€â”€ 05_transformer_summarization.ipynb
â”œâ”€â”€ assets/
â”‚   â”œâ”€â”€ classification_report.png
â”‚   â”œâ”€â”€ model_evaluation_results.png
â”‚   â””â”€â”€ full_evaluation_report.png
â””â”€â”€ reports/
    â””â”€â”€ Project_Reviews_Classification.pdf
```

## Key Skills Demonstrated

- Python
- Pandas / NumPy
- NLP preprocessing
- TF-IDF
- scikit-learn
- Random Forest / XGBoost
- model evaluation
- class imbalance analysis
- TensorFlow / Keras
- LSTM
- PyTorch
- Hugging Face Transformers
- BERT fine-tuning
- T5 summarization
- confusion matrices
- precision / recall / F1
- technical reporting

## What I Would Improve Next

A production-quality revision would:

1. split the data before any resampling
2. use stratified train / validation / test sets
3. use class weights or training-only resampling
4. optimize for macro-F1 in addition to accuracy
5. add systematic error analysis for the neutral class
6. modularize preprocessing, training and evaluation into reusable Python modules
7. remove machine-specific file paths from notebooks
8. add reproducible environment and experiment configuration
9. add unit tests for preprocessing
10. build a lightweight dashboard for business users

## Portfolio Note

This repository is a cleaned presentation of work completed during the Ironhack AI & Machine Learning program. The original assignment scaffolding belongs to Ironhack; the implementations, experiments and project deliverables included here reflect my coursework.

## Author

**Joshua Miranda**

Data Analytics â€¢ Artificial Intelligence â€¢ Python â€¢ SQL â€¢ Machine Learning