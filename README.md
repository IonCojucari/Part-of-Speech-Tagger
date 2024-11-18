# Part-of-Speech Tagger

## Overview

This project is a **Part-of-Speech (POS) Tagging system** that uses **probabilistic models** and supports **greedy decoding** to tag sequences of words. It implements **unigram, bigram, and trigram models** for transition probabilities, combined with emission probabilities for words given tags. The system is designed for efficient training, evaluation, and inference.

---

## Features

### Probabilistic Models
- **Unigrams**: Calculate probabilities of individual tags.
- **Bigrams**: Estimate the likelihood of a tag given the previous tag.
- **Trigrams**: Use a sequence of two preceding tags to estimate the next tag probability.
- **Emission Probabilities**: Compute the likelihood of words for each tag.

### Capabilities
- **Inference**:
  - Tags input sentences using **greedy decoding**.
  - Handles unknown words with smoothing.
- **Sequence Probability**:
  - Computes the likelihood of a tagged sentence.
- **Evaluation**:
  - Measures whole-sentence accuracy, token accuracy, and unknown-token accuracy.
  - Outputs confusion matrices for performance analysis.

### Scalability
- **Multiprocessing**:
  - Speed up training and evaluation by parallelizing computations.
- **Data Handling**:
  - Efficiently loads and processes large datasets.

### Output
- Writes predictions to a CSV file for integration with other systems or evaluations.

---

## Project Structure

### Codebase
1. **`pos_tagger.py`**:
   - Implements the core POS tagger and training logic.
   - Includes probabilistic models and decoding mechanisms.

2. **`evaluate.py`**:
   - Evaluates model performance using metrics like F1-score and confusion matrices.

3. **`constants.py`**:
   - Defines configurable parameters for smoothing, inference methods, and other settings.

4. **`utils.py`**:
   - Contains utility functions for data loading, inference, and visualization (e.g., confusion matrices).

### Data Files
- **Training and Development**:
  - `train_x.csv`, `train_y.csv`: Input sentences and corresponding tags for training.
  - `dev_x.csv`, `dev_y.csv`: Data for model validation and evaluation.
- **Testing**:
  - `test_x.csv`: Unlabeled data for prediction.
  - Predictions are saved to `test_y.csv`.

---

## Usage

### Setup
1. Clone the repository and navigate to the project directory.
2. Place the dataset files (`train_x.csv`, `train_y.csv`, `dev_x.csv`, `dev_y.csv`, `test_x.csv`) in the `data/` folder.

### Run the Project
1. Train the model and evaluate performance:
   ```bash
   python pos_tagger.py
   ```
2. Evaluate results and visualize metrics:
   ```bash
   python evaluate.py -p data/test_y.csv -d data/dev_y.csv --confusion
   ```

3. Predictions for the test set are saved in `data/test_y.csv`.

---

## Results

- **Metrics**:
  - Whole-sentence accuracy.
  - Token accuracy (overall and for unknown tokens).
  - Weighted F1-score for development set predictions.
- **Visualization**:
  - Confusion matrix heatmaps for detailed tag-level analysis.

---

## Configuration Options

- **N-gram Model**: Switch between unigram, bigram, and trigram models (`constants.py`).
- **Smoothing**:
  - Choose between **Laplace smoothing** and **interpolation**.
  - Configure smoothing parameters (e.g., `LAPLACE_FACTOR`).
- **Inference**:
  - Supports **greedy decoding**.
  - Future improvements can integrate Viterbi or beam search.

---

## Future Enhancements

- Implement **beam search** or **Viterbi decoding** for better inference.
- Integrate **pretrained word embeddings** for improved tagging accuracy.
- Add support for multi-language datasets.
- Explore **neural network-based POS tagging**.

---

## Contribution

Contributions to improve the system are welcome. Submit issues or pull requests to enhance the functionality or performance of the tagger.
