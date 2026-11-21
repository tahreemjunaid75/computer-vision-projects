# Transfer Learning and Fine-Tuning of Pretrained CNNs

![Python-3.10%2B](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=flat-square) ![TensorFlow/Keras](https://img.shields.io/badge/TensorFlow%2FKeras-blueviolet?style=flat-square) ![NumPy](https://img.shields.io/badge/NumPy-blueviolet?style=flat-square) ![Matplotlib](https://img.shields.io/badge/Matplotlib-blueviolet?style=flat-square) ![scikit-learn](https://img.shields.io/badge/scikit-learn-blueviolet?style=flat-square) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/03-transfer-learning/Transfer_Learning_and_Fine_Tuning_using_Pretrained_Deep_Convolutional_Neural_Networks_%28CNNs%29.ipynb)

## Overview

The notebook has two transfer-learning studies: DenseNet121 on MNIST, then VGG16, ResNet50, MobileNetV2, and DenseNet121 on CIFAR-10. Each study replaces the ImageNet classifier with a task-specific head, then fine-tunes selected backbone layers.

## Methodology & Pipeline

- **Dataset/Input Data:** MNIST study uses a balanced 1,000-image train subset (100 per digit) and 200-image test subset (20 per digit), split into 800 train/200 validation. CIFAR-10 study uses 1,000 train images (100 per class) and 200 test images (20 per class), also split 800/200 for train/validation.
- **Preprocessing:** MNIST digits are repeated into RGB, resized to 96x96, and use DenseNet ImageNet preprocessing; augmentation is rotation 10 degrees, horizontal/vertical shifts 8%, zoom 10%. CIFAR-10 RGB images resize 32x32 to 96x96 and use each backbone's own ImageNet preprocessing; augmentation uses rotation 10 degrees, shifts 8%, zoom 10%, horizontal flip. Both use batch 32.
- **Model/Algorithm:** MNIST uses ImageNet DenseNet121 (`include_top=False`), global average pooling, dropout 0.2, 10-way softmax; fine-tune last 20 layers (BatchNorm frozen). CIFAR-10 compares ImageNet VGG16, ResNet50, MobileNetV2, DenseNet121 with global pooling/dropout/10-way heads, then fine-tunes final 4 VGG16 layers or final 20 layers of each other backbone (BatchNorm frozen).
- **Hyperparameters/Key Parameters:** MNIST DenseNet: Adam 1e-3, up to 15 epochs; fine-tuning Adam 1e-5 for up to 8 epochs. CIFAR-10 transfer stage: Adam 1e-3, up to 8 epochs; fine-tuning Adam 1e-5, up to 8 epochs. Checkpoint/early stopping monitor validation loss; ReduceLROnPlateau is used in the fine-tuning loop.

## Key Results & Observations

- **MNIST:** frozen DenseNet test accuracy 91.0%, loss 0.3543; fine-tuned accuracy 91.5%, loss 0.3163. **CIFAR-10 fine-tuned test:** VGG16 63.0% (loss 1.6355), ResNet50 76.0% (0.8009), MobileNetV2 76.5% (0.6737), DenseNet121 75.5% (0.7389). MobileNetV2 leads with weighted precision 76.95%, recall 76.5%, F1 76.3%. Accuracy changes after fine-tuning were +6.0, -0.5, +0.5, and +1.5 points respectively.
- **Limitations / next steps:** Both datasets are sampled to only 1,000 training and 200 test images, so these results do not establish full-dataset performance. Fine-tuning did not improve every CIFAR architecture (ResNet50 fell 0.5 points).

## How to Run

- Open the [notebook](./Transfer_Learning_and_Fine_Tuning_using_Pretrained_Deep_Convolutional_Neural_Networks_%28CNNs%29.ipynb) in Jupyter or [Google Colab](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/03-transfer-learning/Transfer_Learning_and_Fine_Tuning_using_Pretrained_Deep_Convolutional_Neural_Networks_%28CNNs%29.ipynb).
- From this project directory, install the repository dependencies with `pip install -r ../requirements.txt`, then run the notebook cells in order. Several notebooks expect datasets, images, or videos to be downloaded or supplied at the paths documented above.

## References & Credits

- MNIST and CIFAR-10 from `tf.keras.datasets`; ImageNet pretrained Keras VGG16, ResNet50, MobileNetV2, and DenseNet121.
