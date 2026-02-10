# OpenCV 103 - Advanced Processing

Professional-level image enhancement and analysis techniques including histogram operations, color correction, and advanced image quality assessment.

## 📚 Modules

### 1. [Image Histograms](opencv-image-histograms/)
Understand and analyze pixel intensity distributions.
- **Grayscale Histograms**: Single-channel intensity distribution
- **Color Histograms**: Multi-channel RGB/HSV histograms
- **Histogram Properties**: Mean, variance, distribution analysis
- **Histogram Comparison**: Measuring image similarity

**Use Cases**: Image analysis, quality assessment, exposure evaluation

### 2. [Histogram Equalization](opencv-histogram-equalization/)
Enhance image contrast using histogram manipulation.
- **Standard Equalization**: Global contrast enhancement
- **CLAHE**: Contrast Limited Adaptive Histogram Equalization
- **Per-Channel Equalization**: RGB vs HSV approaches
- **Comparing Techniques**: Before/after analysis

**Use Cases**: Low-contrast images, medical imaging, photo enhancement

### 3. [Gamma Correction](gamma-correction/)
Non-linear brightness adjustment for display calibration.
- **Gamma Values**: < 1 (brighten), > 1 (darken)
- **Lookup Tables**: Fast gamma transformation
- **Perceptual Brightness**: Human vision considerations
- **Display Calibration**: Consistent image rendering

**Use Cases**: Display correction, HDR imaging, exposure adjustment

### 4. [Color Correction](opencv-color-correction/)
Adjust color balance and white balance.
- **White Balance Algorithms**: Gray world, perfect reflector
- **Color Temperature Adjustment**: Warm/cool correction
- **Channel-wise Correction**: Individual RGB adjustments
- **Reference-based Correction**: Match to known colors

**Use Cases**: Photography, film processing, product photography

### 5. [Color Matching](opencv-color-matching/)
Transfer color palettes between images.
- **Mean and Standard Deviation Transfer**
- **LAB Color Space Matching**
- **Histogram Specification**
- **Style Transfer Basics**

**Use Cases**: Color grading, artistic effects, consistent styling

### 6. [Detect Low Contrast](detect-low-contrast/)
Automatically identify poor quality images.
- **Contrast Metrics**: RMS contrast, Michelson contrast
- **Laplacian Variance**: Sharpness measurement
- **Dynamic Range Analysis**: Histogram spread
- **Quality Scoring**: Automated image assessment

**Use Cases**: Quality control, automated filtering, preprocessing checks

## 🚀 Getting Started

### Prerequisites
```bash
pip install opencv-python numpy matplotlib scipy imutils
```

### Running Examples

#### Python Scripts
```bash
cd opencv-histogram-equalization
python histogram_equalization.py --image path/to/image.jpg
```

#### Jupyter Notebooks
```bash
jupyter notebook
# Open any .ipynb file
```

## 📖 Learning Path

**Recommended Progression:**

1. **Image Histograms** - Foundation for understanding distributions
2. **Histogram Equalization** - Basic contrast enhancement
3. **Gamma Correction** - Non-linear brightness adjustment
4. **Color Correction** - White balance and color adjustment
5. **Color Matching** - Advanced color transfer
6. **Detect Low Contrast** - Automated quality assessment

## 💡 Key Concepts

### Histograms
- **Bins**: Intensity value groupings (typically 256 for 8-bit)
- **Frequency**: Count of pixels at each intensity
- **Shape Analysis**: Understanding image characteristics
- **Equalization**: Spreading out intensity distribution

### Color Spaces for Processing
- **RGB**: Direct channel manipulation
- **HSV**: Separate brightness from color
- **LAB**: Perceptually uniform, ideal for color matching
- **Grayscale**: Single-channel processing

### Contrast Enhancement
- **Global Methods**: Apply to entire image
- **Adaptive Methods**: Localized enhancement (CLAHE)
- **Gamma**: Non-linear adjustment
- **Histogram Stretching**: Expand limited range

## 🛠️ Common Techniques

```python
import cv2
import numpy as np

# Load image
image = cv2.imread('image.jpg')
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Calculate histogram
hist = cv2.calcHist([gray], [0], None, [256], [0, 256])

# Histogram equalization (grayscale)
equalized = cv2.equalizeHist(gray)

# CLAHE (Contrast Limited Adaptive Histogram Equalization)
clahe = cv2.createCLAHE(clipLimit=2.0, tileGridSize=(8,8))
cl_img = clahe.apply(gray)

# Gamma correction
def adjust_gamma(image, gamma=1.0):
    inv_gamma = 1.0 / gamma
    table = np.array([((i / 255.0) ** inv_gamma) * 255 
                      for i in np.arange(0, 256)]).astype("uint8")
    return cv2.LUT(image, table)

brightened = adjust_gamma(image, gamma=0.5)  # Brighten
darkened = adjust_gamma(image, gamma=2.0)    # Darken

# Detect low contrast
def detect_low_contrast(image, threshold=50):
    gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
    laplacian_var = cv2.Laplacian(gray, cv2.CV_64F).var()
    return laplacian_var < threshold

is_blurry = detect_low_contrast(image)

# Color correction (simple white balance)
def white_balance(img):
    result = cv2.cvtColor(img, cv2.COLOR_BGR2LAB)
    avg_a = np.average(result[:, :, 1])
    avg_b = np.average(result[:, :, 2])
    result[:, :, 1] = result[:, :, 1] - ((avg_a - 128) * (result[:, :, 0] / 255.0) * 1.1)
    result[:, :, 2] = result[:, :, 2] - ((avg_b - 128) * (result[:, :, 0] / 255.0) * 1.1)
    return cv2.cvtColor(result, cv2.COLOR_LAB2BGR)

corrected = white_balance(image)
```

## 📝 Practice Projects

1. **Photo Enhancement Tool**: Combine equalization, gamma, and color correction
2. **Batch Image Processor**: Automatically enhance image quality
3. **Quality Filter**: Detect and filter low-quality images
4. **Color Grading Tool**: Match colors across image sets
5. **Histogram Analyzer**: Visualize and compare image distributions
6. **Smart Auto-Enhance**: Automatically determine best enhancement

## 🎯 Real-World Applications

- **Photography**: Professional photo editing and enhancement
- **Medical Imaging**: Enhance X-rays, MRIs, ultrasounds
- **Satellite Imagery**: Enhance contrast in remote sensing
- **Surveillance**: Improve low-light footage
- **Film/Video**: Color grading and matching
- **E-commerce**: Consistent product photography
- **Quality Assurance**: Automated image quality checking

## 📊 Performance Considerations

- **CLAHE vs Standard Equalization**: CLAHE better for local details
- **LAB vs RGB**: LAB better for perceptual operations
- **Lookup Tables**: Fast gamma correction with LUTs
- **Histogram Calculation**: Use masks for region-specific analysis

## 🔗 Prerequisites

Complete **OpenCV 101** and **OpenCV 102** before this module. You should understand:
- Basic image operations
- Color spaces
- Filtering and blurring
- Thresholding techniques

## 🎯 Next Steps

After completing OpenCV 103, explore:
- **DeepLearning 101** - Machine learning for computer vision
- **TFODCourse** - Object detection with TensorFlow
- Advanced topics: HDR imaging, image stitching, 3D reconstruction

## 📚 Additional Resources

- **Histogram Matching**: Advanced technique for precise color transfer
- **Tone Mapping**: HDR to LDR conversion
- **Color Constancy**: Algorithms for illumination-invariant color
- **Dehazing**: Remove fog/haze from images

---

Happy learning! 🎓
