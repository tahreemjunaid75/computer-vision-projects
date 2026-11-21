# OpenCV Edge Detection with Sobel, Laplacian, and Canny

![Python-3.10%2B](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=flat-square) ![OpenCV](https://img.shields.io/badge/OpenCV-blueviolet?style=flat-square) ![NumPy](https://img.shields.io/badge/NumPy-blueviolet?style=flat-square) ![Matplotlib](https://img.shields.io/badge/Matplotlib-blueviolet?style=flat-square) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/06-classical-cv/Image%20Edge%20detetction/Image_Edge_Detection_in_computer_vision.ipynb)

## Overview

This Python and OpenCV edge-detection project compares Sobel gradients, Laplacian responses, and Canny edges across smoothing and threshold settings. A manual non-maximum-suppression step demonstrates how to thin gradient responses.

## Methodology & Pipeline

- **Dataset/Input Data:** Local image path defined in notebook; no named public dataset.
- **Preprocessing:** Load image and convert to grayscale where needed; compare raw and Gaussian-smoothed inputs.
- **Model/Algorithm:** Sobel x/y gradients (3x3), Laplacian, Canny, manual gradient-based non-maximum suppression, and Laplacian before/after Gaussian blur.
- **Hyperparameters/Key Parameters:** Sobel ksize=3; Canny threshold pairs (100,200), then (50,100), (100,200), (150,300); Gaussian blur kernel 5x5, sigma=1.5.

## Key Results & Observations

- Qualitative outputs compare directional Sobel maps, Laplacian edges, NMS-thinned response, and Canny threshold variants; no numeric accuracy metric is reported.
- **Limitations / next steps:** Edge maps depend on image contrast and selected thresholds; no annotated edge ground truth is used.

## How to Run

- Open the [notebook](./Image_Edge_Detection_in_computer_vision.ipynb) in Jupyter or [Google Colab](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/06-classical-cv/Image%20Edge%20detetction/Image_Edge_Detection_in_computer_vision.ipynb).
- From this project directory, install the repository dependencies with `pip install -r ../../requirements.txt`, then run the notebook cells in order. Several notebooks expect datasets, images, or videos to be downloaded or supplied at the paths documented above.

## References & Credits

- OpenCV Sobel, Laplacian, Canny, GaussianBlur APIs.
