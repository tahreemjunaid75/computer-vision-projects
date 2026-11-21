# Motion Estimation and Optical Flow

![Python-3.10%2B](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=flat-square) ![OpenCV](https://img.shields.io/badge/OpenCV-blueviolet?style=flat-square) ![NumPy](https://img.shields.io/badge/NumPy-blueviolet?style=flat-square) ![Matplotlib](https://img.shields.io/badge/Matplotlib-blueviolet?style=flat-square) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/07-motion-estimation/Optical_Flow_and_Motion_Estimation_in_Computer_Vision.ipynb)

## Overview

Studies image motion from a video frame pair using block matching, sparse and dense optical flow, and the optical-flow constraint. The notebook visualizes moving regions and compares full-vector estimates with the aperture-limited normal flow.

## Methodology & Pipeline

- **Dataset/Input Data:** Notebook attempts to download `vtest.avi`; otherwise asks for a local video such as `vtest.avi` or `traffic.mp4`. Saved output indicates the upload/download fallback prompt appeared, so no reproducible final motion metrics are recorded.
- **Preprocessing:** Read adjacent video frames, resize to a target width while preserving aspect ratio, convert to grayscale; some flow algorithms operate on downsampled and Gaussian-smoothed images.
- **Model/Algorithm:** SSD/SAD block matching; least-squares flow; Lucas-Kanade sparse flow; Farneback dense flow; custom Horn-Schunck; thresholded frame difference and morphology for motion mask.
- **Hyperparameters/Key Parameters:** Farneback: pyr_scale 0.5, levels 3, winsize 21, iterations 3, poly_n 5, poly_sigma 1.2. Sparse LK: maxCorners 300, qualityLevel 0.01, minDistance 8, termination 30 iterations / 0.01. Horn-Schunck: alpha 10, 300 iterations. Motion-mask threshold is varied (notebook uses 70 and 20 in separate sections).

## Key Results & Observations

- Notebook includes printed summaries for block displacement, tracked features and flow magnitude when video is available; saved outputs here do not contain numeric values because the input video was unavailable.
- **Limitations / next steps:** Results depend on supplying the video and selecting frames/regions; brightness constancy, small-motion, and aperture assumptions limit classic flow methods.

## How to Run

- Open the [notebook](./Optical_Flow_and_Motion_Estimation_in_Computer_Vision.ipynb) in Jupyter or [Google Colab](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/07-motion-estimation/Optical_Flow_and_Motion_Estimation_in_Computer_Vision.ipynb).
- From this project directory, install the repository dependencies with `pip install -r ../requirements.txt`, then run the notebook cells in order. Several notebooks expect datasets, images, or videos to be downloaded or supplied at the paths documented above.

## References & Credits

- OpenCV VideoCapture and optical-flow APIs; sample video vtest.avi / traffic.mp4 if provided.
