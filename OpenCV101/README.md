# OpenCV 101

Core OpenCV fundamentals for image I/O, pixel operations, masking, channels, and geometric transforms.

## Modules

- [opencv-load-image](opencv-load-image/): image loading and display
- [opencv-getting-setting](opencv-getting-setting/): pixel access and updates
- [opencv-image-arithmetic](opencv-image-arithmetic/): arithmetic operations
- [opencv-bitwise](opencv-bitwise/): bitwise logic and masking basics
- [opencv-masking](opencv-masking/): region-of-interest masking
- [opencv-split-merge](opencv-split-merge/): channel split and merge
- [opencv-resizing](opencv-resizing/): resizing and interpolation
- [opencv-rotate](opencv-rotate/): rotation transforms
- [opencv-flipping](opencv-flipping/): horizontal and vertical flips
- [opencv-translate](opencv-translate/): translation transforms
- [opencv-cropping](opencv-cropping/): ROI extraction
- [opencv-drawing](opencv-drawing/): drawing primitives and text

## Setup

```bash
pip install -r ../requirements.txt
```

## Run

```bash
cd opencv-load-image
python load_image_opencv.py
```

```bash
jupyter notebook
```

## Recommended Order

1. load-image
2. getting-setting
3. image-arithmetic
4. bitwise and masking
5. split-merge
6. resizing, rotate, flipping, translate, cropping
7. drawing
