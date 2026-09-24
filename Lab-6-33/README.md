```markdown
# CS3807 Deep Learning Laboratory: Experiment 6
## End-to-End Study of RNN, LSTM and GRU for Sequence Learning and Video Understanding

---

## 📂 Dataset Descriptions

### 1. Primary Dataset: UCI Human Activity Recognition (HAR) Using Smartphones
The primary sequence classification task utilizes sensor data collected from embedded smartphone accelerometers and gyroscopes:
- **Number of Sequences ($N$):** A stratified experimental subset of 3,000 temporal windows[cite: 4].
- **Partitioning:**
  - **Training Set (70%):** 2,100 sequences
  - **Validation Set (15%):** 450 sequences
  - **Test Set (15%):** 450 sequences (strictly held out)
- **Sequence Dimensions:** Shape of `(N, T, F)` where:
  - $T = 128$ timesteps per window
  - $F = 9$ inertial features/channels (3-axis body acceleration, 3-axis gyroscope, 3-axis total acceleration)
  - Tensor shapes: Training `(2100, 128, 9)`, Validation `(450, 128, 9)`, Testing `(450, 128, 9)`
- **Target Activity Classes (6 categories):**
  - `0`: WALKING
  - `1`: WALKING_UPSTAIRS
  - `2`: WALKING_DOWNSTAIRS
  - `3`: SITTING
  - `4`: STANDING
  - `5`: LAYING
- **Normalization:** Z-score normalization computed strictly over training statistics ($\mu_{train}$, $\sigma_{train}$) and applied to validation and test partitions.

### 2. Video Dataset: Action Recognition
Used for the CNN-RNN video classification pipeline:
- **Input Sampling:** 10 equidistant frames per video clip resized to $224 \times 224 \times 3$.
- **Feature Extraction:** Pre-trained frozen MobileNet V2 extracts a 1280-dimensional feature embedding per frame, forming a representation shape of `(Batch, 10, 1280)`.
- **Target Action Classes (4 sports activities):** Basketball, Biking, TennisSwing, and WalkingWithDog.

### 3. Synthetic Seq2Seq Dataset
Used to demonstrate sequence reversal via encoder-decoder architecture:
- **Input/Target:** Variable sequence of discrete tokens (integers) mapped to reversed order (e.g., `[3, 8, 1, 5]` $\rightarrow$ `[5, 1, 8, 3]`)[cite: 4].

---

## 🚀 How to Run

### 1. Clone the Repository
```bash
git clone [https://github.com/](https://github.com/)<your-username>/<your-repo-name>.git
cd <your-repo-name>

```

### 2. Install Required Dependencies

Ensure you are using Python 3.8+, then install the required dependencies:

```bash
pip install tensorflow numpy matplotlib seaborn scikit-learn notebook

```

### 3. Launch Jupyter Notebook

Start your Jupyter server from the command line:

```bash
jupyter notebook

```

### 4. Execute the Notebook

1. Open `dl-lab-6.ipynb`.
2. Run cells sequentially (`Cell` ➔ `Run All` or step-through with `Shift + Enter`).
3. The UCI HAR dataset and sample action clips are processed automatically inside the notebook environment during data preparation steps.



```

```