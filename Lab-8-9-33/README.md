# CS3807 -- Deep Learning Laboratory: Experiments 8 & 9
**Effect of Attention Type and Attention Position in a Pretrained ResNet50**

---

## Dataset Overview

This repository uses the **TensorFlow Flowers (`tf_flowers`)** dataset[cite: 2], a standard image classification benchmark widely used in deep learning research and repositories similar to Kaggle and the UCI Machine Learning Repository.

### Abstract & Source
* **Dataset Name:** TensorFlow Flowers (`tf_flowers`)[cite: 2]
* **Source:** Originally collected and curated by Google; made available via TensorFlow Datasets.
* **Domain:** Computer Vision, Natural Image Classification, Fine-Grained Object Recognition.

---

## Dataset Characteristics & Specifications

| Attribute | Detail |
| :--- | :--- |
| **Data Type** | Multivariate, Image (RGB)[cite: 2] |
| **Task** | Single-label multi-class image classification[cite: 2] |
| **Total Instances** | 3,670 color images |
| **Number of Classes** | 5 distinct target classes[cite: 2] |
| **Class Distribution** | Approximately balanced across classes (~700–800 images per class) |
| **Image Resolution** | Variable native resolution; resized to $224 \times 224 \times 3$ for backbone compatibility[cite: 2] |
| **Missing Values** | None (clean benchmark corpus) |

---

## Data Fields & Target Classes

Each sample consists of a raw RGB image and an integer label corresponding to one of the following 5 target categories[cite: 2]:

1. `daisy`[cite: 2]
2. `dandelion`[cite: 2]
3. `roses`[cite: 2]
4. `sunflowers`[cite: 2]
5. `tulips`[cite: 2]

---

## Dataset Variations & Challenges

The dataset presents several real-world computer vision challenges that test the robustness of convolutional neural networks and attention modules:
* **Scale & Viewpoint Variations:** Flowers photographed from various angles, close-ups, and wide shots[cite: 2].
* **Illumination & Color:** Variations in lighting conditions, exposure, and natural color saturations[cite: 2].
* **Background Clutter:** Complex natural surroundings including grass, soil, hands, and auxiliary foliage[cite: 2].
* **Intra-class Variance:** Structural diversity within classes (e.g., distinct species and petal counts of roses or tulips)[cite: 2].

---

## Experimental Split Protocol

To ensure rigorous and reproducible benchmarking across all attention ablation studies, a deterministic data partitioning protocol is enforced:

* **Split Ratio:** $70\% : 15\% : 15\%$ for **Training : Validation : Testing**[cite: 2].
* **Exact Sample Count:**
  * **Training Set:** 2569 images
  * **Validation Set:** 550 images
  * **Testing Set:** 551 images
* **Reproducibility:** Fixed random seed (`SEED = 42`) is maintained across all experiments.

---

## Preprocessing & Data Augmentation Pipeline

1. **Resizing:** All input tensors are reshaped to $224 \times 224 \times 3$.
2. **Normalization:** Pixel values are preprocessed using the standard zero-center scaling required by ImageNet-pretrained ResNet50 backbones[cite: 2].
3. **Stochastic Augmentation (Train Set Only):**
   * Random left-right horizontal flipping[cite: 3]
   * Random brightness adjustments ($\max\delta = 0.1$)[cite: 3]
   * Random contrast scaling ($[0.9, 1.1]$)[cite: 3]

---

## Repository Structure

```text
├── Lab-8-9-33/
│   ├── code/                  # Executable Jupyter notebooks and Python scripts
│   ├── plots/                 # Generated visualization figures (plot1.png to plot10.png)
│   ├── dl_lab_8_9.pdf         # Compiled lab report document
│   └── README.md              # Repository and dataset documentation