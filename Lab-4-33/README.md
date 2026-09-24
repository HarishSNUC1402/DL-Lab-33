```markdown
# CS3807 Deep Learning Laboratory: Experiment 4
## Comparative Study of Deep Convolutional Neural Network Architectures Using Transfer Learning

This repository contains the implementation, comparative analysis, and hyperparameter evaluation of modern Convolutional Neural Network architectures (LeNet-5, AlexNet, VGG16, GoogleNet, and ResNet) using Transfer Learning and Fine-Tuning on the CIFAR-10 dataset .

---

## 📂 Dataset Description: CIFAR-10

The experiment evaluates models on the **CIFAR-10 (Canadian Institute for Advanced Research)** dataset :

- **Total Images:** 60,000 color images[cite: 1, 2]
- **Image Resolution:** 32 × 32 pixels across 3 color channels (RGB) 
- **Dataset Split:**
  - **Training Set:** 50,000 images (5,000 samples per class)[cite: 1, 2]
  - **Testing Set:** 10,000 images (1,000 samples per class)[cite: 1, 2]
- **Classes (10 mutually exclusive categories):**
  1. Airplane 
  2. Automobile 
  3. Bird 
  4. Cat 
  5. Deer 
  6. Dog 
  7. Frog 
  8. Horse 
  9. Ship 
  10. Truck 
- **Class Balance:** The dataset is uniformly distributed across all 10 target classes[cite: 1, 2].
- **Tensor Dimensions:**
  - Training Data: `(50000, 32, 32, 3)` 
  - Testing Data: `(10000, 32, 32, 3)` 
- **Preprocessing:** All pixel intensities are normalized from the integer range `[0, 255]` to floating points within `[0, 1]` .

---

## 🏗️ Architecture & Transfer Learning Workflow

The experiment utilizes **VGG16** pretrained on ImageNet as the feature extraction backbone :


```

Input Image (32 x 32 x 3)
│
▼
[VGG16 Convolutional Base] (Pretrained ImageNet weights; feature layers frozen initially)
│
▼
[GlobalAveragePooling2D]
│
▼
[Dense Layer] (ReLU activation, 128 / 256 units)
│
▼
[Dropout / Output Dense Layer] (10 units, Softmax activation)

```

1. **Feature Extraction Phase:** The convolutional base is frozen, and only the custom top classification head is trained .
2. **Fine-Tuning Phase:** The top convolutional blocks of the base network are unfrozen and trained at a lower learning rate to adapt specific representations to CIFAR-10 .

---

## 📊 Key Experimental Findings

### 1. Effect of Fine-Tuning (VGG16)
- **Validation Accuracy Before Fine-Tuning (Frozen Base):** 63.07% 
- **Validation Accuracy After Fine-Tuning (Unfrozen Top Blocks):** 74.94% 

### 2. Architecture Comparison Summary
| Model | Trainable / Total Parameters | Accuracy (%) | Training Time |
| :--- | :--- | :--- | :--- |
| **LeNet-5** | 5,407,286  | 59.94%  | 157.74 s  |
| **AlexNet** | 57,044,810  | 57.28%  | 206.67 s  |
| **VGG16** | 134,301,514  | 69.23%  | 2310.55 s  |
| **GoogleNet** | 5,610,154  | 72.03%  | 654.23 s  |
| **ResNet-18** | 11,181,642  | 74.97%  | 523.34 s  |

---

## 🚀 How to Run

### 1. Clone the Repository
```bash
git clone [https://github.com/](https://github.com/)<your-username>/<your-repo-name>.git
cd <your-repo-name>

```

### 2. Install Required Dependencies

Ensure you have Python 3.8+ installed, then install the required packages:

```bash
pip install tensorflow keras numpy matplotlib seaborn scikit-learn notebook

```

### 3. Launch the Jupyter Notebook Interface

Start the notebook server:

```bash
jupyter notebook

```

### 4. Execute the Notebook

1. Open the experiment notebook (e.g., `DL_Lab4_Transfer_Learning.ipynb`).
2. Run all cells sequentially via **Cell** ➔ **Run All** (or execute cell-by-cell using `Shift + Enter`).
3. The CIFAR-10 dataset will be fetched automatically via `tf.keras.datasets.cifar10.load_data()` during runtime.



```

```