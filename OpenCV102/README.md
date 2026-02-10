# OpenCV 102 - Intermediate Techniques

Advanced image processing including edge detection, filtering, morphological operations, and thresholding. Build upon OpenCV 101 fundamentals to perform sophisticated image analysis.

## 📚 Modules

### 1. [Smoothing and Blurring](smoothing-and-blurring/)
Remove noise and smooth images using various filtering techniques.
- **Averaging/Box Blur**: Simple averaging filter
- **Gaussian Blur**: Weighted averaging with Gaussian kernel
- **Median Blur**: Non-linear filter for salt-and-pepper noise
- **Bilateral Filter**: Edge-preserving smoothing

**Use Cases**: Noise reduction, preprocessing for edge detection, image enhancement

### 2. [Thresholding](opencv-thresholding/)
Convert grayscale images to binary images.
- **Simple Thresholding**: Basic binary conversion
- **Otsu's Method**: Automatic threshold calculation
- **Inverse Thresholding**: Inverted binary images

**Use Cases**: Object segmentation, document scanning, foreground extraction

### 3. [Adaptive Thresholding](adapative-thresholding/)
Apply localized thresholding for varying lighting conditions.
- **Mean Adaptive**: Threshold based on local mean
- **Gaussian Adaptive**: Weighted threshold calculation
- **Block size and C parameter tuning**

**Use Cases**: Document scanning with uneven lighting, QR code detection

### 4. [Color Spaces](opencv-color-spaces/)
Convert between different color representations.
- **RGB ↔ Grayscale**
- **BGR ↔ HSV** (Hue, Saturation, Value)
- **BGR ↔ LAB** (Lightness, A, B)
- Color-based object tracking

**Use Cases**: Color-based segmentation, skin detection, object tracking

### 5. [Image Gradients](image-gradients/)
Detect edges by calculating intensity changes.
- **Sobel Operator**: Gradient in X and Y directions
- **Scharr Operator**: Improved accuracy over Sobel
- **Gradient Magnitude**: Combined gradient strength
- **Gradient Orientation**: Direction of edges

**Use Cases**: Edge detection, texture analysis, feature extraction

### 6. [Canny Edge Detector](canny-edge-detector/)
Industry-standard edge detection algorithm.
- Multi-stage edge detection process
- Non-maximum suppression
- Hysteresis thresholding
- Parameter tuning (min/max thresholds)

**Use Cases**: Object boundaries, shape detection, image segmentation

### 7. [Auto Canny](auto-canny/)
Automatically determine optimal Canny edge detection parameters.
- Automatic threshold calculation
- Adaptive edge detection
- Median-based threshold selection

**Use Cases**: Automated image processing pipelines

### 8. [Convolutions](convolutions-opencv/)
Apply custom kernels for image filtering.
- Understanding convolution operations
- Custom kernel design
- Sharpening, blurring, edge detection kernels
- Embossing effects

**Use Cases**: Custom filters, image effects, feature detection

### 9. [Morphological Operations](morphological-operations/)
Structural operations on binary images.
- **Erosion**: Shrink foreground regions
- **Dilation**: Expand foreground regions
- **Opening**: Remove noise (erosion → dilation)
- **Closing**: Fill holes (dilation → erosion)
- **Gradient**: Edge detection
- **Top Hat & Black Hat**: Highlight features

**Use Cases**: Noise removal, shape extraction, feature enhancement

## 🚀 Getting Started

### Prerequisites
```bash
pip install opencv-python numpy matplotlib imutils
```

### Running Examples

#### Python Scripts
```bash
cd smoothing-and-blurring
python blurring.py
```

#### Jupyter Notebooks
```bash
jupyter notebook
# Open any .ipynb file
```

## 📖 Learning Path

**Recommended Progression:**

1. **Color Spaces** - Understand different representations
2. **Smoothing & Blurring** - Noise reduction techniques
3. **Thresholding** - Binary image conversion
4. **Adaptive Thresholding** - Handle varying lighting
5. **Image Gradients** - Understand edge fundamentals
6. **Canny Edge Detection** - Complete edge detection
7. **Auto Canny** - Automate edge detection
8. **Convolutions** - Custom filtering
9. **Morphological Operations** - Refine binary images

## 💡 Key Concepts

### Filtering Operations
- **Linear Filters**: Averaging, Gaussian blur
- **Non-linear Filters**: Median filter
- **Edge-Preserving**: Bilateral filter

### Edge Detection Pipeline
1. Noise reduction (blurring)
2. Gradient calculation
3. Non-maximum suppression
4. Edge tracking by hysteresis

### Morphological Operations
- **Structuring Element**: Defines operation shape/size
- **Iterations**: Control operation strength
- **Combining Operations**: Create complex effects

## 🛠️ Common Techniques

```python
import cv2
import numpy as np

# Load and convert to grayscale
image = cv2.imread('image.jpg')
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Blur to reduce noise
blurred = cv2.GaussianBlur(gray, (5, 5), 0)

# Apply Canny edge detection
edges = cv2.Canny(blurred, 50, 150)

# Thresholding
ret, thresh = cv2.threshold(gray, 127, 255, cv2.THRESH_BINARY)

# Adaptive thresholding
adaptive = cv2.adaptiveThreshold(gray, 255, 
    cv2.ADAPTIVE_THRESH_GAUSSIAN_C, cv2.THRESH_BINARY, 11, 2)

# Morphological operations
kernel = np.ones((5,5), np.uint8)
opening = cv2.morphologyEx(thresh, cv2.MORPH_OPEN, kernel)
closing = cv2.morphologyEx(thresh, cv2.MORPH_CLOSE, kernel)

# Color space conversion
hsv = cv2.cvtColor(image, cv2.COLOR_BGR2HSV)
```

## 📝 Practice Projects

1. **Document Scanner**: Threshold and edge detection for document processing
2. **Shape Detector**: Combine edge detection with contour analysis
3. **Color-Based Tracker**: Segment objects by color in HSV space
4. **Noise Reducer**: Compare different blurring techniques
5. **Edge Comparison Tool**: Compare Sobel, Scharr, and Canny

## 🎯 Real-World Applications

- **Document Processing**: Adaptive thresholding, morphology
- **Medical Imaging**: Edge detection, gradient analysis
- **Industrial Quality Control**: Defect detection with edges
- **Autonomous Vehicles**: Lane detection with Canny edges
- **OCR Preprocessing**: Thresholding, noise removal

## 🔗 Prerequisites

Complete **OpenCV 101** before starting this module. You should be comfortable with:
- Loading and displaying images
- Image dimensions and coordinates
- Basic transformations
- Pixel-level operations

## 🎯 Next Steps

After completing OpenCV 102, continue to:
- **OpenCV 103** - Advanced processing (histograms, gamma correction, color matching)
- **DeepLearning 101** - Machine learning for computer vision

---

Happy learning! 🎓
