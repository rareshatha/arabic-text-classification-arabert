# Arabic Text Classification with AraBERT

## Overview

This project explores the impact of fine-tuning **AraBERT v2** on Arabic sentiment classification using the **AJGT (Arabic Jordanian General Tweets)** dataset.

The main goal is to compare the performance of the pre-trained AraBERT model before and after fine-tuning and evaluate how much task-specific training can improve Arabic text classification.

The project is implemented as a **Google Colab notebook** and covers the complete workflow, including dataset preparation, Arabic text tokenization, baseline evaluation, model fine-tuning, performance evaluation, visualization, and sentiment prediction on custom Arabic texts.

## Objective

The objective of this project is to demonstrate how fine-tuning a pre-trained Arabic language model can improve its performance on a specific text classification task.

The model is evaluated before and after fine-tuning using:

* Accuracy
* Weighted F1-Score
* Classification Report
* Confusion Matrix

## Dataset

The project uses the **AJGT (Arabic Jordanian General Tweets)** dataset, a publicly available Arabic sentiment classification dataset containing tweets labeled as:

* **Negative**
* **Positive**

The dataset is loaded directly using the Hugging Face Datasets library.

The dataset is split into training and testing sets using an 80/20 split.

## Model

The project uses **AraBERT v2**:

```text
aubmindlab/bert-base-arabertv02
```

AraBERT is a BERT-based language model designed for Arabic Natural Language Processing tasks.

In this project, the model is adapted for binary sentiment classification.

## Methodology

The notebook follows these main steps:

1. Install the required libraries.
2. Load and explore the AJGT dataset.
3. Split the dataset into training and testing sets.
4. Load the AraBERT tokenizer.
5. Tokenize and preprocess the Arabic text.
6. Evaluate the pre-trained AraBERT model as a baseline.
7. Fine-tune AraBERT on the training dataset.
8. Evaluate the fine-tuned model.
9. Compare the baseline and fine-tuned results.
10. Generate performance visualizations.
11. Test the fine-tuned model on custom Arabic texts.

## Text Preprocessing

Arabic text is processed using the AraBERT tokenizer.

The maximum sequence length is set to **128 tokens**, with padding and truncation applied during tokenization.

```python
MAX_LENGTH = 128
```

## Fine-Tuning Configuration

The model is fine-tuned using the Hugging Face `Trainer` API.

| Parameter               |      Value |
| ----------------------- | ---------: |
| Pre-trained Model       | AraBERT v2 |
| Epochs                  |          3 |
| Training Batch Size     |         16 |
| Evaluation Batch Size   |         16 |
| Learning Rate           |       2e-5 |
| Weight Decay            |       0.01 |
| Maximum Sequence Length |        128 |
| Warmup Ratio            |        0.1 |
| Early Stopping Patience |          2 |

## Technologies Used

* Python
* Google Colab
* PyTorch
* Hugging Face Transformers
* Hugging Face Datasets
* Scikit-learn
* Matplotlib
* Seaborn
* AraBERT
* Natural Language Processing
* Transfer Learning
* Fine-Tuning

## Results

The project compares AraBERT's performance before and after fine-tuning.

| Model              | Accuracy | Weighted F1-Score |
| ------------------ | -------: | ----------------: |
| AraBERT Baseline   |   53.12% |            48.91% |
| AraBERT Fine-tuned |   92.47% |            92.31% |

Fine-tuning resulted in a significant improvement in both evaluation metrics.

The Accuracy increased from **53.12% to 92.47%**, while the Weighted F1-Score increased from **48.91% to 92.31%**.

## Performance Visualization

The notebook generates several visualizations to analyze the model's performance.

### Label Distribution

The notebook visualizes the distribution of Positive and Negative samples in the training and testing sets.

### Confusion Matrix

The confusion matrix shows the classification performance of the fine-tuned model across the Positive and Negative classes.

### Before vs After Fine-Tuning

A comparison chart shows the difference in Accuracy and F1-Score before and after fine-tuning.

### Training Curves

Training curves are used to monitor:

* Training Loss
* Validation Accuracy
* Validation F1-Score

## Custom Arabic Text Inference

The fine-tuned model is also tested on custom Arabic sentences.

For each input, the model provides:

* Predicted sentiment
* Prediction confidence

Example:

```text
Text       : الخدمة كانت رائعة والموظفون محترمون جداً
Prediction : Positive
```

## How to Run

The project is implemented as a **Google Colab notebook**.

### Option 1: Google Colab

Open the notebook in Google Colab and run the cells in order.

The notebook automatically installs the required libraries and loads the dataset and pre-trained AraBERT model.

### Option 2: Run Locally

The notebook can also be downloaded as an `.ipynb` file and opened using:

* Jupyter Notebook
* JupyterLab
* Google Colab
* VS Code with Jupyter support

Install the required libraries before running the notebook:

```bash
pip install transformers datasets torch scikit-learn matplotlib seaborn arabert
```

## Project Structure

```text
arabic-text-classification-arabert/
│
├── Arabic_LLM_Finetuning.ipynb
├── README.md
├── label_distribution.png
├── confusion_matrix.png
├── comparison_chart.png
└── training_curves.png
```

## Key Findings

* Fine-tuning significantly improves AraBERT's performance on the target Arabic sentiment classification task.
* The fine-tuned model achieved over **92% Accuracy and Weighted F1-Score**.
* A relatively small Arabic dataset can be effective when combined with a pre-trained language model.
* Fine-tuning allows a pre-trained Arabic model to adapt to a specific NLP task.
* Performance visualizations provide a clearer view of the model's behavior and training progress.

## Future Work

Possible improvements for future work include:

* Evaluating the model on larger and more diverse Arabic datasets.
* Testing the model on different Arabic dialects.
* Exploring additional Arabic NLP datasets and classification tasks.
* Applying data augmentation techniques.
* Experimenting with other Arabic language models.
* Exploring approaches such as Retrieval-Augmented Generation (RAG).

## Academic Project

This project was developed as part of the **Generative AI with LLMs – AI496** course.

**Student:** Shatha Adel Mahrous
**Student ID:** 4210833
**Supervisor:** Dr. Soumaya Chaffar
**University:** University of Prince Mugrin
**Year:** 2026

## Acknowledgments

I would like to thank **Dr. Soumaya Chaffar** for her guidance and supervision throughout this project, and the **University of Prince Mugrin** for providing the academic environment and support needed to complete the work.

## License

This project was developed for academic and educational purposes.
