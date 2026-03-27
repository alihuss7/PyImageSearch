# OpenCV 103

Advanced image enhancement and quality analysis with histograms, correction pipelines, and color transfer.

## Modules

- [opencv-image-histograms](opencv-image-histograms/): grayscale and color histogram analysis
- [opencv-histogram-equalization](opencv-histogram-equalization/): equalization and CLAHE workflows
- [gamma-correction](gamma-correction/): gamma-based brightness correction
- [opencv-color-correction](opencv-color-correction/): white balance and color correction
- [opencv-color-matching](opencv-color-matching/): color transfer and matching methods
- [detect-low-contrast](detect-low-contrast/): image quality and contrast checks

## Setup

```bash
pip install -r ../requirements.txt
```

## Run

```bash
cd opencv-histogram-equalization
python simple_equalization.py
```

```bash
jupyter notebook
```

## Recommended Order

1. opencv-image-histograms
2. opencv-histogram-equalization
3. gamma-correction
4. opencv-color-correction
5. opencv-color-matching
6. detect-low-contrast
