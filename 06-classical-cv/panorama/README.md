# SIFT Feature Matching and OpenCV Panorama Stitching

![Python-3.10%2B](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=flat-square) ![OpenCV](https://img.shields.io/badge/OpenCV-blueviolet?style=flat-square) ![NumPy](https://img.shields.io/badge/NumPy-blueviolet?style=flat-square) ![Matplotlib](https://img.shields.io/badge/Matplotlib-blueviolet?style=flat-square) ![scikit-image](https://img.shields.io/badge/scikit-image-blueviolet?style=flat-square) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/06-classical-cv/panorama/Feature_Detection%2C_Image_Matching%2C_and_Image_Stitching_%28Panorama_Creation%29.ipynb)

## Overview

This Python and OpenCV panorama pipeline matches SIFT descriptors between overlapping photographs and estimates a RANSAC homography to align and blend them. It also compares Harris corner detection and HOG descriptors.

## Methodology & Pipeline

- **Dataset/Input Data:** Two local overlapping photographs (`image1_path` and `cv2.png` in notebook); no external dataset.
- **Preprocessing:** Load image pair, convert to grayscale, detect Harris corners and SIFT descriptors; Lowe ratio filtering then RANSAC homography estimation. Warp first image and mask into a shared canvas; average overlapping pixels.
- **Model/Algorithm:** SIFT keypoints/descriptors with brute-force L2 k-NN matching, Lowe ratio 0.75, homography via `findHomography(..., RANSAC)`; Harris and HOG demonstrations.
- **Hyperparameters/Key Parameters:** Harris block/window parameters in notebook; response threshold 1% of max (also compared 1%, 5%, 10%); SIFT ratio 0.75; test rotation 30 degrees and scales 0.5x/1.5x.

## Key Results & Observations

- Primary pair: 695 and 774 SIFT keypoints, 348 good matches; RANSAC reports 348 inliers, 0 outliers (ratio 1.0). HOG vector length 25,668. A second pair yields 344 good matches, 338 inliers (98.26%).
- **Limitations / next steps:** The first pair's all-inlier result may reflect easy/near-duplicate overlap; panorama quality depends on sufficient shared texture and a single planar homography. Harris is not scale-invariant per notebook observation.

## How to Run

- Open the [notebook](./Feature_Detection%2C_Image_Matching%2C_and_Image_Stitching_%28Panorama_Creation%29.ipynb) in Jupyter or [Google Colab](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/06-classical-cv/panorama/Feature_Detection%2C_Image_Matching%2C_and_Image_Stitching_%28Panorama_Creation%29.ipynb).
- From this project directory, install the repository dependencies with `pip install -r ../../requirements.txt`, then run the notebook cells in order. Several notebooks expect datasets, images, or videos to be downloaded or supplied at the paths documented above.

## References & Credits

- OpenCV SIFT, BFMatcher, RANSAC homography, warpPerspective; scikit-image HOG.
