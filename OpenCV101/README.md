# OpenCV 101 - Fundamentals

Introduction to basic OpenCV operations and image manipulation techniques. This module covers the essential building blocks of computer vision.

## 📚 Modules

### 1. [Loading Images](opencv-load-image/)
Learn how to load and display images using OpenCV.
- Loading images from disk
- Displaying images in windows
- Basic image properties (width, height, channels)

### 2. [Getting and Setting Pixels](opencv-getting-setting/)
Direct pixel manipulation and accessing pixel values.
- Accessing individual pixel values
- Modifying pixel intensities
- Understanding image coordinate systems

### 3. [Image Arithmetic](opencv-image-arithmetic/)
Perform mathematical operations on images.
- Addition and subtraction
- Multiplication and division
- Image brightening and darkening
- Blending images

### 4. [Bitwise Operations](opencv-bitwise/)
Master bitwise AND, OR, XOR, and NOT operations.
- Creating and applying masks
- Combining images with bitwise operations
- Practical applications

### 5. [Masking](opencv-masking/)
Apply masks to extract regions of interest.
- Creating circular and rectangular masks
- Bit masking for selective image processing
- Isolating specific regions

### 6. [Channel Splitting and Merging](opencv-split-merge/)
Understand and manipulate color channels.
- Splitting images into R, G, B channels
- Analyzing individual channels
- Merging modified channels

### 7. [Resizing Images](opencv-resizing/)
Resize images while maintaining or modifying aspect ratios.
- Interpolation methods
- Aspect ratio preservation
- Downscaling and upscaling

### 8. [Rotating Images](opencv-rotate/)
Rotate images by arbitrary angles.
- Rotation matrices
- Center of rotation
- Handling rotated image boundaries

### 9. [Flipping Images](opencv-flipping/)
Flip images horizontally, vertically, or both.
- Horizontal flips (mirror)
- Vertical flips
- Combined flips

### 10. [Translating Images](opencv-translate/)
Shift images in x and y directions.
- Translation matrices
- Image shifting
- Border handling

### 11. [Cropping Images](opencv-cropping/)
Extract rectangular regions from images.
- Array slicing for cropping
- Region of interest (ROI) extraction
- Practical cropping examples

### 12. [Drawing on Images](opencv-drawing/)
Draw shapes, lines, and text on images.
- Drawing lines, rectangles, circles
- Adding text annotations
- Creating visualizations

## 🚀 Getting Started

### Prerequisites
```bash
pip install opencv-python numpy matplotlib
```

### Running Examples

#### Python Scripts
```bash
cd opencv-load-image
python load_image_opencv.py
```

#### Jupyter Notebooks
```bash
jupyter notebook
# Open any .ipynb file in the browser
```

## 📖 Learning Path

**Recommended Order:**
1. **Load Image** - Start here to understand basics
2. **Getting/Setting Pixels** - Learn pixel-level operations
3. **Image Arithmetic** - Understand mathematical operations
4. **Bitwise Operations & Masking** - Master selective processing
5. **Split/Merge Channels** - Work with color spaces
6. **Geometric Transformations** - Resizing, rotating, flipping, translating, cropping
7. **Drawing** - Add annotations and visualizations

## 💡 Key Concepts

- **Image Representation**: Images as NumPy arrays
- **Color Spaces**: RGB, BGR, Grayscale
- **Coordinates**: (x, y) vs (row, col)
- **Channels**: Working with multi-channel images
- **Transformations**: Affine and geometric operations

## 🛠️ Common Operations

```python
import cv2
import numpy as np

# Load an image
image = cv2.imread('image.jpg')

# Display image
cv2.imshow('Image', image)
cv2.waitKey(0)

# Get dimensions
(h, w, c) = image.shape

# Access pixel
pixel = image[100, 50]

# Modify pixel
image[100, 50] = [255, 0, 0]

# Resize
resized = cv2.resize(image, (300, 300))

# Rotate
(h, w) = image.shape[:2]
center = (w // 2, h // 2)
M = cv2.getRotationMatrix2D(center, 45, 1.0)
rotated = cv2.warpAffine(image, M, (w, h))
```

## 📝 Practice Projects

1. **Photo Editor**: Combine multiple operations to build a simple photo editor
2. **Logo Overlay**: Use masking to overlay a logo on images
3. **Image Grid**: Arrange multiple images in a grid layout
4. **Color Channel Analyzer**: Visualize individual color channels

## 🎯 Next Steps

After completing OpenCV 101, move on to:
- **OpenCV 102** - Intermediate techniques (filtering, edge detection, thresholding)
- **OpenCV 103** - Advanced processing (histograms, color correction)

---

Happy learning! 🎓
