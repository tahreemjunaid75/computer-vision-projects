# MNIST and Pet Image CNN Comparisons

![Python-3.10%2B](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=flat-square) ![TensorFlow/Keras](https://img.shields.io/badge/TensorFlow%2FKeras-blueviolet?style=flat-square) ![TensorFlow Datasets](https://img.shields.io/badge/TensorFlow%20Datasets-blueviolet?style=flat-square) ![NumPy](https://img.shields.io/badge/NumPy-blueviolet?style=flat-square) ![Matplotlib](https://img.shields.io/badge/Matplotlib-blueviolet?style=flat-square) ![scikit-learn](https://img.shields.io/badge/scikit-learn-blueviolet?style=flat-square) ![pandas](https://img.shields.io/badge/pandas-blueviolet?style=flat-square) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/05-deep-learning-with-tensorflow-keras/Computer_Vision_and_Deep_Learning_using_TensorFlow_and_Keras.ipynb)

## Overview

The notebook contains a balanced MNIST benchmark (dense, basic CNN, and augmented CNN) and a separate three-architecture CNN benchmark on Oxford-IIIT Pet. It contrasts high accuracy on the small digit subset with the much harder 37-class pet classification task.

## Methodology & Pipeline

- **Dataset/Input Data:** MNIST balanced subset (1,000 training images, 100 per digit; 200 test images, 20 per digit; 800/200 train/validation split), followed by Oxford-IIIT Pet via TensorFlow Datasets (37 classes; 80/20 training/validation split plus official test split).
- **Preprocessing:** MNIST is normalized to [0,1] and channel-expanded; augmentation uses rotation/translation 0.08, zoom +/-0.1, contrast 0.2, and horizontal flip. Pet images resize to 64x64 and normalize to [0,1]; batches of 32 use AUTOTUNE prefetch.
- **Model/Algorithm:** MNIST dense network (128 ReLU, dropout 0.2), basic CNN (3x3 conv layers with 16/32 filters, pooling, 64-unit dense head), and augmented CNN. Pet task compares basic, deeper, and wider from-scratch CNNs with 3x3 convolutions and 2x2 pooling.
- **Hyperparameters/Key Parameters:** 10 epochs; batch 32; all three architectures trained and evaluated with the notebook's shared compile configuration.

## Key Results & Observations

- **MNIST test:** dense loss 0.4546 / accuracy 0.890; basic CNN loss 0.2150 / accuracy 0.945; augmented CNN loss 0.3586 / accuracy 0.880. **Pet test:** basic CNN train/validation/test accuracy 33.97%/11.82%/12.59%, loss 3.37, 531,845 parameters; deeper 50.51%/8.97%/9.54%, loss 4.32, 1,074,629 parameters; wider 68.68%/11.96%/11.28%, loss 4.38, 1,070,437 parameters.
- **Limitations / next steps:** The 200-image MNIST test is small, and augmentation lowered accuracy in this run. Pet models generalize poorly across 37 classes: training accuracy rises while validation/test remain near chance, indicating overfitting and a need for transfer learning or stronger regularization.

## How to Run

- Open the [notebook](./Computer_Vision_and_Deep_Learning_using_TensorFlow_and_Keras.ipynb) in Jupyter or [Google Colab](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/05-deep-learning-with-tensorflow-keras/Computer_Vision_and_Deep_Learning_using_TensorFlow_and_Keras.ipynb).
- From this project directory, install the repository dependencies with `pip install -r ../requirements.txt`, then run the notebook cells in order. Several notebooks expect datasets, images, or videos to be downloaded or supplied at the paths documented above.

## References & Credits

- MNIST via `tf.keras.datasets`; Oxford-IIIT Pet via TensorFlow Datasets; TensorFlow/Keras.
