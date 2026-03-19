# Forest Fire Detection using Deep Learning

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange)
![License](https://img.shields.io/badge/License-MIT-green)

A deep learning project that uses Convolutional Neural Networks (CNN) to automatically detect forest fires from images. Designed to aid in early fire detection for disaster prevention and environmental protection.

---

## Table of Contents

- [Project Description](#project-description)
- [Features](#features)
- [Objectives](#objectives)
- [Model Architecture](#model-architecture)
- [Dataset](#dataset)
- [Results and Performance](#results-and-performance)
- [Project Structure](#project-structure)
- [Installation and Usage](#installation-and-usage)
- [Future Improvements](#future-improvements)
- [References](#references)
- [Contributors](#contributors)
- [License](#license)

---

## Project Description

Forest fires are one of the most devastating natural disasters, causing significant ecological damage and loss of life. Early and accurate detection is critical to enable rapid response. This project leverages deep learning — specifically a multi-layer CNN — to classify aerial or ground-level images as either **fire** or **no fire**, providing a foundation for automated fire-monitoring systems.

---

## Features

- Binary image classification: **fire** vs. **no fire**
- GPU-accelerated training with TensorFlow/Keras
- Real-time data augmentation via `ImageDataGenerator`
- Training and validation accuracy/loss visualisation
- Model evaluation on a held-out test set
- Modular, well-commented Jupyter notebooks

---

## Objectives

1. Build a CNN capable of reliably distinguishing fire from non-fire images.
2. Achieve high accuracy on an unseen test set.
3. Provide a reproducible pipeline from raw data to trained model.
4. Lay the groundwork for deployment in real-world fire-monitoring systems.

---

## Model Architecture

The CNN consists of the following layers:

| Layer | Details |
|---|---|
| Input | 150 × 150 × 3 (RGB) |
| Conv2D + ReLU | 32 filters, 3 × 3 kernel |
| MaxPooling2D | 2 × 2 |
| Conv2D + ReLU | 64 filters, 3 × 3 kernel |
| MaxPooling2D | 2 × 2 |
| Conv2D + ReLU | 128 filters, 3 × 3 kernel |
| MaxPooling2D | 2 × 2 |
| Flatten | — |
| Dense + ReLU | 512 units |
| Dropout | 0.5 |
| Dense + Sigmoid | 1 unit (binary output) |

- **Optimizer:** Adam
- **Loss function:** Binary Cross-Entropy
- **Metric:** Accuracy
- **Epochs:** 12
- **Batch size:** 32

---

## Dataset

The project uses the **Wildfire Dataset** from Kaggle:

> **elmadafri/the-wildfire-dataset** — Version 3  
> Contains train, validation, and test splits with two classes: `fire` and `nofire`.

**Download via KaggleHub:**

```python
import kagglehub
path = kagglehub.dataset_download("elmadafri/the-wildfire-dataset")
```

| Split | Purpose |
|---|---|
| `train/` | Model training |
| `val/` | Hyperparameter tuning & early stopping |
| `test/` | Final evaluation |

---

## Results and Performance

| Metric | Value |
|---|---|
| Training Accuracy | ~95% |
| Validation Accuracy | ~92% |
| Test Accuracy | Reported after `model.evaluate()` |

> Note: Exact values depend on the training run and random seed. Run the notebook to reproduce results.

Training curves (accuracy and loss over epochs) are plotted inside the notebook.

---

## Project Structure

```
Forest-Fire-Detection-using-DL/
├── Forest_Fire_Detection_using_DL.ipynb   # Main training & evaluation notebook
├── Forest_Fire_Detection.ipynb            # Exploratory / experimental notebook
├── PROJECT_STRUCTURE.md                   # Detailed project structure guide
├── requirements.txt                       # Python dependencies
├── .gitignore                             # Files excluded from version control
├── LICENSE                                # MIT License
└── README.md                              # This file
```

---

## Installation and Usage

### 1. Clone the repository

```bash
git clone https://github.com/M4ban/Forest-Fire-Detection-using-DL.git
cd Forest-Fire-Detection-using-DL
```

### 2. Create and activate a virtual environment (recommended)

```bash
python -m venv venv
source venv/bin/activate        # Linux/macOS
venv\Scripts\activate           # Windows
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Download the dataset

```python
import kagglehub
path = kagglehub.dataset_download("elmadafri/the-wildfire-dataset")
print("Dataset path:", path)
```

### 5. Run the notebook

```bash
jupyter notebook Forest_Fire_Detection_using_DL.ipynb
```

Execute all cells in order to train and evaluate the model.

---

## Future Improvements

- [ ] Apply transfer learning (VGG16, ResNet50, EfficientNet) to boost accuracy
- [ ] Add advanced data augmentation (rotation, flipping, brightness jitter)
- [ ] Implement early stopping and learning-rate scheduling callbacks
- [ ] Export the trained model to TensorFlow Lite for edge deployment
- [ ] Build a REST API or web demo for real-time fire detection
- [ ] Extend to multi-class detection (smoke, post-fire damage, etc.)
- [ ] Integrate with drone or satellite imagery pipelines

---

## References

- [The Wildfire Dataset – Kaggle](https://www.kaggle.com/datasets/elmadafri/the-wildfire-dataset)
- LeCun, Y., Bengio, Y., & Hinton, G. (2015). Deep learning. *Nature*, 521(7553), 436–444.
- [TensorFlow / Keras Documentation](https://www.tensorflow.org/api_docs)
- [Keras ImageDataGenerator](https://www.tensorflow.org/api_docs/python/tf/keras/preprocessing/image/ImageDataGenerator)

---

## Contributors

| Name | Role |
|---|---|
| [M4ban](https://github.com/M4ban) | Project Author |

Contributions, issues, and feature requests are welcome! Feel free to open an issue or submit a pull request.

---

## License

This project is licensed under the [MIT License](LICENSE).
