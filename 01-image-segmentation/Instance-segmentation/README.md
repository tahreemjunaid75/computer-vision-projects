# Concrete Defect Instance Segmentation with YOLO11

![Python-3.10%2B](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=flat-square) ![Ultralytics YOLO11](https://img.shields.io/badge/Ultralytics%20YOLO11-blueviolet?style=flat-square) ![PyTorch](https://img.shields.io/badge/PyTorch-blueviolet?style=flat-square) ![OpenCV](https://img.shields.io/badge/OpenCV-blueviolet?style=flat-square) ![NumPy](https://img.shields.io/badge/NumPy-blueviolet?style=flat-square) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/01-image-segmentation/Instance-segmentation/Instance_Segmentation_of_Concrete_Defects_using_YOLO11.ipynb)

## Overview

This project converts COCO polygon annotations for concrete surface defects into YOLO segmentation labels, then trains an instance segmentation model. The goal is to localize and outline cracks and other visible defects for automated inspection.

## Methodology & Pipeline

- **Dataset/Input Data:** Roboflow concrete.v8i.coco ZIP downloaded from Google Drive; 2,568 annotated train images found in the COCO train metadata. Converted split totals: 2,054 train, 257 validation, 257 test. Six labels: concrete, crack, hole, honeycombe, pitting, spalling.
- **Preprocessing:** COCO polygon/RLE annotations converted to polygon contours and normalized YOLO segmentation labels; no missing images or skipped annotations in saved output. YAML specifies train/val/test folders.
- **Model/Algorithm:** Ultralytics YOLO11n-seg pretrained instance segmentation weights (`yolo11n-seg.pt`).
- **Hyperparameters/Key Parameters:** 50 epochs; imgsz 640; batch 8; horizontal flip 0.5; seed 42; optimizer auto, initial lr 0.01, patience 10 as logged by Ultralytics. Validation uses imgsz 640 and batch 8; prediction confidence 0.25.

## Key Results & Observations

- On 257 test images / 492 instances: box precision 0.732, recall 0.757, mAP50 0.803, mAP50-95 0.586; mask precision 0.680, recall 0.721, mAP50 0.753, mAP50-95 0.403. Aggregate mask AP is notably lower than box AP; rare classes also have few examples (e.g. spalling: 7 instances).
- **Limitations / next steps:** Class support is uneven and the recorded test contains only 257 images. Mask AP, especially at stricter IoU thresholds, leaves room for more data and annotation/model tuning.

## How to Run

- Open the [notebook](./Instance_Segmentation_of_Concrete_Defects_using_YOLO11.ipynb) in Jupyter or [Google Colab](https://colab.research.google.com/github/tahreemjunaid75/computer-vision-projects/blob/main/01-image-segmentation/Instance-segmentation/Instance_Segmentation_of_Concrete_Defects_using_YOLO11.ipynb).
- From this project directory, install the repository dependencies with `pip install -r ../../requirements.txt`, then run the notebook cells in order. Several notebooks expect datasets, images, or videos to be downloaded or supplied at the paths documented above.

## References & Credits

- Concrete Defects dataset archive from Google Drive; Ultralytics pretrained `yolo11n-seg.pt`; COCO annotations and pycocotools.
