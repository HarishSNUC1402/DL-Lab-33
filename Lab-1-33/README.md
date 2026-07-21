# Experiment 1: Single Layer Perceptron for Binary Classification

## Objective
The objective of this experiment is to understand the concept of an artificial neuron and implement a Single Layer Perceptron from scratch for binary classification[cite: 3]. The project involves learning the perceptron algorithm, visualizing the training process, and evaluating the classifier using a real-world dataset.

## Dataset Information
* **Name:** Banknote Authentication Dataset
* **Source:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/267/banknote+authentication)
* **Instances:** 1372
* **Features:** 4 Numerical Features (Variance, Skewness, Curtosis, Entropy)
* **Target Class:** 0 for Authentic Banknote, 1 for Forged Banknote

## Repository Structure
* `DL_Lab_1.ipynb`: The primary Python script containing the dataset loading, EDA, preprocessing, model training, and evaluation.
* `requirements.txt`: The list of Python dependencies required to run the code.
* `README.md`: Project documentation.

## Dependencies
The project requires Python 3.8+ and the following libraries:
* pandas
* numpy
* matplotlib
* seaborn
* scikit-learn

## Execution Instructions
Follow these steps to run the experiment on your local machine:

**Step 1: Clone the repository**
```bash
git clone [https://github.com/yourusername/perceptron-binary-classification.git](https://github.com/yourusername/perceptron-binary-classification.git)
cd perceptron-binary-classification