# Project Structure

This document describes the organisation of the **Forest Fire Detection using Deep Learning** project.

---

## Directory Layout

```
Forest-Fire-Detection-using-DL/
├── Forest_Fire_Detection_using_DL.ipynb   # Primary notebook
├── Forest_Fire_Detection.ipynb            # Experimental notebook
├── PROJECT_STRUCTURE.md                   # This file
├── requirements.txt                       # Python dependencies
├── .gitignore                             # Git exclusions
├── LICENSE                                # MIT License
└── README.md                              # Project overview
```

---

## Notebook Descriptions

### `Forest_Fire_Detection_using_DL.ipynb` — Main Notebook

The primary, end-to-end pipeline for training and evaluating the CNN model.

| Section | Description |
|---|---|
| **1. Dataset Download** | Downloads the Wildfire Dataset from Kaggle via `kagglehub` |
| **2. Imports** | Loads TensorFlow, Keras, NumPy, Matplotlib, and OS utilities |
| **3. GPU Configuration** | Enables memory growth on GPU if available |
| **4. Data Paths** | Sets `train_dir`, `val_dir`, and `test_dir` paths |
| **5. Class Exploration** | Lists classes and counts images per class |
| **6. Sample Visualisation** | Displays sample images for each class |
| **7. Data Pipeline** | Creates `ImageDataGenerator` objects; flows images from directories |
| **8. Class Mapping** | Prints class-index mapping for reference |
| **9. Model Definition** | Builds the Sequential CNN (see architecture in README) |
| **10. Model Compilation** | Adam optimiser, binary cross-entropy loss, accuracy metric |
| **11. Model Training** | Trains for 12 epochs; records `history` |
| **12. Accuracy Plot** | Plots training vs. validation accuracy over epochs |
| **13. Loss Plot** | Plots training vs. validation loss over epochs |
| **14. Test Evaluation** | Evaluates final model accuracy on the held-out test set |

### `Forest_Fire_Detection.ipynb` — Experimental Notebook

An exploratory notebook used for prototyping individual pipeline components (data loading, augmentation experiments, architecture search). May contain partial or draft code.

---

## Data Pipeline

```
Raw Images (Kaggle)
        │
        ▼
kagglehub.dataset_download()
        │
        ▼
  Directory Structure
  ├── train/
  │   ├── fire/
  │   └── nofire/
  ├── val/
  │   ├── fire/
  │   └── nofire/
  └── test/
      ├── fire/
      └── nofire/
        │
        ▼
ImageDataGenerator (rescale=1./255)
        │
        ▼
flow_from_directory()
  target_size=(150, 150)
  batch_size=32
  class_mode='binary'
        │
        ▼
  CNN Model Training / Evaluation
```

---

## Adding New Notebooks

When adding new notebooks to this project, please follow these conventions:

1. **Name** the notebook descriptively using `Snake_Case`.
2. **Document** each section with a Markdown cell heading.
3. **Add an entry** to the table in this file explaining the notebook's purpose.
4. **Clear all outputs** before committing (`Kernel → Restart & Clear Output`).
