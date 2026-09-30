# MNIST Autoencoder Study

This directory contains the plots produced for **CS3807 Deep Learning
Laboratory - Experiment 7**. The accompanying notebook, [`E7_final.ipynb`](../E7_final.ipynb),
implements and compares a fully connected autoencoder, convolutional
autoencoder, denoising autoencoder, and variational autoencoder (VAE).

## Dataset card

### Dataset

**MNIST handwritten digits** (Modified National Institute of Standards and
Technology database).

| Property | Description |
| --- | --- |
| Task | Unsupervised image reconstruction and representation learning |
| Data type | Grayscale images of handwritten decimal digits |
| Classes | 10 digit labels (`0` through `9`); labels are used for display and analysis, not as model targets |
| Original training set | 60,000 images |
| Original test set | 10,000 images |
| Image dimensions | 28 x 28 pixels, 1 channel |
| Pixel values | 0-255 in the downloaded files; normalized to `[0, 1]` before training |
| Experimental training subset | First 10,000 training images |
| Experimental test subset | First 2,000 test images |
| Flattened representation | `(N, 784)` for the fully connected autoencoder |
| Spatial representation | `(N, 28, 28, 1)` for the convolutional, denoising, and variational autoencoders |
| Missing values | None expected |
| Download source | `tf.keras.datasets.mnist` (TensorFlow's MNIST mirror) |

The notebook downloads the dataset automatically the first time
`tf.keras.datasets.mnist.load_data()` is executed. No dataset file needs to be
committed to this repository.

### Preprocessing

1. Load MNIST through TensorFlow/Keras.
2. Keep the first 10,000 training images and first 2,000 test images to make
   the laboratory experiment reproducible and practical to run.
3. Convert pixel values to `float32` and divide by 255.
4. Keep both flattened and image-shaped versions of the data.
5. Add Gaussian or salt-and-pepper corruption only for the denoising
   autoencoder experiment.

### Models and experiment settings

| Model | Main configuration | Objective |
| --- | --- | --- |
| FC-AE | `784 -> 128 -> 32 -> 16 -> 32 -> 128 -> 784` | Binary cross-entropy reconstruction loss |
| CAE | Convolutional encoder with pooling and convolutional decoder with upsampling | Image reconstruction |
| DAE | Gaussian noise (`sigma` 0.1, 0.2, 0.3) and salt-and-pepper noise (`p=0.10`) | Recover clean images from corrupted images |
| VAE | Two-dimensional latent space with reparameterization | Reconstruction loss plus KL-divergence regularization |

The FC-AE uses Adam with learning rate `1e-3`, batch size `128`, and `20`
epochs. The notebook also evaluates reconstruction error, SSIM, latent-space
structure, random VAE generations, latent interpolation, and latent dimensions
`{2, 8, 16, 32}`.

## Repository contents

- [`../E7_final.ipynb`](../E7_final.ipynb) - complete experiment notebook.
- [`plot1.png`](plot1.png) and [`plot2.png`](plot2.png) - fully connected
  autoencoder reconstructions and training curves.
- [`plot3.png`](plot3.png) - FC-AE and CAE reconstruction comparison.
- [`plot4.png`](plot4.png) and [`plot5.png`](plot5.png) - denoising examples
  and noise-level comparison.
- [`plot6.png`](plot6.png) through [`plot9.png`](plot9.png) - VAE latent
  space, generated samples, interpolation, and training curves.
- [`plot10.png`](plot10.png) - latent-dimension study.

## How to clone and run

### 1. Clone the repository

```bash
git clone https://github.com/HarishSNUC1402/DL-Lab-33.git
cd DL-Lab-33/Lab-7-33
```

### 2. Create an isolated Python environment

Python 3.10-3.12 is recommended. Using a virtual environment prevents the
experiment's packages from affecting other projects.

**Windows PowerShell**

```powershell
py -3.12 -m venv .venv
.\.venv\Scripts\Activate.ps1
```

**macOS/Linux**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
python -m pip install tensorflow numpy pandas matplotlib scikit-image jupyter
```

If TensorFlow is not available for the selected Python version or operating
system, use a supported Python environment or follow the installation
instructions in the [TensorFlow documentation](https://www.tensorflow.org/install).

### 4. Start Jupyter and run the notebook

```bash
jupyter notebook
```

Open `E7_final.ipynb` in the browser, then choose **Kernel > Restart Kernel
and Run All** (or run the cells from top to bottom). The first run downloads
MNIST and trains every model, so it can take several minutes and requires
additional memory. A GPU is helpful but not required; TensorFlow falls back to
the CPU automatically.

The notebook displays the metrics and figures inline. The committed images in
the `plots` directory are reference outputs; rerunning the notebook may
produce slightly different values because of TensorFlow, hardware, or package
version differences.

## Reproducibility

The notebook sets NumPy and TensorFlow random seeds to `42` and uses fixed
dataset prefixes (`10,000` training and `2,000` test images). Exact numerical
results are not guaranteed across CPU/GPU devices or TensorFlow versions.

