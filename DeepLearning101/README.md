# DeepLearning 101 - Introduction to Machine Learning

Introduction to machine learning and deep learning for computer vision. Learn fundamental concepts by building your first image classifier.

## 📚 Project Overview

### [First Image Classifier](first-image-classifier/)

Build a complete image classification system from scratch using K-Nearest Neighbors (k-NN).

**What You'll Learn:**

- Loading and preprocessing image datasets
- Feature extraction and representation
- Machine learning classification algorithms
- Model evaluation and metrics
- Building reusable components

## 🎯 Project Structure

```
first-image-classifier/
├── first_image_classifier.ipynb  # Interactive tutorial
├── knn.py                         # Command-line classifier
├── dataset/                       # Image dataset
│   └── animals/                   # Sample dataset (cats, dogs, pandas)
└── pyimagesearch/                 # Custom modules
    ├── preprocessing/             # Image preprocessors
    └── datasets/                  # Dataset loaders
```

## 🚀 Getting Started

### Prerequisites

```bash
pip install opencv-python numpy scikit-learn imutils matplotlib
```

### Quick Start

#### Using Python Script

```bash
cd first-image-classifier

# Train and test with default parameters
python knn.py --dataset dataset/animals

# Specify number of neighbors
python knn.py --dataset dataset/animals --neighbors 3

# Use all CPU cores for faster processing
python knn.py --dataset dataset/animals --jobs -1
```

#### Using Jupyter Notebook

```bash
jupyter notebook first_image_classifier.ipynb
```

## 📖 Learning Modules

### 1. Understanding k-NN Classification

**K-Nearest Neighbors** is a simple yet powerful algorithm:

- No explicit "training" phase
- Classification based on nearest examples
- Distance metrics (Euclidean, Manhattan)
- Choosing optimal k value

**Pros:**

- Simple to understand and implement
- No training time
- Works well with small datasets

**Cons:**

- Slow prediction for large datasets
- Requires careful feature engineering
- Sensitive to irrelevant features

### 2. Image Preprocessing

Transform raw images into consistent format for classification.

**SimplePreprocessor:**

- Resize images to fixed dimensions
- Maintain consistent input size
- Handle different aspect ratios

```python
from pyimagesearch.preprocessing import SimplePreprocessor

sp = SimplePreprocessor(32, 32)  # Resize to 32x32
image = sp.preprocess(image)
```

### 3. Dataset Loading

Efficiently load and organize image datasets.

**SimpleDatasetLoader:**

- Load images from directory structure
- Extract labels from folder names
- Batch processing
- Progress tracking

```python
from pyimagesearch.datasets import SimpleDatasetLoader
from imutils import paths

# Get all image paths
imagePaths = list(paths.list_images("dataset/animals"))

# Load dataset
sdl = SimpleDatasetLoader(preprocessors=[sp])
(data, labels) = sdl.load(imagePaths, verbose=500)
```

### 4. Feature Representation

Raw pixel values as features (flatten 32x32x3 → 3072 features).

### 5. Train/Test Split

Divide data for validation:

````python
from sklearn.model_selection import train_test_split
# DeepLearning 101

Introductory machine learning module for image classification using a K-Nearest Neighbors baseline.

## Project

- [first-image-classifier](first-image-classifier/): end-to-end k-NN image classifier with script and notebook

## Setup

```bash
pip install -r ../requirements.txt
````

## Run

```bash
cd first-image-classifier
python knn.py --dataset dataset/animals --neighbors 3 --jobs -1
```

```bash
jupyter notebook first_image_classifier.ipynb
```

## Learning Scope

- dataset loading and label extraction
- preprocessing and fixed-size feature representation
- train and test split
- baseline classification with k-NN
- evaluation with precision, recall, F1-score, and accuracy

## Next Step

Use this baseline as the transition point to CNN-based models and transfer learning workflows.
pandas 0.62 0.58 0.60 254
