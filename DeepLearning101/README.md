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
```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    data, labels, test_size=0.25, random_state=42
)
```

### 6. Model Training & Evaluation
```python
from sklearn.neighbors import KNeighborsClassifier
from sklearn.metrics import classification_report

# Train model
model = KNeighborsClassifier(n_neighbors=1, n_jobs=-1)
model.fit(X_train, y_train)

# Make predictions
predictions = model.predict(X_test)

# Evaluate
print(classification_report(y_test, predictions))
```

## 📊 Expected Output

```
[INFO] loading images...
[INFO] processed 500/3000
[INFO] processed 1000/3000
[INFO] processed 1500/3000
...

              precision    recall  f1-score   support

        cats       0.55      0.50      0.52       250
        dogs       0.50      0.58      0.54       246
      pandas       0.62      0.58      0.60       254

    accuracy                           0.55       750
   macro avg       0.56      0.55      0.55       750
weighted avg       0.56      0.55      0.55       750
```

## 💡 Key Concepts

### Supervised Learning
- **Training Data**: Labeled examples
- **Features**: Image pixel values
- **Labels**: Class categories
- **Model**: k-NN classifier

### Classification Metrics
- **Precision**: Correct positive predictions / Total positive predictions
- **Recall**: Correct positive predictions / Total actual positives
- **F1-Score**: Harmonic mean of precision and recall
- **Accuracy**: Overall correct predictions

### Dataset Organization
```
dataset/
└── animals/
    ├── cats/
    │   ├── cat_001.jpg
    │   ├── cat_002.jpg
    │   └── ...
    ├── dogs/
    │   ├── dog_001.jpg
    │   ├── dog_002.jpg
    │   └── ...
    └── pandas/
        ├── panda_001.jpg
        ├── panda_002.jpg
        └── ...
```

## 🛠️ Customization

### Using Your Own Dataset

1. **Organize Images:**
   ```
   dataset/
   └── my_dataset/
       ├── class1/
       ├── class2/
       └── class3/
   ```

2. **Run Classifier:**
   ```bash
   python knn.py --dataset dataset/my_dataset --neighbors 3
   ```

### Tuning Parameters

- **--neighbors**: Try values 1, 3, 5, 7 (odd numbers preferred)
- **Image size**: Modify SimplePreprocessor dimensions
- **Test split**: Adjust test_size in train_test_split

### Improving Accuracy

1. **More training data**: Larger dataset → better performance
2. **Better preprocessing**: Data augmentation, normalization
3. **Feature engineering**: Extract better features (HOG, SIFT)
4. **Try different k values**: Experiment with neighbors parameter
5. **Advanced models**: Neural networks (next steps)

## 📝 Practice Projects

1. **Custom Dataset Classifier**: Collect and classify your own images
2. **Parameter Tuning**: Find optimal k value for your dataset
3. **Feature Comparison**: Compare raw pixels vs HOG features
4. **Cross-Validation**: Implement k-fold cross-validation
5. **Confusion Matrix**: Visualize classification errors

## 🎯 Real-World Applications

- **Medical Diagnosis**: Classify medical images (X-rays, CT scans)
- **Quality Control**: Detect defective products
- **Agriculture**: Identify plant diseases
- **Wildlife**: Animal species identification
- **Fashion**: Clothing categorization

## 🔗 Prerequisites

Recommended but not required:
- **OpenCV 101** - Image loading and manipulation
- **OpenCV 102** - Preprocessing techniques
- Basic Python and NumPy knowledge

## 🎯 Next Steps

After completing DeepLearning 101, explore:

1. **Deep Neural Networks**: Move beyond k-NN to CNNs
2. **Transfer Learning**: Use pre-trained models (VGG, ResNet)
3. **TFODCourse**: Build object detection systems
4. **Advanced Topics**: 
   - Convolutional Neural Networks (CNNs)
   - Data augmentation
   - Regularization techniques
   - Fine-tuning strategies

## 📚 Additional Concepts to Explore

- **Feature Extraction**: HOG, SIFT, SURF
- **Dimensionality Reduction**: PCA, t-SNE
- **Other Classifiers**: SVM, Random Forest, Logistic Regression
- **Deep Learning Frameworks**: TensorFlow, PyTorch
- **Model Deployment**: Save and load trained models

## 🔬 Understanding k-NN Limitations

k-NN works well for:
- ✅ Small to medium datasets
- ✅ Low-dimensional features
- ✅ Quick prototyping

Not ideal for:
- ❌ Large-scale production systems
- ❌ High-dimensional data without feature engineering
- ❌ Real-time applications (slow prediction)

**Solution**: Move to deep learning (neural networks) for complex problems!

---

Happy learning! 🎓
