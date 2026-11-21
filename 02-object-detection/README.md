# Clash of Clans Object Detection with YOLO11s

![Python-3.10%2B](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=flat-square) ![Ultralytics YOLO11](https://img.shields.io/badge/Ultralytics%20YOLO11-blueviolet?style=flat-square) ![PyTorch](https://img.shields.io/badge/PyTorch-blueviolet?style=flat-square) ![OpenCV](https://img.shields.io/badge/OpenCV-blueviolet?style=flat-square) ![NumPy](https://img.shields.io/badge/NumPy-blueviolet?style=flat-square) ![Matplotlib](https://img.shields.io/badge/Matplotlib-blueviolet?style=flat-square) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/02-object-detection/Object_detection_fine_tuning_by_training_a_pretrained_YOLO11s_model_on_Clash_of_Clans_dataset_from_Robloflow_Universe.ipynb)

## Overview

Fine-tunes a pretrained YOLO11 small detector to identify defensive structures and other objects in Clash of Clans base screenshots. The notebook first demonstrates pretrained COCO inference and confidence filtering, then evaluates the custom 16-class model.

## Methodology & Pipeline

- **Dataset/Input Data:** Clash of Clans dataset by Find This Base on Roboflow Universe; 125 original annotated images, version 4 with 301 images at 640 x 640. Notebook reports 13 test images.
- **Preprocessing:** Extract Roboflow dataset archive and load the provided `data.yaml`; Ultralytics handles image resizing/augmentation during training.
- **Model/Algorithm:** Pretrained `yolo11s.pt`, fine-tuned for 16 dataset classes.
- **Hyperparameters/Key Parameters:** Training call uses 10 epochs, image size 640, batch 16; other training values follow Ultralytics defaults. The pretrained demo also compares YOLO11n and YOLO11s and confidence thresholds 0.1, 0.25, 0.5, and 0.8.

## Key Results & Observations

- Validation metrics printed: precision 0.9348, recall 0.9116, mAP50 0.9675, mAP50-95 0.7668. The notebook also runs predictions on three test screenshots.
- **Limitations / next steps:** The dataset is small (301 images; 13 test images), so validation scores may not reflect broad generalization across game layouts or image styles.

## How to Run

- Open the [notebook](./Object_detection_fine_tuning_by_training_a_pretrained_YOLO11s_model_on_Clash_of_Clans_dataset_from_Robloflow_Universe.ipynb) in Jupyter or [Google Colab](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/02-object-detection/Object_detection_fine_tuning_by_training_a_pretrained_YOLO11s_model_on_Clash_of_Clans_dataset_from_Robloflow_Universe.ipynb).
- From this project directory, install the repository dependencies with `pip install -r ../requirements.txt`, then run the notebook cells in order. Several notebooks expect datasets, images, or videos to be downloaded or supplied at the paths documented above.

## References & Credits

- Find This Base, Clash of Clans Object Detection dataset, Roboflow Universe: https://universe.roboflow.com/find-this-base/clash-of-clans-vop4y; Ultralytics `yolo11s.pt` and COCO `yolo11n.pt`.
