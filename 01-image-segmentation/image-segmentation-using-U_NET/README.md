# Oxford-IIIT Pet Semantic Segmentation with TensorFlow U-Net

![Python-3.10%2B](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=flat-square) ![TensorFlow](https://img.shields.io/badge/TensorFlow-blueviolet?style=flat-square) ![TensorFlow Datasets](https://img.shields.io/badge/TensorFlow%20Datasets-blueviolet?style=flat-square) ![NumPy](https://img.shields.io/badge/NumPy-blueviolet?style=flat-square) ![Matplotlib](https://img.shields.io/badge/Matplotlib-blueviolet?style=flat-square) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/01-image-segmentation/image-segmentation-using-U_NET/Image_Segmentation_using_U_Net_built_with_TensorFlow_Keras.ipynb)

## Overview

This semantic segmentation project trains a custom TensorFlow U-Net on Oxford-IIIT Pet images to predict foreground, background, and boundary masks. It reports independent test accuracy, loss, and mean IoU.

## Methodology & Pipeline

- **Dataset/Input Data:** Oxford-IIIT Pet `4.*.*`: 3,680 train images and 3,669 original test images; split the latter deterministically into 1,834 validation and 1,835 test images (seed 42).
- **Preprocessing:** Resize RGB images and masks to 128 x 128; nearest-neighbor mask resizing; image values scaled to [0,1], mask labels shifted from 1-3 to 0-2. Training-only horizontal flip (p=0.5) and brightness jitter +/-0.1. Shuffle buffer 1,000; batch 32; AUTOTUNE map/prefetch.
- **Model/Algorithm:** Four-level encoder/decoder U-Net, two 3x3 same-padded He-normal Conv2D + BatchNorm + ReLU per block; encoder filters 32/64/128/256, 2x2 max pooling; 512-filter bottleneck; transposed-convolution upsampling and skips; 1x1 softmax with 3 classes (~7,771,939 total parameters).
- **Hyperparameters/Key Parameters:** Adam 1e-3; sparse categorical cross-entropy; pixel accuracy and custom 3-class MeanIoU. Up to 30 epochs, batch 32. Checkpoint best `val_mean_iou`; ReduceLROnPlateau factor 0.5/patience 3 and EarlyStopping patience 3 on validation loss.

## Key Results & Observations

- Independent test: accuracy 0.8940, loss 0.2815, mean IoU 0.7329.
- **Limitations / next steps:** The notebook reports aggregate pixel scores and visualizes five predictions; no per-class IoU is printed. The reduced 128 x 128 input limits boundary detail.

## How to Run

- Open the [notebook](./Image_Segmentation_using_U_Net_built_with_TensorFlow_Keras.ipynb) in Jupyter or [Google Colab](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/01-image-segmentation/image-segmentation-using-U_NET/Image_Segmentation_using_U_Net_built_with_TensorFlow_Keras.ipynb).
- From this project directory, install the repository dependencies with `pip install -r ../../requirements.txt`, then run the notebook cells in order. Several notebooks expect datasets, images, or videos to be downloaded or supplied at the paths documented above.

## References & Credits

- Oxford-IIIT Pet via TensorFlow Datasets (`oxford_iiit_pet:4.*.*`); TensorFlow/Keras U-Net implementation.
