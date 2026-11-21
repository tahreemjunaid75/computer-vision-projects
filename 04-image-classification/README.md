# MNIST and Pet Image CNN Comparisons

![Python-3.10%2B](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=flat-square) ![TensorFlow/Keras](https://img.shields.io/badge/TensorFlow%2FKeras-blueviolet?style=flat-square) ![NumPy](https://img.shields.io/badge/NumPy-blueviolet?style=flat-square) ![Matplotlib](https://img.shields.io/badge/Matplotlib-blueviolet?style=flat-square) ![scikit-learn](https://img.shields.io/badge/scikit-learn-blueviolet?style=flat-square) ![TensorFlow Datasets](https://img.shields.io/badge/TensorFlow%20Datasets-blueviolet?style=flat-square) ![pandas](https://img.shields.io/badge/pandas-blueviolet?style=flat-square) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/04-image-classification/MNIST_Digit_Classification.ipynb)

## Overview

The notebook contains two classification studies: fully connected/CNN/augmented CNN models on a balanced MNIST subset, followed by basic, deeper, and wider CNN comparisons on Oxford-IIIT Pet. It demonstrates how architecture and training behavior differ across grayscale digits and 37-class natural images.

## Methodology & Pipeline

- **Dataset/Input Data:** MNIST balanced subset: 1,000 training examples (100 per digit), 200 test examples (20 per digit), with an 800/200 train/validation split. The later Oxford-IIIT Pet experiment uses 37 classes with official train/test data and an 80/20 split of the training partition.
- **Preprocessing:** MNIST grayscale values are normalized to [0,1] and channel-expanded; training augmentation uses random rotation/translation (0.08), zoom +/-0.1, contrast 0.2, and horizontal flip. Pet images resize to 64x64, normalize to [0,1], and batch/prefetch at 32.
- **Model/Algorithm:** MNIST dense baseline (128 ReLU, dropout 0.2, 10-way softmax), CNN (3x3 conv, 16/32 filters, max pooling, 64-unit dense head), and augmented CNN. Pet task compares basic, deeper, and wider from-scratch CNNs with 3x3 convolutions and 2x2 pooling.
- **Hyperparameters/Key Parameters:** MNIST models use Adam and sparse categorical cross-entropy, up to 15 epochs, batch 32; early stopping monitors `val_loss` (patience 3, restore best weights), though the augmented fit call leaves callbacks commented out. Pet models train 10 epochs, batch 32, input 64x64.

## Key Results & Observations

- **MNIST test:** dense loss 0.4546 / accuracy 0.890; basic CNN loss 0.2150 / accuracy 0.945; augmented CNN loss 0.3586 / accuracy 0.880. **Oxford-IIIT Pet test:** basic CNN 12.59% accuracy / loss 3.37; deeper 9.54% / 4.32; wider 11.28% / 4.38. Basic CNN performed best in each study.
- **Limitations / next steps:** MNIST uses only 200 test digits, so metrics have sampling variance; augmentation lowered MNIST test accuracy in this run. Pet CNNs substantially overfit, suggesting stronger regularization, transfer learning, and more training data.

## How to Run

- Open the [notebook](./MNIST_Digit_Classification.ipynb) in Jupyter or [Google Colab](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/04-image-classification/MNIST_Digit_Classification.ipynb).
- From this project directory, install the repository dependencies with `pip install -r ../requirements.txt`, then run the notebook cells in order. Several notebooks expect datasets, images, or videos to be downloaded or supplied at the paths documented above.

## References & Credits

- MNIST via `tf.keras.datasets.mnist`; TensorFlow/Keras and scikit-learn split/evaluation utilities.
