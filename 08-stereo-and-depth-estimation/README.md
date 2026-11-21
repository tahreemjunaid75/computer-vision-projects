# Stereo Disparity and Depth Estimation with OpenCV

![Python-3.10%2B](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=flat-square) ![OpenCV](https://img.shields.io/badge/OpenCV-blueviolet?style=flat-square) ![NumPy](https://img.shields.io/badge/NumPy-blueviolet?style=flat-square) ![Matplotlib](https://img.shields.io/badge/Matplotlib-blueviolet?style=flat-square) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/08-stereo-and-depth-estimation/Stereo_Vision_and_Depth_Estimation_%28using_Block_Matching_SSD_Disparity%29_in_Computer_Vision.ipynb)

## Overview

This Python and OpenCV stereo-vision project estimates disparity by matching image patches with SSD windows, then converts disparity to depth using baseline and focal length. It compares window sizes and camera-parameter effects.

## Methodology & Pipeline

- **Dataset/Input Data:** Stereo pair loaded as grayscale from notebook paths (`CV.png` and `cv2.png` in the notebook); saved shapes are left (256,246) and right (258,249), so dimensions differ.
- **Preprocessing:** Resize the right image to left dimensions in the first helper; grayscale images; choose the middle scanline for epipolar visualization.
- **Model/Algorithm:** Custom sum-of-squared-differences (SSD) block matcher; depth formula Z = baseline x focal length / disparity.
- **Hyperparameters/Key Parameters:** Maximum disparity 30; compare 3x3 and 21x21 windows; baseline B=0.54 m and focal length f=721.5 px.

## Key Results & Observations

- With B=0.54 and f=721.5: disparities 5/10/20/30 yield 77.92/38.96/19.48/12.99 m. At disparity 20, baselines 0.30/0.54/1.00 m yield 10.82/19.48/36.08 m; focal lengths 500/721.5/1000 px yield 13.50/19.48/27.00 m.
- **Limitations / next steps:** No ground-truth depth error is reported. The later notebook section loads differently sized images (left 256x246, right 258x249) and its duplicate matcher does not resize them, so matching requires correcting dimensions first. SSD is slow and sensitive to texture, occlusion, and calibration.

## How to Run

- Open the [notebook](./Stereo_Vision_and_Depth_Estimation_%28using_Block_Matching_SSD_Disparity%29_in_Computer_Vision.ipynb) in Jupyter or [Google Colab](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/08-stereo-and-depth-estimation/Stereo_Vision_and_Depth_Estimation_%28using_Block_Matching_SSD_Disparity%29_in_Computer_Vision.ipynb).
- From this project directory, install the repository dependencies with `pip install -r ../requirements.txt`, then run the notebook cells in order. Several notebooks expect datasets, images, or videos to be downloaded or supplied at the paths documented above.

## References & Credits

- OpenCV image loading/resize; stereo depth relation described in notebook.
