# Digital Image Processing with NumPy, SciPy, and scikit-image

![Python-3.10%2B](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=flat-square) ![NumPy](https://img.shields.io/badge/NumPy-blueviolet?style=flat-square) ![Pillow](https://img.shields.io/badge/Pillow-blueviolet?style=flat-square) ![SciPy](https://img.shields.io/badge/SciPy-blueviolet?style=flat-square) ![scikit-image](https://img.shields.io/badge/scikit-image-blueviolet?style=flat-square) ![Matplotlib](https://img.shields.io/badge/Matplotlib-blueviolet?style=flat-square) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/09-digital-image-processing-fundamentals/Digital_Image_Processing_%28or_Computer_Vision%29.ipynb)

## Overview

This Python image-processing workflow uses NumPy, SciPy, and scikit-image for grayscale translation, sharpening, smoothing, noise removal, Sobel edge detection, thresholding, and erosion. Its comparisons show how filter size affects detail and noise.

## Methodology & Pipeline

- **Dataset/Input Data:** Notebook inputs `/content/cartoon.png` and `/content/picturewithdetail.png`; first image output shape 407x424 (RGB 3 channels and grayscale).
- **Preprocessing:** Convert input images to grayscale; arrays use uint8 for initial image and float for filtering. Translation fills exposed pixels with black; filter outputs are clipped to [0,255].
- **Model/Algorithm:** NumPy translation; SciPy Gaussian/median filters and convolution; Sobel gradient magnitude; binary threshold and scikit-image erosion.
- **Hyperparameters/Key Parameters:** Translate left 10 px; Gaussian sigma 1 for mild smoothing (notebook text describes a strong sigma 8 blur, but code actually uses sigma=1); compare 3x3 sharpening kernel [[0,-1,0],[-1,5,-1],[0,-1,0]] and custom 5x5 center-20 kernel; box filters 3x3 and 9x9; salt/pepper RNG seed 42 with 2% salt and 2% pepper; median size 3; binary threshold 128; erosion footprint 3x3.

## Key Results & Observations

- Notebook observations: custom 5x5 produces stronger sharpening/noise tradeoff; 9x9 box filter destroys more fine detail than 3x3; median filtering removes most impulse noise while preserving main edges, and sharpening cannot restore detail lost to blur.
- **Limitations / next steps:** The notebook text requests sigma=8 but executed code uses sigma=1 in that cell; outputs are qualitative and no numeric image-quality metric is calculated.

## How to Run

- Open the [notebook](./Digital_Image_Processing_%28or_Computer_Vision%29.ipynb) in Jupyter or [Google Colab](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/09-digital-image-processing-fundamentals/Digital_Image_Processing_%28or_Computer_Vision%29.ipynb).
- From this project directory, install the repository dependencies with `pip install -r ../requirements.txt`, then run the notebook cells in order. Several notebooks expect datasets, images, or videos to be downloaded or supplied at the paths documented above.

## References & Credits

- SciPy ndimage; scikit-image morphology; Pillow image loading.
