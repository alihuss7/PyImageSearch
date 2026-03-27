# OpenCV 102

Intermediate OpenCV workflows focused on filtering, thresholding, gradients, edges, and morphology.

## Modules

- [smoothing-and-blurring](smoothing-and-blurring/): averaging, Gaussian, median, bilateral filters
- [opencv-thresholding](opencv-thresholding/): simple and Otsu thresholding
- [adapative-thresholding](adapative-thresholding/): adaptive thresholding for uneven lighting
- [opencv-color-spaces](opencv-color-spaces/): BGR, grayscale, HSV, LAB conversions
- [image-gradients](image-gradients/): Sobel and Scharr gradients
- [canny-edge-detector](canny-edge-detector/): Canny edge detection pipeline
- [auto-canny](auto-canny/): automatic Canny threshold selection
- [convolutions-opencv](convolutions-opencv/): custom kernels and filtering
- [morphological-operations](morphological-operations/): erosion, dilation, opening, closing, hats

## Setup

```bash
pip install -r ../requirements.txt
```

## Run

```bash
cd smoothing-and-blurring
python blurring.py
```

```bash
jupyter notebook
```

## Recommended Order

1. color-spaces
2. smoothing-and-blurring
3. thresholding and adapative-thresholding
4. image-gradients
5. canny-edge-detector and auto-canny
6. convolutions-opencv
7. morphological-operations
