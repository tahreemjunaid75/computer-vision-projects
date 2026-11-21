# OpenCV Hough Circle and Line Detection

![Python-3.10%2B](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=flat-square) ![OpenCV](https://img.shields.io/badge/OpenCV-blueviolet?style=flat-square) ![NumPy](https://img.shields.io/badge/NumPy-blueviolet?style=flat-square) ![Matplotlib](https://img.shields.io/badge/Matplotlib-blueviolet?style=flat-square) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/06-classical-cv/Hough%20transformation/Hough_Transforms_%28Feature_Extraction%29_in_computer_vision.ipynb)

## Overview

This Python and OpenCV Hough-transform workflow detects circular coin boundaries and straight road markings. It compares standard and probabilistic line detection and shows how circle-detection tuning changes the number of detections.

## Methodology & Pipeline

- **Dataset/Input Data:** Local notebook assets `coin.png` and `road2.png`.
- **Preprocessing:** Convert images to grayscale; apply 5x5 median blur for coin circles; detect road edges with Canny thresholds 50 and 150.
- **Model/Algorithm:** `cv2.HoughCircles` with HOUGH_GRADIENT; standard `cv2.HoughLines`; probabilistic `cv2.HoughLinesP`.
- **Hyperparameters/Key Parameters:** Circle detector is run once and again with tuned settings (values are in notebook code); line HoughLinesP threshold=100; Canny=(50,150).

## Key Results & Observations

- Saved outputs: initial circle pass detects 28 circles, tuned pass 11; standard Hough returns 208 lines and probabilistic Hough returns 44 line segments.
- **Limitations / next steps:** Counts vary strongly with thresholds and scene edges; tuning reduces circle detections substantially. No ground-truth precision/recall is calculated.

## How to Run

- Open the [notebook](./Hough_Transforms_%28Feature_Extraction%29_in_computer_vision.ipynb) in Jupyter or [Google Colab](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/06-classical-cv/Hough%20transformation/Hough_Transforms_%28Feature_Extraction%29_in_computer_vision.ipynb).
- From this project directory, install the repository dependencies with `pip install -r ../../requirements.txt`, then run the notebook cells in order. Several notebooks expect datasets, images, or videos to be downloaded or supplied at the paths documented above.

## References & Credits

- OpenCV Hough circle/line transform APIs.
