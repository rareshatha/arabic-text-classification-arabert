# Arabic Text Classification with AraBERT

## Overview

This project explores the impact of fine-tuning **AraBERT v2** on Arabic sentiment classification.

The main goal is to compare the performance of the pre-trained AraBERT model before and after task-specific fine-tuning using the **AJGT (Arabic Jordanian General Tweets)** dataset.

The project covers the complete workflow, including dataset preparation, Arabic text tokenization, baseline evaluation, model fine-tuning, performance evaluation, visualization, and inference on custom Arabic texts.

## Objective

The objective of this project is to demonstrate how fine-tuning a pre-trained Arabic language model can improve its performance on a specific text classification task.

The model is evaluated before and after fine-tuning using:

* Accuracy
* Weighted F1-Score
* Classification Report
* Confusion Matrix

## Dataset

The project uses the **AJGT (Arabic Jordanian General Tweets)** dataset.

It is a binary sentiment classification dataset containing Arabic tweets labeled as:

* **Negative**
* **Positive**

The dataset is loaded using the Hugging Face Datasets library.

The data is divided into training and testing sets using an 80/20 split.

## Model

The project uses:

**AraBERT v2**

```text
aubmindlab/bert-base-arabertv02
```

AraBERT is a BERT-based language model designed specifically for Arabic Natural Language Processing tasks.

For this project, the model is adapted for binary sentiment classification.

## Methodology

The project follows these main steps:

1. Install and import the required libraries.
2. Load and explore the AJGT dataset.
3. Split the dataset into training and testing sets.
4. Load the AraBERT tokenizer.
5. Tokenize and preprocess the Arabic text.
6. Evaluate the pre-trained AraBERT model as a baseline.
7. Fine-tune AraBERT on the training dataset.
8. Evaluate the fine-tuned model.
9. Compare the baseline and fine-tuned results.
10. Visualize the model performance.
11. Test the fine-tuned model on custom Arabic texts.

## Text Preprocessing

Arabic text is tokenized using the AraBERT tokenizer.

The maximum sequence length is set to **128 tokens**, with padding and truncation applied during tokenization.

```python
MAX_LENGTH = 128
```

## Fine-Tuning Configuration

The model was fine-tuned using the Hugging Face `Trainer` API.

Main training settings:

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
| Optimizer               |      AdamW |
| Early Stopping Patience |          2 |

## Technologies Used

* Python
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

The project generates several visualizations to analyze model performance.

### Confusion Matrix

The confusion matrix shows the classification performance of the fine-tuned model across the Positive and Negative classes.

```text
confusion_matrix.png
```

### Before vs After Fine-Tuning

A comparison chart is generated to visualize the change in Accuracy and F1-Score before and after fine-tuning.

```text
comparison_chart.png
```

### Training Curves

Training and evaluation curves are generated to monitor:

* Training Loss
* Validation Accuracy
* Validation F1-Score

```text
training_curves.png
```

### Dataset Distribution

The project also visualizes the distribution of Positive and Negative labels in the training and testing sets.

```text
label_distribution.png
```

## Custom Arabic Text Inference

After fine-tuning, the model can be used to classify new Arabic texts as Positive or Negative.

The project includes examples of custom Arabic sentences and returns:

* Predicted sentiment
* Prediction confidence

Example:

```text
Text       : الخدمة كانت رائعة والموظفون محترمون جداً
Prediction : Positive
```

## Project Structure

```text
arabic-text-classification-arabert/
│
├── arabic_llm_finetuning.py
├── README.md
├── label_distribution.png
├── confusion_matrix.png
├── comparison_chart.png
└── training_curves.png
```

## Installation

Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/arabic-text-classification-arabert.git
```

Move to the project directory:

```bash
cd arabic-text-classification-arabert
```

Install the required libraries:

```bash
pip install transformers datasets torch scikit-learn matplotlib seaborn arabert
```

## Running the Project

Run the Python script:

```bash
python arabic_llm_finetuning.py
```

The script will:

* Load the AJGT dataset.
* Prepare and tokenize the data.
* Evaluate the baseline AraBERT model.
* Fine-tune AraBERT.
* Evaluate the fine-tuned model.
* Generate performance metrics and visualizations.
* Run sentiment predictions on custom Arabic texts.

## Key Findings

* Fine-tuning significantly improves AraBERT's performance on the target classification task.
* The fine-tuned model achieved over **92% Accuracy and Weighted F1-Score**.
* A relatively small Arabic dataset can be effective when combined with a strong pre-trained language model.
* Fine-tuning allows a general pre-trained Arabic model to adapt to a specific NLP task.
* Performance visualization and detailed evaluation help provide a clearer understanding of model behavior.

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
