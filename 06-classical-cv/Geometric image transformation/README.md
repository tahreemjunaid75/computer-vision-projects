# OpenCV Affine and Perspective Image Transformations

![Python-3.10%2B](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=flat-square) ![OpenCV](https://img.shields.io/badge/OpenCV-blueviolet?style=flat-square) ![NumPy](https://img.shields.io/badge/NumPy-blueviolet?style=flat-square) ![Matplotlib](https://img.shields.io/badge/Matplotlib-blueviolet?style=flat-square) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/06-classical-cv/Geometric%20image%20transformation/Geometric_Image_Transformations.ipynb)

## Overview

This Python and OpenCV image-transformation project compares affine scale, rotation, and translation order, four 2x interpolation methods, and four-point perspective homography. Side-by-side outputs make geometric and interpolation effects easy to inspect.

## Methodology & Pipeline

- **Dataset/Input Data:** Notebook image loaded from a local path set in the notebook; no dataset name or saved numeric dimensions are reported in extracted outputs.
- **Preprocessing:** Load BGR with OpenCV and convert to RGB for visualization; define image-center and corner points for transforms.
- **Model/Algorithm:** OpenCV affine composition via 3x3 scale, rotation, and translation matrices followed by `warpAffine`; `resize` interpolation comparison; four-point homography with `getPerspectiveTransform` and `warpPerspective`.
- **Hyperparameters/Key Parameters:** Scale-up factor 2x; compare INTER_NEAREST, INTER_LINEAR, INTER_CUBIC, INTER_LANCZOS4. Affine orders: scale -> rotate -> translate, rotate -> scale -> translate, translate -> rotate -> scale.

## Key Results & Observations

- Notebook demonstrates that transformation composition order changes the output; interpolation methods trade pixelation against smoothness/detail. Homography output is visual; no quantitative metric is printed.
- **Limitations / next steps:** Point selection and qualitative visual comparison are manual; no geometric accuracy benchmark is calculated.

## How to Run

- Open the [notebook](./Geometric_Image_Transformations.ipynb) in Jupyter or [Google Colab](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/06-classical-cv/Geometric%20image%20transformation/Geometric_Image_Transformations.ipynb).
- From this project directory, install the repository dependencies with `pip install -r ../../requirements.txt`, then run the notebook cells in order. Several notebooks expect datasets, images, or videos to be downloaded or supplied at the paths documented above.

## References & Credits

- OpenCV geometric transforms and interpolation documentation (APIs used in notebook).
