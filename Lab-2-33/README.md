# Multi-Layer Perceptron (MLP) for Multi-Class Image Classification

**Shiv Nadar University Chennai**  
**Course:** CS3807 - Deep Learning Laboratory  
**Experiment 2:** Implementation of a Multi-Layer Perceptron (MLP) for Multi-Class Image Classification  

---

## Overview
This repository contains the implementation of a Multi-Layer Perceptron (MLP) built using TensorFlow/Keras to classify clothing images from the Fashion-MNIST dataset. The project walks through the complete deep learning pipeline: data preprocessing, building a baseline neural network, training, evaluation, and finally, utilizing automated hyperparameter optimization to find the most efficient network architecture.

## Objectives
* Implement an MLP using TensorFlow and Keras.
* Preprocess image datasets (flattening 2D matrices to 1D vectors, normalizing pixel values).
* Build, train, and evaluate a baseline MLP model.
* Perform automated hyperparameter optimization using RandomizedSearchCV paired with SciKeras.
* Compare baseline performance against the optimized model.

## Dataset: Fashion-MNIST
The project uses the Fashion-MNIST dataset, which is designed as a drop-in replacement for the classic MNIST dataset[cite: 1]. 
* **Training Images:** 60,000[cite: 1]
* **Testing Images:** 10,000[cite: 1]
* **Classes:** 10 distinct apparel categories (T-shirt/top, Trouser, Pullover, Dress, Coat, Sandal, Shirt, Sneaker, Bag, Ankle boot)[cite: 1]
* **Image Dimensions:** 28 x 28 pixels (Grayscale)[cite: 1]

---

## Model Architectures

### 1. Baseline Model
Constructed based on the recommended lab manual architecture[cite: 1]:
* **Input Layer:** 784 neurons (flattened 28x28 images)[cite: 1]
* **Hidden Layer 1:** 128 neurons, ReLU activation[cite: 1]
* **Hidden Layer 2:** 64 neurons, ReLU activation[cite: 1]
* **Output Layer:** 10 neurons, Softmax activation[cite: 1]
* **Optimizer:** Adam | **Loss:** Categorical Crossentropy | **Epochs:** 20 | **Batch Size:** 32[cite: 1]

### 2. Optimized Model
Obtained via RandomizedSearchCV through a predefined search space[cite: 1]:
* **Input Layer:** 784 neurons[cite: 1]
* **Hidden Layer(s):** 1 Layer with 256 neurons
* **Activation:** Tanh
* **Regularization:** Dropout rate of 0.2
* **Output Layer:** 10 neurons, Softmax activation[cite: 1]
* **Optimizer:** Adam (Learning Rate: 0.001) | **Epochs:** 20 | **Batch Size:** 64

---

## Results and Performance Comparison

By optimizing our hyperparameters, we discovered that a simpler, wider network (1 hidden layer, 256 neurons) performed just as well as the deeper baseline model, but was significantly faster to train.

| Metric | Baseline Model | Optimized Model |
| :--- | :---: | :---: |
| **Accuracy** | 0.8778 | 0.8793 |
| **Precision** | 0.8820 | 0.8791 |
| **Recall** | 0.8778 | 0.8793 |
| **F1-Score** | 0.8790 | 0.8768 |
| **Training Time** | ~97.39s | ~53.38s |

> **Key Takeaway:** Hyperparameter tuning proved that increasing architectural complexity does not always yield better results. By lowering the hidden layer count to 1 and increasing the batch size to 64, training time was nearly cut in half without sacrificing predictive accuracy.

---

## Tools and Technologies Used
* **Python 3.x**
* **TensorFlow / Keras:** For model building and deep learning operations.
* **Scikit-Learn:** For metrics (Confusion Matrix, Classification Report) and Hyperparameter Optimization.
* **SciKeras:** Wrapper to bridge Keras models with Scikit-Learn's tuning tools[cite: 1].
* **Matplotlib & Seaborn:** For generating mandatory loss/accuracy curves and heatmaps[cite: 1].

---

## How to Run Locally

**1. Clone the repository:**
```bash
git clone [https://github.com/HarishSNUC1402/DL-Lab-33.git](https://github.com/HarishSNUC1402/DL-Lab-33.git)
cd DL-Lab-33/Lab-1-33