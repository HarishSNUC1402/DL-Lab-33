```markdown
# CS3807 Deep Learning Laboratory: Experiment 3
## Implementation of Convolutional Neural Networks (CNNs) for Image Classification

---

## 📂 Dataset Description: CIFAR-10

The experiments are conducted using the **CIFAR-10 (Canadian Institute for Advanced Research)** dataset:

- **Total Images:** 60,000 color images
- **Image Resolution:** 32 × 32 pixels across 3 color channels (RGB)
- **Dataset Split:**
  - **Training Set:** 50,000 images (5,000 images per class)
  - **Testing Set:** 10,000 images (1,000 images per class)
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
- **Class Balance:** The dataset is perfectly balanced with an equal number of samples across all categories.
- **Data Tensor Dimensions:**
  - Training Data Tensor: `[50000, 3, 32, 32]`
  - Testing Data Tensor: `[10000, 3, 32, 32]`
- **Challenges:** Low resolution (32 × 32) coupled with substantial intra-class variation in object poses, illumination, backgrounds, and visual overlap (e.g., cat vs. dog, automobile vs. truck).

---

## 🚀 How to Run

### 1. Clone the Repository
```bash
git clone [https://github.com/](https://github.com/)<your-username>/<your-repo-name>.git
cd <your-repo-name>

```

### 2. Install Required Dependencies

Ensure you have Python 3.8+ installed, then run:

```bash
pip install torch torchvision numpy matplotlib seaborn scikit-learn notebook

```

### 3. Launch Jupyter Notebook

Start the Jupyter environment in your terminal:

```bash
jupyter notebook

```

### 4. Execute the Notebook

1. Open `DL_Lab_CNN_Experiment3.ipynb`.
2. Run all cells sequentially via **Cell** ➔ **Run All** (or execute cell-by-cell with `Shift + Enter`).
3. The dataset will automatically download to a local `./data` directory during the execution of Task 1.

```

```