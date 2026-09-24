```markdown
# CS3807 Deep Learning Laboratory: Experiment 5
## Comprehensive Study of CNN Training, Regularization, Optimization, Hyperparameter Tuning, Transfer Learning and Cross-Validation

---

## 📂 Dataset Description: Oxford-IIIT Pet Dataset

This experiment uses the **Oxford-IIIT Pet Dataset**, a fine-grained image classification benchmark of cats and dogs :

- **Total Samples:** 7,390 valid RGB images 
- **Target Classes:** 37 fine-grained breeds (cats and dogs) 
- **Resolution & Preprocessing:** 
  - Raw images possess varying spatial resolutions and aspect ratios .
  - All input images are uniformly resized to $224 \times 224 \times 3$ .
  - Input pixel channels are normalized according to MobileNet V2 ImageNet requirements .
- **Data Partitioning:**
  - **Training Set (70%):** 5,172 samples 
  - **Validation Set (15%):** 1,109 samples 
  - **Test Set (15%):** 1,109 samples (strictly held out and untouched during tuning) 
  - **Cross-Validation Pool:** The combined train + validation pool (6,281 samples) is used for 5-fold stratified cross-validation .
- **Classification Challenges:** High intra-class variance in posture and lighting, combined with low inter-class variance among morphologically similar breeds (e.g., American Pit Bull Terrier vs. Staffordshire Bull Terrier, Ragdoll vs. Birman) .

---

## 🚀 How to Run

### 1. Clone the Repository
```bash
git clone [https://github.com/](https://github.com/)<your-username>/<your-repo-name>.git
cd <your-repo-name>

```

### 2. Install Required Dependencies

Ensure Python 3.8+ is installed, then run:

```bash
pip install tensorflow keras numpy matplotlib seaborn scikit-learn notebook

```

### 3. Launch Jupyter Notebook

Start the local notebook server:

```bash
jupyter notebook

```

### 4. Execute the Experiment Notebook

1. Open the experiment notebook (`dl-lab5.ipynb`).
2. Run all cells sequentially via **Cell** ➔ **Run All** (or execute step-by-step using `Shift + Enter`).
3. The dataset will be downloaded and extracted into the working directory automatically upon executing the data ingestion cell.

```

```